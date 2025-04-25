# Financial Data Validator

A Python-based validation tool for financial Excel files that ensures data integrity and consistency according to specified configuration parameters.

## Overview

This tool validates Excel spreadsheets containing financial data against a set of predefined rules. It checks for proper formatting, required data presence, and consistency in financial reports.

## Features

- Validates Excel files (.xls, .xlsx) against customizable configuration rules
- Verifies company names match expected values
- Ensures financial data contains audited values
- Validates year sequences and data continuity
- Checks for required row names and non-empty values
- Comprehensive error reporting and logging
- Command-line interface for easy integration into workflows

## Requirements

- Python 3.6+
- Dependencies:
  - pandas
  - pyyaml
  - argparse
  - openpyxl (for .xlsx files)
  - xlrd (for .xls files)

## Installation

```bash
# Clone the repository or download the script
git clone https://github.com/AnsarMahir/Excelvalidation.git

# Install dependencies
pip install pandas pyyaml openpyxl xlrd
```

## Usage

Run the validator from the command line:

```bash
python validation_script.py --excel [PATH_TO_EXCEL_FILE] --config [PATH_TO_CONFIG_YAML] --output [OPTIONAL_OUTPUT_JSON_PATH]
```

### Arguments

- `--excel`: Path to the Excel file to validate (required)
- `--config`: Path to the YAML configuration file (required)
- `--output`: Path to save the validation results in JSON format (optional)

## Configuration

Configure validation rules using a YAML file. Example configuration:

```yaml
sheet_name: "Compute"
expected_company_name: "ACME Corporation"
audit_type_row: 5
year_row: 6
validation_settings:
  min_required_years: 3
row_validations:
  - row: 10
    expected_name: "Revenue"
  - row: 15
    expected_name: "Net Income"
  - row: 20
    expected_name: "Total Assets"
```

### Configuration Options

- `sheet_name`: Name of the Excel sheet to validate
- `expected_company_name`: Expected company name to match in the file
- `audit_type_row`: Row number containing audit type information
- `year_row`: Row number containing financial years
- `validation_settings`: Additional validation parameters
  - `min_required_years`: Minimum number of years required in the report
- `row_validations`: List of specific rows to validate
  - `row`: Row number
  - `expected_name`: Expected name of the row (in first column)

## Output

The validation script produces:

1. Console output with a summary of validation results
2. Detailed log file (`financial_data_validator.log`)
3. Optional JSON output file with validation results

Example console output:

```
=== VALIDATION SUMMARY ===
Valid: ✓ YES

Warnings:
1. Gap in year sequence: 2020 to 2022
```

## Error Codes

The script returns:
- `0`: Validation successful (no errors)
- `1`: Validation failed (errors found)

## Extending the Validator

To add new validation rules, modify the `ExcelValidator` class in the script:

1. Add a new validation method (e.g., `_validate_new_rule`)
2. Call the method from the `validate_file` method
3. Update the configuration schema to include new validation parameters


## Contact
mohamedansak@gmail.com
