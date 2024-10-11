# Delta-Data-Cleaning-MI

This README file describes a project that cleans and processes data from a Japan Lifebear Notebook App users database. The project involves loading the data, splitting it into smaller parts, correcting headers, and identifying and removing invalid or duplicate data. The cleaned data and any discarded data are saved to separate files. The process is logged for tracking and debugging purposes. The README also lists the necessary Python libraries and provides instructions on how to use the code.

# Japan Lifebear Notebook App Users Data Cleaning and Processing

This project focuses on cleaning and processing a dataset of Japan Lifebear Notebook App users. 

## Data Source

The dataset used is "3.6M-Japan-lifebear.com-Largest-Notebook-App-UsersDB-csv-2019.csv". It's assumed to be located in the `/content/` directory within a Google Colab environment.

## Process

1. **Data Loading and Initial Exploration:**
    - The dataset is loaded into a pandas DataFrame using `pd.read_csv`.
    - The separator is set to ';' and `low_memory=True` is used for optimized loading.
    - The first few rows of the DataFrame are printed using `df.head()`.

2. **Data Splitting:**
    - A function `split_csv` is defined to split the large CSV file into smaller chunks for easier processing.
    - The function takes the input file path, output directory, and chunk size as arguments.
    - It creates the output directory if it doesn't exist and saves each chunk as a separate CSV file.

3. **Data Cleaning and Header Correction:**
    - A dictionary `header_mapping` maps the correct column names to the existing column names in the DataFrame.
    - A new DataFrame is created with the corrected headers using the mapping.
    - The cleaned DataFrame is saved to a new CSV file named "cleaned_data_0.csv".

4. **Garbage Data Identification and Logging:**
    - Logging is configured to record information about garbage data.
    - An empty DataFrame `garbage_data_csv` is created to store invalid and duplicate data.
    - Checks are performed to identify invalid data, such as rows with missing 'id' or invalid email or birthday formats.
    - Duplicate data is identified based on the 'id' column.
    - Garbage data is added to `garbage_data_csv`, and logging messages are recorded.
    - The garbage data is saved to a CSV file named "garbage_data.csv".
    - A final logging message indicates the total number of rows placed in the garbage data file.

## Dependencies

- pandas
- numpy
- os
- logging
- re

## Usage

1. Place the "3.6M-Japan-lifebear.com-Largest-Notebook-App-UsersDB-csv-2019.csv" file in the `/content/` directory.
2. Run the provided Python code in a Google Colab notebook.
3. The cleaned data will be saved to "cleaned_data_0.csv".
4. Garbage data will be saved to "garbage_data.csv".
5. Logging information will be recorded in "garbage_data_log.txt".
