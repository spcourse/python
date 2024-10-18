# Pandas cheatsheet

### 1. Creating a Pandas Series

    import pandas as pd

    s = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
    print(s)

### 2. Creating a Pandas DataFrame

    data = {'Name': ['John', 'Anna', 'Peter', 'Linda', 'Tom'],
            'Age': [28, 24, 35, 32, 28],
            'City': ['New York', 'Paris', 'Berlin', 'London', 'New York']}

    df = pd.DataFrame(data)
    print(df)

### 3. Accessing Rows and Columns (Indexing and Slicing)

- **Accessing rows**:

      df.iloc[0]  # Access by position
      df.loc[0]   # Access by index label

- **Slicing rows**:

      df.iloc[1:4:2]  # Slicing from row 1 to 4, with steps of 2

- **Accessing columns**:

      df['Name']           # Single column -> Series
      df[['Name', 'Age']]  # Multiple columns -> DF

### 4. statistics

- **Statistical info of columns**:

      df['Age'].mean()
      df['Age'].median()
      df['Age'].sum()  
      df['Age'].min()  
      df['Age'].max()  
      df['Age'].var()  
      df['Age'].std()
      df['Age'].count()  # Count non-null values

### 5. Filtering Data

- **Single condition**: Filter rows based on a single condition.

      df[df['Age'] > 30]

- **Filter with multiple conditions**: You can combine multiple conditions using `&` (and) or `|` (or), and parentheses `()`.

      # Example: Filter rows where Age > 30 and City is 'New York'
      filtered_df = df[(df['Age'] > 30) & (df['City'] == 'New York')]

      # Example: Filter rows where Age < 30 or City is 'Paris'
      filtered_df = df[(df['Age'] < 30) | (df['City'] == 'Paris')]


### 6. Grouping and Looping Over Groups

- **Grouping by 'City' and Looping Over Groups**:

      grouped = df.groupby('City')

      for city, group in grouped:
          print(f"\nCity: {city}")
          print(group)

### 7. Common Aggregation Functions

- **Aggregation after `groupby`**:

      grouped['Age'].mean()      
      grouped['Age'].sum()       
      grouped['Age'].count()    
      grouped['Age'].max()      
      grouped['Age'].min()       
      grouped['Age'].median()    
      grouped['Age'].std()       
      grouped['Age'].var()       

### 8. Reading and Writing to CSV

- **Reading/writing CSV**:

      df = pd.read_csv('data.csv')

      df.to_csv('output.csv', index=False)


### 9. Column Operations: Adding, Multiplying, etc.

- **Arithmetic operations on columns**:

      # Adding a new column by combining other columns
      df['Salary'] = [50000, 60000, 75000, 65000, 55000]
      df['Bonus'] = df['Salary'] * 0.10  

      # Adding, subtracting, multiplying columns
      df['Total Compensation'] = df['Salary'] + df['Bonus']
      df['Years Until Retirement'] = 65 - df['Age']  
      

### 10. Sorting Data

- **Sort by a single column**:

      df.sort_values(by='Age')  

- **Sort by multiple columns**:

      df.sort_values(by=['Age', 'Salary'], ascending=[True, False])
