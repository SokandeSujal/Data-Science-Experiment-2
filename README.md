# Data Science Experiment 2 - Data Preprocessing and Cleaning

This repository contains the code and results for the second experiment in the Data Science Fundamentals with Python course. The objective of this experiment is to preprocess and clean a dataset obtained from the UCI Machine Learning Repository.

## Experiment Overview

### Steps:
1. **Loading the Dataset**: The dataset is loaded using the Pandas library.
2. **Inspecting the Dataset**: Key statistical measures, such as the mean of 'age' and 'marks', are calculated.
3. **Cleaning Column Names**: Leading or trailing spaces in column names are removed.
4. **Standardizing Column Data**: The 'name' column is standardized by capitalizing the first letter of each name.
5. **Handling Duplicate Rows**: Duplicate rows are identified and removed.
6. **Handling Missing Values**: Missing values are handled through imputation using the mean, median, or mode, as appropriate.
7. **Forward and Backward Fill**: Missing values are also handled using forward fill and backward fill techniques.
8. **Saving the Cleaned Dataset**: The cleaned dataset is saved to a CSV file.

## Concepts Used
- **Pandas Library**: Used for data manipulation and analysis.
- **Data Cleaning**: Techniques such as removing duplicates, handling missing values, and standardizing data.
- **Imputation**: Filling missing data using statistical measures like mean, median, or mode.
- **Forward Fill and Backward Fill**: Techniques to fill missing values by propagating previous or subsequent values.
- **DataFrame Operations**: Methods to inspect and clean the dataset.

## Steps to Reproduce

1. **Set up Google Colab**:
   - Open [Google Colab](https://colab.research.google.com/).
   - Create a new notebook.

2. **Import Necessary Libraries**:
   - Start by importing the required libraries.

    ```python
    import pandas as pd
    import matplotlib.pyplot as plt
    ```

3. **Load the Dataset**:
   - Use the path of the dataset.

    ```python
    dataset1 = '/content/drive/MyDrive/Ds Data Sets/student3.csv'
    df = pd.read_csv(dataset1)
    ```

4. **Inspect the Dataset**:
   - Display the first few rows of the dataset and calculate key statistics.

    ```python
    df
    display(df['age'].mean())
    display(df['marks '].mean())
    ```

5. **Clean Column Names**:
   - Remove leading or trailing spaces from column names.

    ```python
    df.columns = df.columns.str.strip()
    df.columns
    ```

6. **Standardize Column Data**:
   - Capitalize the first letter of each name in the 'name' column.

    ```python
    df['name'] = df['name'].str.title()
    df['name']
    ```

7. **Handle Duplicate Rows**:
   - Identify and remove duplicate rows.

    ```python
    df.duplicated()
    df.drop_duplicates(inplace=True)
    df.duplicated()
    ```

8. **Check and Impute Missing Values**:
   - Handle missing values by filling them with appropriate statistical measures.

    ```python
    df.count()
    df.isnull().sum()
    df['marks'].fillna(df['marks'].mean(), inplace=True)
    df['age'].fillna(df['age'].median(), inplace=True)
    df['class'].fillna(df['class'].mode()[0], inplace=True)
    ```

9. **Forward Fill and Backward Fill Missing Values**:
   - Apply forward fill and backward fill techniques to handle missing values.

    ```python
    df_ffill = df.ffill()
    df_bfill = df.bfill()
    df_ffill.head()
    df_bfill.head()
    ```

10. **Save the Cleaned Dataset**:
    - Save the cleaned dataset to a CSV file.

    ```python
    cleaned_dataset = df_ffill
    cleaned_dataset.to_csv('cleaned_dataset.csv', index=True)
    print("Cleaned Dataset saved as 'cleaned_dataset.csv'")
    ```

## How to Use
1. Clone this repository.
2. Run the notebook `Experiment_2_AIDS_SUJAL_SOKANDE.ipynb` in Google Colab or locally.

## Dataset
The dataset used in this experiment is sourced from the [UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/index.php).

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
