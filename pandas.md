https://medium.com/@nandeda.narayan/list/master-python-pandas-100-examples-with-code-8de0c6e063c6


### 1. **DataFrame (df)** and **Series**
- **DataFrame**: A 2D labeled data structure with rows and columns (similar to an Excel sheet or SQL table).
  ```python
  import pandas as pd
  data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
  df = pd.DataFrame(data)
  print(df)
  ```
- **Series**: A 1D labeled array (similar to a column in a DataFrame).
  ```python
  series = pd.Series([1, 2, 3], name="Numbers")
  print(series)
  ```

---

### 2. **Indexing and Selection: `.loc` and `.iloc`**
- **`.loc`**: Access rows/columns by labels or boolean masks.
  ```python
  df.loc[0, 'Name']  # Access value in row 0, column 'Name'
  df.loc[df['Age'] > 25]  # Filter rows where Age > 25
  ```
- **`.iloc`**: Access rows/columns by integer position.
  ```python
  df.iloc[0, 1]  # Access value in first row, second column
  ```

---

### 3. **Cumulative Operations**
- **Cumulative sum, product, max, etc.**
  ```python
  df['Cumulative Age'] = df['Age'].cumsum()
  print(df)
  ```

---

### 4. **Aggregation**
- Perform summarization like mean, sum, etc.
  ```python
  df['Age'].agg(['mean', 'sum'])
  ```

---

### 5. **Pivot Tables**
- Rearrange and summarize data.
  ```python
  data = {'Category': ['A', 'A', 'B'], 'Value': [10, 15, 10]}
  df = pd.DataFrame(data)
  pivot = df.pivot_table(values='Value', index='Category', aggfunc='sum')
  print(pivot)
  ```

---

### 6. **Percentages**
- Calculate percentages for columns or rows.
  ```python
  df['Percentage'] = (df['Age'] / df['Age'].sum()) * 100
  ```

---

### 7. **Ranking**
- Rank values in a column.
  ```python
  df['Rank'] = df['Age'].rank(method='dense', ascending=False)
  ```

---

### 8. **Descriptive Statistics**
- Get summary statistics.
  ```python
  print(df.describe())
  ```

---

### 9. **Join**
- Combine DataFrames on their indexes.
  ```python
  df1 = pd.DataFrame({'A': [1, 2]}, index=[1, 2])
  df2 = pd.DataFrame({'B': [3, 4]}, index=[1, 2])
  joined = df1.join(df2)
  ```

---

### 10. **Merge**
- Combine DataFrames based on keys (similar to SQL JOIN).
  ```python
  df1 = pd.DataFrame({'Key': [1, 2], 'A': [3, 4]})
  df2 = pd.DataFrame({'Key': [1, 2], 'B': [5, 6]})
  merged = pd.merge(df1, df2, on='Key')
  ```

---

### 11. **Melt**
- Reshape DataFrames from wide to long format.
  ```python
  melted = pd.melt(df, id_vars=['Name'], value_vars=['Age'])
  ```

---

### 12. **GroupBy**
- Group data and apply operations.
  ```python
  grouped = df.groupby('Category')['Value'].mean()
  ```

---

### 13. **Concatenate**
- Combine DataFrames vertically or horizontally.
  ```python
  df3 = pd.concat([df1, df2], axis=0)  # Vertical
  ```

---

### 14. **Fill NaN Values**
- Fill missing values.
  ```python
  df.fillna(0, inplace=True)
  ```

---

### 15. **Drop**
- Remove rows or columns.
  ```python
  df.drop('Age', axis=1, inplace=True)  # Drop column
  df.drop(0, axis=0, inplace=True)     # Drop row
  ```

---

### 16. **Read/Write**
- Read from or write to external files:
  ```python
  df = pd.read_csv('file.csv')  # Read CSV
  df.to_excel('file.xlsx')      # Write Excel
  ```

---

### 17. **Simple Visualization**
- Create basic plots (requires Matplotlib or Seaborn).
  ```python
  df['Age'].plot(kind='bar')
  ```

---

### 18. **Apply and Applymap**
- **`apply`**: Apply a function to rows/columns.
  ```python
  df['Age Squared'] = df['Age'].apply(lambda x: x**2)
  ```
- **`applymap`**: Apply element-wise transformations to the entire DataFrame.
  ```python
  df.applymap(lambda x: str(x).upper())
  ```

---

### 19. **Filtering Columns by Condition**
- Select columns based on specific conditions.
  ```python
  filtered_cols = df.loc[:, df.dtypes == 'int64']
  ```

---

### 20. **Bitmask**
- Boolean masks for filtering.
  ```python
  mask = df['Age'] > 25
  filtered_df = df[mask]
  ```

---

### 21. **Reindex**
- Change the index of the DataFrame.
  ```python
  df = df.reindex([1, 0])
  ```
