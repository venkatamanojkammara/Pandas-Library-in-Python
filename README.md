# Understanding-Pandas-Library
1. **Introduction :**

   Pandas is an open-source data analysis and manipulation library built on top of the Python programming language. It provides data structures and functions needed to work seamlessly with structured data, including advanced indexing, reshaping, and handling of missing data.

2. **Why Use Pandas?**
   •	Data Cleaning: Easily handle missing or corrupt data.
   •	Data Transformation: Efficiently transform and modify data.
   •	Data Analysis: Perform complex data analysis with intuitive syntax.
   •	Integration: Seamlessly integrates with other Python libraries such as NumPy, Matplotlib, and SciPy.

3. **Uses :**
   •	Data Wrangling: Cleaning, transforming, and organizing raw data.
   •	Data Analysis: Statistical analysis, aggregations, and transformations.
   •	Data Visualization: Plotting data with integrated support for Matplotlib.
   •	Data Import/Export: Reading and writing data from/to various formats like CSV, Excel, SQL databases, and more.

4. **Pandas Series with Different Data Types :**

    A Pandas Series is a one-dimensional labeled array capable of holding any data type.

   *Creating a Series*

        import pandas as pd

   *Integer Series*

       int_series = pd.Series([1, 2, 3, 4, 5])

   *Float Series*
   
        float_series = pd.Series([1.1, 2.2, 3.3, 4.4, 5.5])

  *String Series*

      string_series = pd.Series(['a', 'b', 'c', 'd', 'e'])

   *Boolean Series*
   
      bool_series = pd.Series([True, False, True, False, True])

   *Series with Custom Index*
   
      custom_index_series = pd.Series([10, 20, 30], index=['a', 'b', 'c'])

5. **Pandas DataFrames :**

   A DataFrame is a two-dimensional labeled data structure with columns of potentially different types.

   *Creating DataFrames Manually*


   *Creating a DataFrame from a dictionary*

        data = {
            'Name': ['Alice', 'Bob', 'Charlie'],
            'Age': [25, 30, 35],
            'City': ['New York', 'Los Angeles', 'Chicago']
        }
        df = pd.DataFrame(data)

   *Creating a DataFrame from a list of dictionaries*

        data = [
         {'Name': 'Alice', 'Age': 25, 'City': 'New York'},
         {'Name': 'Bob', 'Age': 30, 'City': 'Los Angeles'},
         {'Name': 'Charlie', 'Age': 35, 'City': 'Chicago'}
       ]
        df = pd.DataFrame(data)


   *Reading CSV and Excel Files*


   *Reading a CSV file*

        df_csv = pd.read_csv('data.csv')

   *Reading an Excel file*

        df_excel = pd.read_excel('data.xlsx', sheet_name='Sheet1')

6. **Different Functions Available in Pandas :**
   
   •	Head and Tail: View the first or last few rows.

        df.head()  # First 5 rows
        df.tail()  # Last 5 rows
   
   •	Info and Describe: Get information about DataFrame.

        df.info()      # Summary of the DataFrame
        df.describe()  # Statistical summary

   •	Shape and Columns: Get dimensions and column names.

        df.shape    # (rows, columns)
        df.columns  # Index of column names

    •	Selecting Data: Select specific rows and columns.

        df['Age']         # Select column
        df[['Name', 'City']]  # Select multiple columns
        df.iloc[0]        # Select first row
        df.loc[0, 'Name'] # Select specific element

7. **Handling Null Values :**

   *Detecting Null Values*

        df.isnull()       # Returns a DataFrame of booleans
        df.isnull().sum() # Count of null values in each column

   *Dropping Null Values*

        df.dropna()  # Drop rows with any null values
        df.dropna(axis=1)  # Drop columns with any null values


8. **Filling Null Values :**

   Filling with Specific Values

        df.fillna(0)  # Fill all null values with 0

   Filling with Statistical Methods

       df.fillna(df.mean())   # Fill with mean
       df.fillna(df.median()) # Fill with median
       df.fillna(df.mode().iloc[0]) # Fill with mode

   Forward Fill and Backward Fill

        df.fillna(method='ffill')  # Forward fill
        df.fillna(method='bfill')  # Backward fill

9. **GroupBy, Merge, and Append Functions :**

   *GroupBy*

      Group data by a specific column and perform aggregations.

        grouped = df.groupby('City')
        grouped.mean()  # Mean of each group

   *Merge*

      Combine two DataFrames based on a common column.

        df1 = pd.DataFrame({'key': ['A', 'B', 'C'], 'value': [1, 2, 3]})
        df2 = pd.DataFrame({'key': ['A', 'B', 'D'], 'value': [4, 5, 6]})
        merged_df = pd.merge(df1, df2, on='key')


   *Append*

      Add rows of another DataFrame to the end of the current DataFrame.

        df1 = pd.DataFrame({'A': [1, 2, 3]})
        df2 = pd.DataFrame({'A': [4, 5, 6]})
        appended_df = df1.append(df2, ignore_index=True)

10. **Pivot Table in Pandas :**
   Pivot tables are used to summarize data with multi-dimensional keys.

   *Creating a Pivot Table*

    df = pd.DataFrame({
        'A': ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'],
        'B': ['one', 'one', 'two', 'two', 'one', 'one'],
        'C': ['small', 'large', 'large', 'small', 'small', 'large'],
        'D': [1, 2, 2, 3, 3, 4]
    })
    pivot_table = pd.pivot_table(df, values='D', index=['A', 'B'], columns=['C'], aggfunc=np.sum)

11. **Additional Information :**

   *Sorting Data*
      Sort data by a specific column.

      df.sort_values(by='Age', ascending=False)

   *Renaming Columns*
      Rename columns in a DataFrame.

      df.rename(columns={'Name': 'Full Name'}, inplace=True)


   *Filtering Data*
      Filter data based on a condition.

      df[df['Age'] > 30]


   *Applying Functions*

  Apply a function to each element or row/column.

      df['Age'].apply(lambda x: x + 1)


   *Handling Duplicates*
      Identify and remove duplicate rows.

      df.duplicated()  # Boolean Series of duplicated rows
      df.drop_duplicates()  # Remove duplicate rows








