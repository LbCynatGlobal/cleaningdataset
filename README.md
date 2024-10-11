# Data Cleaning Script

## Overview
This script processes and cleans a CSV file by removing invalid email addresses, invalid login IDs, handling missing data, and removing duplicates. It processes the CSV file in chunks to manage memory usage efficiently and outputs cleaned data into separate CSV files. Invalid or erroneous rows are stored in a separate "garbage" CSV file.

## Requirements
- **Python 3.x**
- **pandas**: A Python library for data manipulation.
- **re**: A module for working with regular expressions.

You can install the required packages via `pip`:
```bash
pip install pandas
```

## Input File
The script reads an input CSV file located at `/content/Lifebear.csv`. It processes the CSV file in chunks to handle large datasets without running into memory issues. 

Make sure to modify the `input_file_path` variable if your input file is located elsewhere:
```python
input_file_path = '/path/to/your/Lifebear.csv'
```

## Key Features
1. **Chunk-based Processing**: The script processes the CSV file in chunks, allowing it to handle large files without overwhelming system memory.
2. **Validation and Cleaning**:
   - **Email Validation**: Only rows with valid email addresses (matching a specific regex pattern) are retained.
   - **Login ID Validation**: Only alphanumeric login IDs are allowed (no special characters).
   - **Handling Missing Data**: Rows missing essential fields (`login_id`, `password`) are removed.
   - **Duplicate Removal**: Any duplicate rows are identified and removed.
3. **Garbage Collection**: Rows with invalid data (invalid email addresses, login IDs, or missing essential fields) are saved in a separate "garbage" file.
4. **Multiple CSV Outputs**:
   - Cleaned data is saved into separate CSV files for each chunk.
   - All cleaned data is concatenated and saved into a final CSV file.
   - All garbage data is saved into a single "garbage" CSV file.

## Configuration

- **Chunk Size**: This controls how many rows are processed in each chunk. You can adjust the chunk size based on your system’s memory capacity:
   ```python
   chunk_size = 10000  # Adjust chunk size if needed
   ```
- **Max Chunks**: The script processes up to 4 chunks by default, but you can change this limit:
   ```python
   max_chunks = 4  # Change this to process more or fewer chunks
   ```

## File Output

- **Cleaned Data**: Each cleaned chunk is saved into separate CSV files named as `/content/cleaned_chunk_<chunk_number>.csv`.
- **Final Cleaned Data**: After processing all chunks, the script merges the cleaned chunks into a single file: `/content/final_cleaned_data.csv`.
- **Garbage Data**: Invalid or erroneous rows are saved into a single file: `/content/final_garbage_data.csv`.

## Example Usage

To run the script, simply execute it in a Python environment. It will read the CSV file, clean the data, and save the cleaned and garbage files.

```bash
python clean_csv_script.py
```

## Error Handling
- The script handles errors during `datetime` conversion and email/login ID validation using the `re` module for regex-based pattern matching.
- Invalid rows are not discarded immediately; they are saved into the garbage CSV for further inspection.



## Credits
Lathelia Brathwaite



