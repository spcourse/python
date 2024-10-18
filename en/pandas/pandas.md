# Pandas

## Introduction

When processing data, you will most often work with _structured data_. This is the kind of data where you have a table with some number of named columns, each corresponding to a different feature, and a sequence of rows, each corresponding to a different sample. Examples of structured data can be found everywhere and occur any time you are making a series of observations and write down some properties for each observation you make.

Some examples of structured data are:
- Weather reports, where you have columns such as 'Date', 'Temperature' and 'Humidity', and each row shows the temperature and humidity on some date.
- Companies use structured data everywhere, from user accounts to product information and from purchases to reviews.
- A grocery list is a very simple type of structured data, where you have a 'Product' and 'Amount' column indicating how many of what product you intend to buy.

_Note on notation:_ There are many different ways to refer to the columns and rows in a table. This notebook will refer to the vertically orientated axis as 'columns' (but elsewhere this might be called a 'field', 'feature' or 'property') and the horizontal axis as 'rows' (also called 'entries', 'samples' or 'observations').

`Pandas` (often imported as `pd`) is the most popular library to use when dealing with structured data in Python. In this exercise notebook, we will explore some of the basics of working with Pandas. This notebook will not be able to cover everything you will ever need, but will hopefully give you an idea of what it can do for you. 

Some sections will end with a note on *Further Reading*; this will not be necessary for completing the exercises, but references relevant information that might help you in the future.


```python
import pandas as pd

from tests import *

# This line indicates that any floating point number should only have 2 digits
# past the decimal point. This prevents numbers like 5.00000003 to be printed,
# and instead will just print 5.00.
pd.set_option("display.precision", 2)
```

## DataFrames

Structured data is nothing more than a table consisting of rows and columns. In `Pandas`, such a table is called a `DataFrame`. To create a DataFrame called `df`, you can use `df = pd.DataFrame(data)` where `data` is a `list` of rows, and each row is also a list, containing the values for that row. Below you can see a simple example of creating a table with 2 rows and 3 columns.

You can have any number of rows, but it is important that each row has the same number of elements (i.e. columns), otherwise you will get an error. The example below uses Jupyter's `display` function to get a nice looking output (although `print` also works).


```python
data = [[1, 2, 3], # The first row has values 1, 2, 3
        [4, 5, 6]] # The second row has values 4, 5, 6

df = pd.DataFrame(data)

display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>


Now this is not a very descriptive table, since the columns are just called `0`, `1` and `2`. To change this, you can use the optional `columns` argument when creating the `DataFrame`, where you can specify the names of each of the columns using a `list`. Make sure to provide as many column names as there are columns in your data (the number of values in a single row), otherwise you will get an error.

Let's create another dataframe; the first column has values `'a'` and `'b'` and we call it `'Some letter'`, another column with values `2` and `5` we call `'Int'` and finally a column with `3.5` and `6.5` we call `'A float'`.


```python
data = [['a', 2, 3.5],
        ['b', 5, 6.2]]

df = pd.DataFrame(data, columns=['Some letter', 'Int', 'A float'])

display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Some letter</th>
      <th>Int</th>
      <th>A float</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a</td>
      <td>2</td>
      <td>3.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b</td>
      <td>5</td>
      <td>6.2</td>
    </tr>
  </tbody>
</table>
</div>


You might have already noticed that each of the _rows_ also gets its own index on the left (in this case it is `0` and `1`, which it does by default). This is called the `index` of the dataframe (which you can see by using `df.index`), and can be set using the optional `index` argument to provide a `list` of row names when creating the `DataFrame`.

Again, make sure you provide as many names in the `index` argument as there are rows (in this case 2 rows, and therefore 2 names); otherwise you will get an error.


```python
data = [['a', 2, 3.5],
        ['b', 5, 6.2]]

df = pd.DataFrame(data,
    index=['First Row', 'Row 2'],
    columns=['Some letter', 'Int', 'A float']
)

display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Some letter</th>
      <th>Int</th>
      <th>A float</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>First Row</th>
      <td>a</td>
      <td>2</td>
      <td>3.5</td>
    </tr>
    <tr>
      <th>Row 2</th>
      <td>b</td>
      <td>5</td>
      <td>6.2</td>
    </tr>
  </tbody>
</table>
</div>



```python
print("The index column of the dataframe:")
display(df.index)
```

### Exercise 1
Create a DataFrame called `df` that contains the data in the following table:

|       | **A** | **B** |
|-------|-------|-------|
| **X** | 5.3   | foo   |
| **Y** | 2.0   | bar   |
| **Z** | 0.2   | baz   |


```python
df = None

# YOUR CODE HERE

display(df)
```


```python
test_1(df)
```

*Further Reading:* You can find the full documentation on creating a DataFrame [here](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame) (which lists the technical description of all the options) or use the Pandas User Guide [on DataFrames](https://pandas.pydata.org/pandas-docs/stable/user_guide/dsintro.html#basics-dataframe) (which includes more examples).

Now that we know how to create a DataFrame, let's see what we can do with them!

This notebook will follow a narrative where you are hired as the new head of (and only member of) the Data Processing department of your local grocery store. This grocery store has kept a record of their products, and it is now up to you to process this data. This record consists of products, to what category they belong, their price, the size (i.e. 'unit') of the product and the current stock.

We have provided you with a function `get_df()` which gets you the data as a `DataFrame` for you to use. As you can see, it is _indexed_ on the 'Product' and has the _columns_ 'Category', 'Price', 'Unit' and 'Stock'. The example `DataFrame` is displayed below.


```python
df = get_df()
display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


### Getting data from a DataFrame

A table consists of columns with values for each row; and similarly, a `DataFrame` consists of `Series` with values for each index. Therefore, if you want to look at a single column of your data, you'll need to retrieve that `Series` from your `DataFrame`!

To see what columns are in your DataFrame, you can use the `df.columns` property:


```python
print("The columns of `df`:")
display(df.columns)

# Indexing works the same way as a list:
print("\nThe second column is:", df.columns[1])
```

    The columns of `df`:



    Index(['Category', 'Price', 'Unit', 'Stock'], dtype='object')


    
    The second column is: Price


To get a column from your DataFrame, you can index it in the same way you do with a dictionary: by using `df['ColumnName']`, where `df` is your DataFrame and `ColumnName` is the name of your column. The code below retrieves the 'Price' column from our DataFrame:


```python
# Retrieve the 'Price' column from the DataFrame as a Series
prices = df['Price']

display(prices)
```


    Apple          2.39
    Banana         1.49
    Broccoli       1.29
    Carrot         0.45
    Coffee         7.49
    Eggplant       0.72
    Juice          2.79
    Lettuce        0.82
    Penne          0.99
    Rice           2.59
    Spaghetti      0.99
    Strawberry     3.49
    Tagliatelle    1.89
    Name: Price, dtype: float64



```python
# Here you can see that this is indeed a 'Series' object:
print("The variable 'prices' is of type:", type(prices))

# You can always check the dtype of your Series by using .dtype:
print("This Series has dtype:", prices.dtype)
```

    The variable 'prices' is of type: <class 'pandas.core.series.Series'>
    This Series has dtype: float64


In the example above you can see that this Series doesn't just contain the _values_ of the 'Price' column (displayed on the right), but also the _index_, which lists the product names from the original DataFrame (displayed on the left). This way, it is a lot easier to see which price belongs to what product! Lastly, you can see at the bottom what the `dtype` of this column is (in this case `float64`, since these are floating point numbers).

Accessing the data in that `Series` then also works in the same way as for dictionaries: you can just use the index as the key. For example, the price of Broccoli can be found by first retrieving the 'Price' column from the `DataFrame`, and then indexing the resulting `Series` on 'Broccoli':


```python
# Retrieve the 'Price' column from the DataFrame as a Series
prices = df['Price']

# Get the 'Broccoli' value from that Series
price_broccoli = prices['Broccoli']

print("The price of Broccoli is:", price_broccoli)
```

    The price of Broccoli is: 1.29


### Exercise 2

In the 'Stock' column, how many 'Penne' are left? Use `df` to find the value and save the result in `stock_penne`.


```python
df = get_df()
stock_penne = None

# YOUR CODE HERE

print("There are", stock_penne, "penne in stock.")
```

## Series

A `Series` is data structure specific to *Pandas*, that has aspects of both lists and dictionaries. It is like a `list` in that it is an ordered sequence of data, meaning it just stores different values together in some order. However, the indices used for a `Series` don't need to be the integers $0, 1, \dots$, like with a list, but can be any type, including strings, like the keys of a `dictionary`.

Note that all the values in a `Series`, must be of the same type, like with *Numpy* `ndarrays`. In the example above, the `Series` has a `dtype` of float, meaning it can only contain floating point values. Lastly, a `Series` has an optional name, which is set automatically here to the name of the column from the `DataFrame` where it came from.

If we want to create a `Series`, we can just define it using a list of indices and list of values. Note that order here matters; position 0 in the index list will become the index for position 0 in the value list, and this will become the first element in the `Series`. Below is an example to create a `pd.Series` called `discount` with products as its indices and a discounted price as its values.


```python
discount_products = ['Strawberry', 'Apple', 'Coffee', 'Juice', 'Broccoli']
discount_prices = [2.99, 2.15, 4.99, 1.89, 0.99]

discount = pd.Series(
    data=discount_prices,      # Use discount_prices as the values
    index=discount_products,   # Use discount_products as the index
    dtype=float,               # Set the type for the `data` argument to floating point numbers
    name="Discount",           # Set the name for the Series to Discount
)

display(discount)
```


    Strawberry    2.99
    Apple         2.15
    Coffee        4.99
    Juice         1.89
    Broccoli      0.99
    Name: Discount, dtype: float64


The most basic version of a `Series` is just a sequence of data of the same type, meaning you actually don't _need_ to provide an index for your `Series`. If you do not provide any index, `Pandas` will just use $0, 1, \dots$, like the indices of a `list`.

However, much of the power of Pandas is the use of this index to easily retrieve rows from your DataFrame (more on this in the section on [Indexing, Selection and Masking](#indexing-selection-and-masking)). It is therefore always recommended to use _some_ sort of index for your Series, if you can!

Below is an example of the basic way you can create a Series, by just providing a `list` of values:


```python
basicSeries = pd.Series([6.4, 2.3, 1.0])

display(basicSeries)
```


    0    6.4
    1    2.3
    2    1.0
    dtype: float64


You can create a `Series` with any kind of data. Below are some more examples with different data types: pay attention to the resulting `dtype` for each!

Pandas tries its best to find the right type for your Series, and falls back on an `object` type if it cannot find a type that works. A Series must always be consistent in its type for all values in the Series, and standard types for this are the same as for *Numpy*; integers, floats and booleans. Note that *strings* are not in this list, and so strings also get the generic `object` type.

What you can do with a column largely depends on the `dtype` of that `Series`, so always try to pick the type that works for your data!


```python
print("A Series with strings gets dtype 'object':")
display(pd.Series(['a', 'b', 'c']))

print("\nIf you provide a mix of integers and floats, it will convert all elements to floats:")
display(pd.Series([1, 2, 3.0]))

print("\nBut you can also force it to be a specific type:")
display(pd.Series([1, 2, 3.0], dtype=int))

print("\nIf you provide a mix of strings and other types, then everything becomes 'object's:")
display(pd.Series(['hello', 2, 3.0]))

print("\nAs a very useful extra, Pandas can even convert your date to a consistent type:")
display(pd.Series([ "2023 aug 02", "2021 8 23", "1970/01/01"], dtype="datetime64[ns]"))
```

    A Series with strings gets dtype 'object':



    0    a
    1    b
    2    c
    dtype: object


    
    If you provide a mix of integers and floats, it will convert all elements to floats:



    0    1.0
    1    2.0
    2    3.0
    dtype: float64


    
    But you can also force it to be a specific type:



    0    1
    1    2
    2    3
    dtype: int64


    
    If you provide a mix of strings and other types, then everything becomes 'object's:



    0    hello
    1        2
    2      3.0
    dtype: object


    
    As a very useful extra, Pandas can even convert your date to a consistent type:



    0   2023-08-02
    1   2021-08-23
    2   1970-01-01
    dtype: datetime64[ns]


### Exercise 3

At the end of the day, the following sales come in:

|            |   |
|------------|---|
| Lettuce    | 1 |
| Carrot     | 3 |
| Spaghetti  | 1 | 
| Coffee     | 2 |
| Apple      | 1 |
| Strawberry | 1 |

Create a `Series` called `sales` containing the data in the table above.


```python
sales = None

# YOUR CODE HERE

display(sales)
```

### Adding and modifying data

You can *add* a column to your `DataFrame` in the same way we retrieved a column from the DataFrame before. If you have a Series called `mySeries`, you can add it to your DataFrame `myDataFrame` as a column named `'myColumn'` using `myDataFrame['myColumn'] = mySeries`. Pandas will even match the `index` of your Series and DataFrame, so all values end up in the right place!

Let's use the `discount` Series from before and add it to the Dataframe. This will match all the indices in the Series with the DataFrame indices, and add the values in the right place. When there is no discount for a specific product, the value automatically gets set to `NaN`. We will come back to the different ways you can deal with the `NaN`s later, in the section on [Handling missing values](#Handling-missing-values).


```python
df = get_df()

print("The discount Series")
discount = pd.Series(discount_prices, index=discount_products)
display(discount)

print("Added to the DataFrame:")
df['Discount'] = discount
display(df)
```

    The discount Series



    Strawberry    2.99
    Apple         2.15
    Coffee        4.99
    Juice         1.89
    Broccoli      0.99
    dtype: float64


    Added to the DataFrame:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
      <th>Discount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
      <td>2.15</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
      <td>0.99</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
      <td>4.99</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
      <td>1.89</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
      <td>2.99</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


We can also easily modify values in `Series` using basic arithmetic operations. All arithmetic operations are element-wise by default, and broadcasted when necessary, exactly like in *Numpy*.

Below is a simple example where we get a new inventory shipment with 10 items for each product, and need to update the DataFrame accordingly. Note that this increase is getting broadcasted to every value in the `Series` here.

It is important to remember that any arithmetic operation always creates a **new** `Series`, and so doesn't modify the existing DataFrame! If we want to update the values in the DataFrame, we need to re-assign the new Series to the corresponding collumn.


```python
print("Adding 10 to the stock of every product:")
increased_stock = df['Stock'] + 10
display(increased_stock)

print("\nReplacing the stock column in the DataFrame:")
df['Stock'] = increased_stock
display(df)
```

    Adding 10 to the stock of every product:



    Apple          16
    Banana         12
    Broccoli       13
    Carrot         32
    Coffee         20
    Eggplant       11
    Juice          13
    Lettuce        15
    Penne          13
    Rice           17
    Spaghetti      10
    Strawberry     20
    Tagliatelle    12
    Name: Stock, dtype: int64


    
    Replacing the stock column in the DataFrame:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
      <th>Discount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>16</td>
      <td>2.15</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>12</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>13</td>
      <td>0.99</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>32</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>20</td>
      <td>4.99</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>11</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>13</td>
      <td>1.89</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>15</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>13</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>17</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>20</td>
      <td>2.99</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>12</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


An important difference with *Numpy* is that element-wise operations are always matched by *their index*, so the order of the elements in the Series actually does not matter, only what their index is. We'll come back to this in more detail in the section [Operating on DataFrames](#Operating-on-DataFrames), but for now we'll just give another example, so you have a bit of an idea of the possibilities:

Let say you want to now compute the percentage of discount for each of the discounted prices, so you can use those to advertise your sale. First we'll need to compute ratio of the discounted prices compared to the original price and store the result in a new `Series`. We can just do this by dividing the Discount column by the Price column:


```python
discount_ratio = df['Discount'] / df['Price']

print("The ratio of the discounted price compared to the original price:")
display(discount_ratio)
```

    The ratio of the discounted price compared to the original price:



    Apple          0.90
    Banana          NaN
    Broccoli       0.77
    Carrot          NaN
    Coffee         0.67
    Eggplant        NaN
    Juice          0.68
    Lettuce         NaN
    Penne           NaN
    Rice            NaN
    Spaghetti       NaN
    Strawberry     0.86
    Tagliatelle     NaN
    dtype: float64


Note that this division was indeed performed element by element and matched on the index, so the discounted price of an apple was divided by the original price of an apple, and so on. The products that had a `NaN` value for the discount, then also automatically become `NaN` for the ratio.

Next, we can just multiply this by $100$ to get a percentage, and subtract that value from $100$ to get the percentage that was discounted. Lastly, we can then add this new `Series` back into the `DataFrame` as a new column:


```python
discount_percentage = 100 - discount_ratio * 100
df['Percentage'] = discount_percentage

print('Discount percentage added to the DataFrame:')
display(df)
```

    Discount percentage added to the DataFrame:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
      <th>Discount</th>
      <th>Percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>16</td>
      <td>2.15</td>
      <td>10.04</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>12</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>13</td>
      <td>0.99</td>
      <td>23.26</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>32</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>20</td>
      <td>4.99</td>
      <td>33.38</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>11</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>13</td>
      <td>1.89</td>
      <td>32.26</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>15</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>17</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>20</td>
      <td>2.99</td>
      <td>14.33</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>12</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


In the `DataFrame` we can now see the apples have $10\%$ discount when sold for $2.15$ instead of $2.39$, but we might want to advertise with the $33\%$ discount on coffee instead!

With a couple of discounts this is easy to spot, but for a larger `DataFrame` you would use built-in *aggregate* functions instead. Aggregate functions combine data in a column in some way, so for example using a `.sum()` to compute the total for a column. Here we'll need to use the `.max()` function to find the largest discount percentage and `.idxmax()` to find the product that largest discount belongs to. Note that `NaN` values in the Percentage column will just be ignored here, as this is the default behaviour for all aggregation functions.


```python
largest_discount_percentage = df['Percentage'].max()
largest_discount_product = df['Percentage'].idxmax()

original_price = df['Price'][largest_discount_product]
discount_price = df['Discount'][largest_discount_product]
product_unit =  df['Unit'][largest_discount_product]

print(f'Our best deal is a {int(largest_discount_percentage)}% discount on {largest_discount_product}:')
print(f'Usually {original_price} per {product_unit}, but now on sale for {discount_price}!')
```

    Our best deal is a 33% discount on Coffee:
    Usually 7.49 per 1 kg, but now on sale for 4.99!


### Exercise 4

In exercise 3 we created a `sales` Series with the amount sold, and the prices of each product are listed in the product DataFrame, so we can now see how much revenue we made from these products!

Create a new Series called `revenue`, which combines the number of items sold from `sales` Series with prices from the product DataFrame `df`. The resulting Series should indicate the revenue per product and be added to the DataFrame as a column called Revenue. Finally, compute the total revenue by aggregating all the values in the `revenue` Series and store this as `total_revenue`.


```python
print("As a quick reminder, this is the data in the sales Series:")
display(sales)
```


```python
# Reset the DataFrame
df = get_df()

revenue = None
total_revenue = None

# YOUR CODE HERE

print("Revenue per item, added as new column in the DataFrame:")
display(df)

print(f"\n\nIn total, the market had a revenue of: ${total_revenue:.2f}")
```


```python
test_4(revenue, total_revenue)
```

*Further Reading:* The official documentation has more about [creating a Series](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series). Pandas User Guide also has a [section on Series](https://pandas.pydata.org/pandas-docs/stable/user_guide/dsintro.html#basics-series) and the [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/03.01-introducing-pandas-objects.html) introduces Pandas using Series.

## Indexing, Selection and Masking

In the previous section we covered the most basic ways to retrieve data from a `DataFrame`, but there are many more ways to get data from a `DataFrame` in *Pandas*. As we've already covered how to retrieve columns, next we'll take a look at how to get specific rows from a `DataFrame`.

The first thing we need to answer is: What is a 'row' in *Pandas*? Turns out: it's also a `Series`! That's great, because we just learned how to work with those. Let's start by taking another look at our example `DataFrame`:


```python
df = get_df()

display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


There are several ways to access the rows in a `DataFrame`, but the most common ones are `df.loc[...]` and `df.iloc[...]`. These two methods look and work very similarly, but there are some important differences:

### Using `df.loc[...]`

The `.loc` property retrieves rows by making use of the *index* we defined for our dataframe. This works similarly to a dictionary, where you can use the key (i.e. index) to get the row you want: `df.loc['Banana']` will get you the row where the index is equal to 'Banana'.


```python
df = get_df()
row = df.loc['Banana']

print("The row with index 'Banana' is:")
display(row)
print("\nThis row is of the type:", type(row))
```

    The row with index 'Banana' is:



    Category    Fruits
    Price         1.49
    Unit        500 gr
    Stock            2
    Name: Banana, dtype: object


    
    This row is of the type: <class 'pandas.core.series.Series'>


As you can see, the resulting row `Series` automatically becomes indexed by the *columns* from the original DataFrame. This means that, for example, you could now retrieve the 'Price' for a specific `row` using `row['Price']`. This works the same way for any row, regardless of whether you're using either `.loc` or `.iloc` to retrieve it.

### Using `df.iloc[...]`

The `.iloc` property retrieves rows by the order in which the rows are stored in the `DataFrame`. It stands for "integer location" and works the same way as `list` indices: `df.iloc[0]` is the first row, `df.iloc[1]` is the second, et cetera.

It is important to note that if you re-order your dataframe (such as with sorting), the order of the rows will change and therefore also their "Integer location"! After some operations, using `df.iloc[0]` might give a different result than before. This is different then with `df.loc`, where you just get the row matching the index regardless of the exact position in the `DataFrame`.


```python
df = get_df()
row = df.iloc[0]

print("The first row of the DataFrame is:")
display(row)
print("\nThis row is of the type:", type(row))
```

    The first row of the DataFrame is:



    Category    Fruits
    Price         2.39
    Unit          1 kg
    Stock            6
    Name: Apple, dtype: object


    
    This row is of the type: <class 'pandas.core.series.Series'>


### Rows vs. columns

Retrieving specific rows from a `DataFrame` can obviously be very useful, but there is an important caveat to keep in mind when working with rows:

The problem here stems from the fact that a `Series` can only ever have one type. This works great for columns, as you expect a column of data to all be of the same type (e.g. a price column should always contain floats for each row). This is probably also the best way to look at what a `DataFrame` actually is: A collection of different columns of data, each with their *own data type*, that also each share the *same row index*.

However, a single row of data will contain information from all of the different columns, which might have different types. For mixed types, *Pandas* will again try its best to convert the types to a consistent option, but if you have just one column with strings, then the whole row `Series` will become type 'object'. You can actually already see this happening in both the examples above!

Converting everything to 'object' type means you lose the type information from the columns. In addition, these rows are actually *new* `Series` that have to be built by retrieving the values from each column for an index, and then combining them together into that `Series` (which is when the type conversion happens). This *much* slower than getting a column, where you simply can simply retrieve the stored `Series` from a `DataFrame`.

As a result, the best option is usually to work with columns directly. Looping over the rows in a `DataFrame` might seem like a natural way to process data, as you're going through the data line by line, but this is actually very inefficient. Instead you should try and use element-wise operations to modify a whole column in a `DataFrame`, like the examples you've already seen in the section [Adding and modifying data](#Adding-and-modifying-data).

Note that is still possible to loop through the rows of a `DataFrame` using functions like [`.iterrows()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iterrows.html). This function will create a new `Series` for each row and return them one by one, which can sometimes be very useful. However, if you do find yourself using this, ask yourself first if there isn't a better way to solve your problem, as this type of approach should always be one of the last options you try.

### Exercise 5

Select the fifth row from `df` using the `.iloc[...]` property and store it it in the variable `fifth`.

Next, select the row about Lettuce from `df` and save it in the variable `lettuce` using the `.loc[..]` property.


```python
df = get_df()
fifth = None
lettuce = None

# YOUR CODE HERE

print("Fifth row:")
display(fifth)

print("Lettuce:")
display(lettuce)
```

### Selecting multiple rows or columns

In addition to using `.loc['Banana']` or `.iloc[8]` to obtain a single row, you can also pass a `list` of values to obtain multiple rows from your DataFrame in one go! This actually also works for *columns*, by passing a list of column names when indexing the DataFrame. Note that all these operations will *always* return a `DataFrame`, and not a `Series` like before - even if it is a `DataFrame` with only a single row or column!

Below are some examples using lists to index a DataFrame:


```python
df = get_df()
print("The full dataframe:")
display(df)

rows1 = df.loc[ ['Carrot', 'Juice', 'Rice'] ]
print("\nThe rows with index 'Carrot', 'Juice' and 'Rice':")
display(rows1)

rows2 = df.loc[ ['Carrot'] ]
print("\nThe row with index 'Carrot', as a DataFrame:")
display(rows2)

rows3 = df.iloc[ [0, 2, 4] ]
print("\nFirst, third and fifth row, using a list of indices for iloc:")
display(rows3)

rows4 = df[ ['Category', 'Price'] ]
print("\nSelecting only the Category and Price columns")
display(rows4)
```

    The full dataframe:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    The rows with index 'Carrot', 'Juice' and 'Rice':



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>


    
    The row with index 'Carrot', as a DataFrame:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>


    
    First, third and fifth row, using a list of indices for iloc:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


    
    Selecting only the Category and Price columns



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
    </tr>
  </tbody>
</table>
</div>


The `df.iloc` property works with the position index, and also supports 'slices':
- `df.iloc[a:]` returns everything starting from the `a`-th row.
- `df.iloc[:b]` returns everything up to (but not including) the `b`-th row.
- `df.iloc[::c]` returns every `c`-th row, starting with the first.
    You can also think of this as the 'step size' with which to go through the DataFrame. By default this is 1, which is just every row. A step size of 2 means you skip every second row, et cetera.

And these can also be combined as `df.iloc[a:b:c]` which says: from the `a`th to the `b`th row, give every `c`th row starting with the `a`th.

*Further Reading:* You can find more examples on slices [here](https://www.geeksforgeeks.org/python-list-slicing/).

Below are some examples. Feel free to try out some different values in a new cell, and predict what you'll see before running the code.


```python
df = get_df()
print("Full DataFrame, with a new default range as index:")
# If you reset the index, it will use indices 0,1,... instead
# This will help see what integer indexes are for each row!
display(df.reset_index())

print("\n\nStarting at the tenth row:")
display(df.iloc[10:])

print("\n\nFirst five rows:")
display(df.iloc[:5])

# A negative index means: count backwards from the end
print("\n\nStarting at the second-to-last row:")
display(df.iloc[-2:])

# A bit of an advanced example:
# 1:10 says "Take the second to tenth rows (indices 1,2,3,4,5,6,7,8,9)"
#   :2 says "And then skip every other row (indices 1,3,5,7,9)"
print("\n\nEvery second row up to the tenth row:")
display(df.iloc[1:10:2])
```

    Full DataFrame, with a new default range as index:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Apple</td>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Banana</td>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Broccoli</td>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Carrot</td>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Coffee</td>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Eggplant</td>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Juice</td>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Lettuce</td>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Penne</td>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Rice</td>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Spaghetti</td>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Strawberry</td>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Tagliatelle</td>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    
    Starting at the tenth row:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    
    First five rows:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


    
    
    Starting at the second-to-last row:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    
    Every second row up to the tenth row:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 6
Create a variable `groceries` which contains all the information in `df` for Broccoli, Coffee and Rice using the `.loc` property.

Create a variable `odds` which contains all the odd rows (first, third, fifth, et cetera) using `.iloc` and slices.


```python
df = get_df()
groceries = None
odds = None

# YOUR CODE HERE

print("Groceries:")
display(groceries)

print("\n\nOdd rows:")
display(odds)
```

### Combining row and column selection

If you want to select specific rows *and* columns from a `DataFrame`, there are many ways you can do this in *Pandas*. First off, you can just combine the methods for selecting rows and columns you saw earlier, as these always return a `DataFrame` which you can just index again.

Some examples:


```python
df = get_df()

print("\nSelecting columns first, then indexing the resulting rows using loc:")
cols = df[['Category', 'Price']]
res1 = cols.loc[['Carrot', 'Juice', 'Rice']]
display(res1)


print("\nIndexing the rows using their position with iloc, then selecting the columns:")
rows = df.iloc[[3, 6, 9]]
res2 = rows[['Category', 'Price']]
display(res2)


print("\nSelecting columns first, then slices on iloc, executed on the same line:")
res3 = df[['Category', 'Price']].iloc[3:10:3]
display(res3)
```

    
    Selecting columns first, then indexing the resulting rows using loc:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
    </tr>
  </tbody>
</table>
</div>


    
    Indexing the rows using their position with iloc, then selecting the columns:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
    </tr>
  </tbody>
</table>
</div>


    
    Selecting columns first, then slices on iloc, executed on the same line:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
    </tr>
  </tbody>
</table>
</div>


Note that all these different methods end up with the same DataFrame! Actually any combination of row and column indexing you've seen before would work for this, of course.

In addition, `loc` and `iloc` also support the option to index rows and columns together in the same operation, which is a little more efficient than first creating new Series for the full rows and then selecting from them. With these methods the row indices must always come first (as `loc` and `iloc` are row-based operations), and then optionally you can add a column index too, separated by a comma. This combined indexing also works for single indices, where you only give one index for the rows or columns position, instead of a list. Note in those cases the row or column is reduced, and the result will no longer be a DataFrame. A few examples:


```python
df = get_df()

print("\nSelecting the rows with index Apple and Broccoli, and the columns Category and Stock")
display(df.loc[ ['Apple', 'Broccoli'], ['Category', 'Stock'] ])

print("\nSelecting the first and second row, and the second and fourth column:")
display(df.iloc[ [0, 1], [1, 3] ])

print("\nSelecting the Penne row and the Price column (which is just an element):")
display(df.loc['Penne', 'Price'])

print("\nSelecting only the first row, and the first and fourth column (which is a Series):")
display(df.iloc[0, [0, 3]])

```

    
    Selecting the rows with index Apple and Broccoli, and the columns Category and Stock



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>


    
    Selecting the first and second row, and the second and fourth column:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>2.39</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>1.49</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    Selecting the Penne row and the Price column (which is just an element):



    0.99


    
    Selecting only the first row, and the first and fourth column (which is a Series):



    Category    Fruits
    Stock            6
    Name: Apple, dtype: object


All these different indexing methods can make *Pandas* especially confusing to newcomers, as they are all used interchangeably in explanations and example you might find online. One of the goals of this notebook is to introduce all of these properly, so you can make a bit more sense of the different options you might encounter.

Below are 3 examples all using `loc` that look very similar, but do completely different things. Read the code fo the examples and try to predict what each of these will do, before actually running the cell:


```python
example1 = df.loc['Apple', 'Price']

print("\nExample 1:")
display(example1)

example2 = df.loc[['Apple', 'Broccoli']]

print("\nExample 2:")
display(example2)

example3 = df.loc[['Apple'], ['Price']]

print("\nExample 3:")
display(example3)

```

    
    Example 1:



    2.39


    
    Example 2:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>


    
    Example 3:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>2.39</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 7

Below are 3 exercises to test your understanding with:

a) Select the Broccoli, Coffee and Rice rows from the DataFrame, while also only selecting the Category and Price columns. Save the results in `ex_7a`.

b) Select the last 3 rows from the DataFrame, while also only selecting the Price and Unit columns. Save the results in `ex_7b`.

c) Select the Unit and Stock for Juice. The results should be Series indexed with Unit and Stock. Save the results in `ex_7c`.


```python
df = get_df()
ex_7a = None
ex_7b = None
ex_7c = None

# YOUR CODE HERE

print("\n7a:")
display(ex_7a)

print("\n7b:")
display(ex_7b)

print("\n7c:")
display(ex_7c)
```

### Masking

The last, and very useful, method we'll cover to select data from you DataFrame is masking. Masking is another concept borrowed directly from *Numpy*, as so works almost exactly the same way in *Pandas*.

Masks are used to select parts of a DataFrame where some condition is `True`. You can create a mask by using boolean operators (like  `>`, `<=` or `==`) directly on a DataFrame or Series to define the condition where the mask should be `True`. This will result a broadcasted comparison of elements on the DataFrame/Series, so will create a new DataFrame/Series containing only `True`s and `False`s. Applying a mask just takes the part(s) of your DataFrame where the mask is `True`, and leaves out the parts where it is `False`.

The code below uses the Stock column to create a mask called `mask` where the Stock column is less than four, then uses it to show what items in the DataFrame are low in stock. Note that the `dtype` of the mask becomes `bool`ean and it indeed contains only `True` for the rows that have a Stock less than 4.


```python
df = get_df()

mask = df['Stock'] < 4

print("\nMask where Stock is less than 4:")
display(mask)

print("\nUsing the mask on the DataFrame gives:")
display(df[mask])
```

    
    Mask where Stock is less than 4:



    Apple          False
    Banana          True
    Broccoli        True
    Carrot         False
    Coffee         False
    Eggplant        True
    Juice           True
    Lettuce        False
    Penne           True
    Rice           False
    Spaghetti       True
    Strawberry     False
    Tagliatelle     True
    Name: Stock, dtype: bool


    
    Using the mask on the DataFrame gives:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


Pandas also has built-in functions to create masks. One such example is the `pd.Series.isin(values)` method. This mask is `True` whenever a element in a Series is equal to one of the elements you provided as the *list* of `values`.

As an example, the code below creates a mask where the values in the 'Category' column are either 'Vegetables' or 'Fruits'.


```python
df = get_df()

mask = df['Category'].isin(['Vegetables', 'Fruits'])

print("\nThe mask where the category is either Fruits or Vegetables:")
display(mask)

print("\n\nThe result of applying this mask on the DataFrame:")
display(df[mask])
```

    
    The mask where the category is either Fruits or Vegetables:



    Apple           True
    Banana          True
    Broccoli        True
    Carrot          True
    Coffee         False
    Eggplant        True
    Juice          False
    Lettuce         True
    Penne          False
    Rice           False
    Spaghetti      False
    Strawberry      True
    Tagliatelle    False
    Name: Category, dtype: bool


    
    
    The result of applying this mask on the DataFrame:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


You can also use logical operations, like *logical or* `|` and the *logical and* `&`, to combine two masks element-wise. The first creates a new mask where each element is `True` if one of the masks was `True` for that element, and the second creates a new mask where each element is `True` if both the masks were `True` for that element.


```python
expensive = df['Price'] > 1
low_stock = df['Stock'] < 4

combined_mask = expensive & low_stock

print("\nThe combined mask for items that are both expensive and low in stock:")
display(combined_mask)

print("\nSelecting out the rows where the combined mask is True:")
display(df[combined_mask])
```

    
    The combined mask for items that are both expensive and low in stock:



    Apple          False
    Banana          True
    Broccoli        True
    Carrot         False
    Coffee         False
    Eggplant       False
    Juice           True
    Lettuce        False
    Penne          False
    Rice           False
    Spaghetti      False
    Strawberry     False
    Tagliatelle     True
    dtype: bool


    
    Selecting out the rows where the combined mask is True:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 8

Select the rows from the DataFrame where the Category is either Pastas or Fruits, and the Price is either below 1 or above 3. Store the result as `ex_8`.


```python
df = get_df()
ex_8 = None

# YOUR CODE HERE

display(ex_8)
```

*Further Reading:* The Python Data Science Handbook has a section on [data indexing and selection](https://jakevdp.github.io/PythonDataScienceHandbook/03.02-data-indexing-and-selection.html) and using [masks](https://jakevdp.github.io/PythonDataScienceHandbook/02.06-boolean-arrays-and-masks.html). The documentation on [`.iloc`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.iloc.html) and [`.loc`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.loc.html) also contains more examples.

## Operating on DataFrames

In the section on [`Adding and modifying data`](#Adding-and-modifying-data) you already saw that basic arithmetic operations are actually done *element-wise* by default, which is extremely useful. The general term for operations that are applied element-wise are "Universal Functions" (or Ufuncs) and make libraries such as NumPy and Pandas incredibly powerful, convenient and computationally efficient. These Ufuncs do not only work with basic arithmetics (`+`, `-`, `*`, `/`, etc) but also more sophisticated operations (exponential, trigonometric, logarithmic functions and many more).

With all of these operations, it is important to keep track of the `index` of the Series you are using. For example, if you have a Series `a` with index `0,1,2` and a Series `b` with index `1,2,3`, the operation `c = a + b` will have index `0,1,2,3` (the union of the index of `a` and `b`). Only on indices `1` and `2` will it be able to compute a result, and on indices `0` and `3` it will automatically fill in `NaN` ("Not a Number").


```python
a = pd.Series(
    data=[5, 2, 3],
    index=[0, 1, 2]
)
b = pd.Series(
    data=[7, 3, 1],
    index=[1, 2, 3]
)

print("Series a:")
display(a)

print("\n\nSeries b:")
display(b)

print("\n\na+b gives:")
display(a + b)
```

    Series a:



    0    5
    1    2
    2    3
    dtype: int64


    
    
    Series b:



    1    7
    2    3
    3    1
    dtype: int64


    
    
    a+b gives:



    0    NaN
    1    9.0
    2    6.0
    3    NaN
    dtype: float64


As you can see, the indices `1` and `2` have been added element-wise, as they occur in *both* Series, while for indices `0` and `3` no valid result could be computed, so they become `NaN`. If you want a different result for the indices that only occur once, you'll need to specify how to handle those cases with the `pd.Series.add(...)` method. Using `a.add( b )` is completely equivalent to `a + b`, but using `.add` allows you to specify a `fill_value`, which it will use whenever one of the Series is missing a value for some index.

For example, we can set up a Series called `sales` with the daily sales for some products. If you want to subtract these from the 'Stock' Series in `df`, you need to specify what to do with the missing indices. In this case, we can fill these with zeros using the `sub` function and `fill_value=0`.


```python
df = get_df()

# Extract the 'Stock' column
stock = df['Stock']

print("Stock before sales:")
display(stock)

# Set up a 'sales' Series
sales = pd.Series(
    data=[1, 3, 1, 2, 1, 2],
    index=['Lettuce', 'Carrot', 'Tagliatelle', 'Coffee', 'Apple', 'Strawberry'],
    dtype=int,
    name='Sales'
)

print("\n\nSales:")
display(sales)

print("\n\nStock after sales:")
display( stock.sub(sales, fill_value=0) )

# See what happens if you do not specify a `fill_value` by uncommenting the following line:
# display( stock.sub(sales) )
```

    Stock before sales:



    Apple           6
    Banana          2
    Broccoli        3
    Carrot         22
    Coffee         10
    Eggplant        1
    Juice           3
    Lettuce         5
    Penne           3
    Rice            7
    Spaghetti       0
    Strawberry     10
    Tagliatelle     2
    Name: Stock, dtype: int64


    
    
    Sales:



    Lettuce        1
    Carrot         3
    Tagliatelle    1
    Coffee         2
    Apple          1
    Strawberry     2
    Name: Sales, dtype: int64


    
    
    Stock after sales:



    Apple           5.0
    Banana          2.0
    Broccoli        3.0
    Carrot         19.0
    Coffee          8.0
    Eggplant        1.0
    Juice           3.0
    Lettuce         4.0
    Penne           3.0
    Rice            7.0
    Spaghetti       0.0
    Strawberry      8.0
    Tagliatelle     1.0
    dtype: float64


### Exercise 9

The government has decided to stimulate eating health by removing VAT (Value Added Tax) from all fresh fruits and vegetables. As result, you'll need to lower the prices of some of your products according. You already got a list of the VAT charges per product from the owner of the store, and now just need to update the prices in the DataFrame. Make sure the prices of the other products are not affected!



```python
df = get_df()

fruit_veg_tax = pd.Series([0.22, 0.13, 0.12, 0.04, 0.06, 0.07, 0.31],
    index=['Apple', 'Banana', 'Broccoli', 'Carrot', 'Eggplant', 'Lettuce', 'Strawberry']
)

print("\nThe VAT charge added per fruit/vegetable:")
display(fruit_veg_tax)

# YOUR CODE HERE

print("\nThe DataFrame with updated prices")
display(df)
```

*Further Reading:* The python data science handbook on [operations in pandas](https://jakevdp.github.io/PythonDataScienceHandbook/03.03-operations-in-pandas.html).

## Map

Next to these built-in operations, you can also apply your own function to each value in a Series. Below is a very simple example function, that just returns the length of a string. Say you want to apply `myFunc` to each value in `series_in` and save the results in `series_out`, then you might write something like this:


```python

# A very simple example function
def myFunc(value):
    newValue = len(value)
    return newValue


# Get some Series
series_in = pd.Series(["Hello", "world!"])

print("Input series:")
display(series_in)


# Save the new results in a list for now
series_out = []

# Go through each value in the input Series
for value in series_in:
    # Apply your function to the value, save in output list
    series_out.append( myFunc(value) )

# Create a new series with new values
series_out = pd.Series(series_out)


print("\n\nOutput Series:")
display(series_out)
```

    Input series:



    0     Hello
    1    world!
    dtype: object


    
    
    Output Series:



    0    5
    1    6
    dtype: int64


But looping through values, appending them and then creating a new Series is quite inefficient. All of this can be replaced by using the `pd.Series.map` method. You provide the name of your function (`myFunc` in this case), and Pandas will *map* each value in your Series using your function:


```python

# A very simple example function
def myFunc(value):
    # Do some operations here...
    newValue = len(value)
    return newValue


# Get some Series
series_in = pd.Series(["Hello", "world!"])

print("Input series:")
display(series_in)


# Apply myFunc to each value in series_in, save the result in series_out
series_out = series_in.map(myFunc)


print("\n\nOutput Series:")
display(series_out)
```

    Input series:



    0     Hello
    1    world!
    dtype: object


    
    
    Output Series:



    0    5
    1    6
    dtype: int64


### Exercise 10
Your boss wants to create some advertisements, and needs to replace each 'kg', 'pc' and 'gr' in the 'Unit' column with the full name. You have already written a function called `rename_units` - which replaces each occurance of 'kg', 'pc', 'gr' and 'L' with the full name - and now want to apply it efficiently to the 'Unit' column.

Use the `rename_units` function defined below to `map` all the values in the series `units`. Save the results in your `df` as column 'Units - Long'


```python

def rename_units(units_str):
    """
    Rename shorthands for units to their full name
    such as 'gr' to 'Gram', 'pc' to 'Stucks'

    Input: units_str - a string to replace units in
    Output: A string with unit shorthands replaced with full name
    """
    units_str = units_str.replace("gr", "Gram")
    units_str = units_str.replace("kg", "Kilogram")
    units_str = units_str.replace("pc", "Stuks")
    units_str = units_str.replace("L", "Liter")
    return units_str


# YOUR CODE HERE

display(df)
```

### Lambda functions

One thing you'll see very commonly in combination with `map` are `lambda` functions. Lamba functions are built-in to Python (so not a part of *Pandas* specifically), and can be use to quickly define functions you only want to use once, which is exactly what you want to do with a `map` most of the time.

For example, let's say you want convert all the Categories to lowercase. Defining a function for this and using `map` would be a good solution:



```python
def lowercase(x):
    return x.lower()


df = get_df()

df['Category'] = df['Category'].map(lowercase)

print("\nThe Category column replaced by the lowercase version:")
display(df)
```

    
    The Category column replaced by the lowercase version:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>international</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


An even more compact solution would be to use a `lambda` function here. A lambda function starts with the word `lambda`, followed by a space, the argument of your function (the example below uses `x`) and a colon (`:`). After that you can write a single line of code for the function, which will define what the function *returns*.

This is just a shorter way to write a function, where you don't need give it a name, don't need to write `return` and can define it on the same line. The example above can be replaced by the following using a `lamdba` function:


```python
df = get_df()

df['Category'] = df['Category'].map(lambda x: x.lower())

print("\nThe Category column replaced by the lowercase version:")
display(df)
```

    
    The Category column replaced by the lowercase version:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>international</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


*Further Reading:* More about [lambda statements](https://www.dataquest.io/blog/tutorial-lambda-functions-in-python/), including examples with and without the use of Pandas. 

## Sorting values

Sorting your DataFrame or Series is also a useful and common operation. This is as easy as providing a column to sort on, and *Pandas* will do the rest. By default this will sort the rows of the DataFrame in ascending order (lowest to highest), but you can change this by setting the optional `ascending` parameter to `False`. Note that strings are automatically sorted in alphabetical order too.

The code below will sort the DataFrame by the 'Category' column in ascending order:


```python
df = get_df()

sorted_categories = df.sort_values(by='Category')

display(sorted_categories)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 11

Sort the `df` by 'Price' in descending order and store the result in `df_sorted`


```python
df = get_df()
df_sorted = None

# YOUR CODE HERE

display(df_sorted)
```


```python
test_11(df_sorted)
```

Another useful method is sorting by multiple columns: simply replace the `by=...` argument with a list of column names (`by=['col1', 'col2', ...]`). Similarly, you can replace the `ascending=...` argument with a list with `True` or `False` values (`ascending=[True, False, ...]`) of the same length, which indictates for each of the corresponding columns whether they should be sorted in ascending order or not.

Note that order of the columns in the `by` list matter, as the DataFrame will be sorted by the first column first, and so on. The code below first sorts by the 'Category' column (in ascending order). If multiple rows have the same category, it will then sort these by the 'Stock' column (in descending order):


```python
df = get_df()

display(df.sort_values(by=['Category', 'Stock'], ascending=[True, False]))
```

### Exercise 12

Sort the `df` by category, then price, both in descending order, store the result in `df_sorted2`


```python
df = get_df()
df_sorted2 = None

# YOUR CODE HERE

display(df_sorted2)
```

## Handling missing values

In the section on [operations](#operating-on-dataframes) we already encountered some `NaN` values. Knowing how to deal with missing values is a great skill when working messy datasets (which most datasets are, in practice).

For this exercise we will use a different dataset: For the most popular products in the store (Carrots, Apples, Coffee and Lettuce), your boss has kept a registry of the stock over time. In this case, the products are the columns, and each row is indexed by a date. The values you see is the stock at the start of each week (the market gets restocked on the first of each month).

Unfortunately, some values were illegible and are replaced with `NaN` values. In this section you will see some tools that can help you deal with this.


```python
stock_df = get_stocks()

display(stock_df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Product</th>
      <th>Carrot</th>
      <th>Apple</th>
      <th>Coffee</th>
      <th>Lettuce</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-08-07</th>
      <td>7.0</td>
      <td>17.0</td>
      <td>13.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-08-14</th>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>2023-08-21</th>
      <td>NaN</td>
      <td>9.0</td>
      <td>7.0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>2023-08-28</th>
      <td>NaN</td>
      <td>5.0</td>
      <td>3.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>2023-09-04</th>
      <td>38.0</td>
      <td>20.0</td>
      <td>17.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-09-11</th>
      <td>22.0</td>
      <td>12.0</td>
      <td>14.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>2023-09-18</th>
      <td>11.0</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2023-09-25</th>
      <td>3.0</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2023-10-02</th>
      <td>44.0</td>
      <td>23.0</td>
      <td>15.0</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>2023-10-09</th>
      <td>28.0</td>
      <td>10.0</td>
      <td>11.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>


The most simple method of dealing with `NaN` values is by removing them. This can be done using the `pd.DataFrame.dropna(...)` method. By default, it will remove any row that has any `NaN` on it. You can change this to drop any _column_ that has at least one `NaN` value by passing `axis=1`. If you want to drop a row/column if it is _completely_ filled with `NaN` values, you can pass `how='all'`.

Below is a code example that uses `dropna` with `axis=0` and `how=any` (which are also the default options) to remove the rows containing `NaN`. You can make a new cell where you copy this example and can play around with different combinations of argument. With each combination of arguments you test, try to predict how many rows and columns you expect to see before running the cell.


```python
stock_df = get_stocks()

# Drop rows/columns that contain NaN values
# axis=0 -> drop rows (default)
#      1 -> drop columns
# how='any' -> if that row/column contains at least one NaN value (default)
#     'all' -> if that row/column contains only NaN values
cleaned_df = stock_df.dropna(axis=0, how='any')

display(cleaned_df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Product</th>
      <th>Carrot</th>
      <th>Apple</th>
      <th>Coffee</th>
      <th>Lettuce</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-08-07</th>
      <td>7.0</td>
      <td>17.0</td>
      <td>13.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-09-04</th>
      <td>38.0</td>
      <td>20.0</td>
      <td>17.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-09-11</th>
      <td>22.0</td>
      <td>12.0</td>
      <td>14.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>2023-10-02</th>
      <td>44.0</td>
      <td>23.0</td>
      <td>15.0</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>2023-10-09</th>
      <td>28.0</td>
      <td>10.0</td>
      <td>11.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>


The above example shows that, no matter how you deal with discarding `NaN` values, you throw away some valuable data in the process.

Instead, you can try to replace these missing values with some _approximation_ or guess of what these values could have been. Doing this in a sophisticated way is its own field of research (called Regression, which is part of Machine Learning), but for now we will just replace each `NaN` with a constant value (i.e. the same value everywhere).

Filling values can be done using the `pd.DataFrame.fillna(...)` method. For example, you can specify some `value` you want to fill with:


```python
stock_df = get_stocks()

display(stock_df.fillna(value=0))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Product</th>
      <th>Carrot</th>
      <th>Apple</th>
      <th>Coffee</th>
      <th>Lettuce</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-08-07</th>
      <td>7.0</td>
      <td>17.0</td>
      <td>13.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-08-14</th>
      <td>0.0</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>2023-08-21</th>
      <td>0.0</td>
      <td>9.0</td>
      <td>7.0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>2023-08-28</th>
      <td>0.0</td>
      <td>5.0</td>
      <td>3.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>2023-09-04</th>
      <td>38.0</td>
      <td>20.0</td>
      <td>17.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-09-11</th>
      <td>22.0</td>
      <td>12.0</td>
      <td>14.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>2023-09-18</th>
      <td>11.0</td>
      <td>0.0</td>
      <td>12.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2023-09-25</th>
      <td>3.0</td>
      <td>0.0</td>
      <td>9.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2023-10-02</th>
      <td>44.0</td>
      <td>23.0</td>
      <td>15.0</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>2023-10-09</th>
      <td>28.0</td>
      <td>10.0</td>
      <td>11.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>


Using the same constant value for each column might not be the best approach: there seem to be many more Carrots in stock than Coffee. It would be better if you use some constant value for one column, and another value for another column.

You can do this by passing a 'mapping' in the `value` argument, which gives a value to use for each column in the dataframe. A `dict`ionary is a type of mapping, which maps the keys of that dictionary to the corresponding values. The example below uses Carrot, Apple and Coffee as a key, each with their own value.


```python
stock_df = get_stocks()

# Create a dictionary (a type of mapping)
mapping = {
    'Carrot': 15,
    'Apple': 10,
    'Coffee': 2
}

display(stock_df.fillna(value=mapping))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Product</th>
      <th>Carrot</th>
      <th>Apple</th>
      <th>Coffee</th>
      <th>Lettuce</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-08-07</th>
      <td>7.0</td>
      <td>17.0</td>
      <td>13.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-08-14</th>
      <td>15.0</td>
      <td>12.0</td>
      <td>2.0</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>2023-08-21</th>
      <td>15.0</td>
      <td>9.0</td>
      <td>7.0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>2023-08-28</th>
      <td>15.0</td>
      <td>5.0</td>
      <td>3.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>2023-09-04</th>
      <td>38.0</td>
      <td>20.0</td>
      <td>17.0</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>2023-09-11</th>
      <td>22.0</td>
      <td>12.0</td>
      <td>14.0</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>2023-09-18</th>
      <td>11.0</td>
      <td>10.0</td>
      <td>12.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2023-09-25</th>
      <td>3.0</td>
      <td>10.0</td>
      <td>9.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2023-10-02</th>
      <td>44.0</td>
      <td>23.0</td>
      <td>15.0</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>2023-10-09</th>
      <td>28.0</td>
      <td>10.0</td>
      <td>11.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 13

A Series is another example of a mapping, where the indices are mapped to the values of the Series. Use the [pd.DataFrame.mean()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.mean.html) function to compute the average stock for every product. The result should be a Series and stored in `product_means`.

Next, use this mapping to replace the missing values in `stock_df` for each column with the mean of that column. Store the result in `cleaned_stocks`.


```python
stock_df = get_stocks()

product_means = None
cleaned_stocks = None

# YOUR CODE HERE

print("The average stock of per product:")
display(product_means)

print("\n\nUsing this as constant fill for each column gives:")
display(cleaned_stocks)
```

*Further Reading:* in the python data science handbook on [handling missing data](https://jakevdp.github.io/PythonDataScienceHandbook/03.04-missing-values.html).

## Grouping

Categorical variables (such as the 'Category' column in our example dataset) can also be used to group data together. In doing this, you combine one or more rows from your original DataFrame into a row in the grouped DataFrame. You will then need to specify how these rows get combined (also called 'aggregating'), as multiple rows will need to be reduced to one row per Category.

First, you can group a DataFrame using the `pd.DataFrame.groupby` method and specifying what column you want to group on. This gives something called a `DataFrameGroupBy`, which is special intermediate `groupby` object. The groupby can then be completed by using an aggregate function on the `DataFrameGroupBy`. This will return a regular `DataFrame` again, with its rows reduced as specified by the aggregate function.

You've already seen some of the possible aggregate functions for numerical values throughout this notebook. These are functions like `.sum()`, `.max()`, `.min()`, `.mean()` and `.median()`, which combine values by computing, for example, the maximum value in each column. With a `groupby`, these functions are applied to *all the remaining columns*, so the columns that were not selected as the column to group on. Applying an aggregate function to a `DataFrameGroupBy` results in a new DataFrame with just one row for each separate group, containing all the combined values of that group. Note that is not possible to apply these functions on *nonnumerical* columns (like the Units column), so trying this will result in an error. You can pass the optional `numeric_only=True` argument to the aggregate functions to tell *Pandas* explicitly to just drop those columns.


```python
df = get_df()

grouped_df = df.groupby('Category')

print("\nIntermediate groupby object, which isn't a real DataFrame:")
display(grouped_df)

print("\nHowever, we can access each group separately, which are DataFrames:")
for (group_name, group_df) in grouped_df:
    print('\n'+ group_name +':')
    display(group_df)


category_means = grouped_df.mean(numeric_only=True)

print("\n\n\nComputing the mean per group for each column:")
display(category_means)

# Note this is usually how this is used, with both function calls on the same line
# so without storing the intermediate groupby object seperately
category_max = df.groupby('Category').max(numeric_only=True)

print("\nComputing the maximum per group for each column:")
display(category_max)
```

    
    Intermediate groupby object, which isn't a real DataFrame:



    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x15a4bf350>


    
    However, we can access each group separately, which are DataFrames:
    
    Breakfast:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>


    
    Fruits:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Strawberry</th>
      <td>Fruits</td>
      <td>3.49</td>
      <td>400 gr</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


    
    International:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>


    
    Pastas:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Tagliatelle</th>
      <td>Pastas</td>
      <td>1.89</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


    
    Vegetables:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Eggplant</th>
      <td>Vegetables</td>
      <td>0.72</td>
      <td>1 pc</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Lettuce</th>
      <td>Vegetables</td>
      <td>0.82</td>
      <td>1 pc</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>


    
    
    
    Computing the mean per group for each column:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Stock</th>
    </tr>
    <tr>
      <th>Category</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Breakfast</th>
      <td>5.14</td>
      <td>6.50</td>
    </tr>
    <tr>
      <th>Fruits</th>
      <td>2.46</td>
      <td>6.00</td>
    </tr>
    <tr>
      <th>International</th>
      <td>2.59</td>
      <td>7.00</td>
    </tr>
    <tr>
      <th>Pastas</th>
      <td>1.29</td>
      <td>1.67</td>
    </tr>
    <tr>
      <th>Vegetables</th>
      <td>0.82</td>
      <td>7.75</td>
    </tr>
  </tbody>
</table>
</div>


    
    Computing the maximum per group for each column:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Stock</th>
    </tr>
    <tr>
      <th>Category</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Breakfast</th>
      <td>7.49</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Fruits</th>
      <td>3.49</td>
      <td>10</td>
    </tr>
    <tr>
      <th>International</th>
      <td>2.59</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Pastas</th>
      <td>1.89</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Vegetables</th>
      <td>1.29</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>


As you can see, the result of these groupby and aggregates is a new DataFrame containing the combined data. In the mean DataFrame you can, for example, see that average Stock of all the Breakfast items is $6.5$. And, in the max DataFrame you can see that the Fruit with the highest Price costs $3.49$.

There are also some aggregate functions that work on both numerical and categorical columns:

- `grouped_df.count()` will count the number of rows in that group, excluding `NaN`s.
- `grouped_df.nunique()` counts the number of unique values in each group for each column.
- `grouped_df.first()` gives the elements of the first of the grouped rows. Similarly, `.last()` gives the last.
- `grouped_df.head(n)` will include (up to) the first `n` rows in that group. Similarly, `.tail(n)` gives the last `n` rows.



```python
df = get_df()

print("\nThe number of unique values in each group:")
display(df.groupby('Category').nunique())

print("\nThe first value in each group:")
display(df.groupby('Category').first())

print("\nKeeping (up to) the first 2 rows per group:")
display(df.groupby('Category').head(2))

```

    
    The number of unique values in each group:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
    <tr>
      <th>Category</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Breakfast</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Fruits</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>International</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Pastas</th>
      <td>2</td>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Vegetables</th>
      <td>4</td>
      <td>2</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>


    
    The first value in each group:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
    <tr>
      <th>Category</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Breakfast</th>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Fruits</th>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>International</th>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Pastas</th>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Vegetables</th>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>


    
    Keeping (up to) the first 2 rows per group:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Price</th>
      <th>Unit</th>
      <th>Stock</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Apple</th>
      <td>Fruits</td>
      <td>2.39</td>
      <td>1 kg</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Banana</th>
      <td>Fruits</td>
      <td>1.49</td>
      <td>500 gr</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Broccoli</th>
      <td>Vegetables</td>
      <td>1.29</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Carrot</th>
      <td>Vegetables</td>
      <td>0.45</td>
      <td>1 pc</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Coffee</th>
      <td>Breakfast</td>
      <td>7.49</td>
      <td>1 kg</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Juice</th>
      <td>Breakfast</td>
      <td>2.79</td>
      <td>2 L</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Penne</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Rice</th>
      <td>International</td>
      <td>2.59</td>
      <td>1 kg</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Spaghetti</th>
      <td>Pastas</td>
      <td>0.99</td>
      <td>500 gr</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>


Like regular `DataFrames`, you can select one or more columns from a `DataFrameGroupBy` using the column names. Remember that, as when indexing columns, a single column will always return a Series, and a list of columns (even a list of 1 column) returns a DataFrame!

The examples below compute the minimum Stock per Category, and number of unique values in Price and Unit per Category.


```python
df = get_df()

grouped_df = df.groupby('Category')

minimum_stock = grouped_df['Stock'].min()

print("\nThe minimum values in the Stock column, per Category:")
# Passing just 'Stock' gives a Series, from which we compute the min
display(minimum_stock)

unique_price_unit = grouped_df[['Price', 'Unit']].nunique()

print("\nThe number of unique values in the 'Price' and 'Unit' column, per category:")
# Passing multiple columns gives a DataFrame; from which we compute the n-unique
display(unique_price_unit)

```

    
    The minimum values in the Stock column, per Category:



    Category
    Breakfast        3
    Fruits           2
    International    7
    Pastas           0
    Vegetables       1
    Name: Stock, dtype: int64


    
    The number of unique values in the 'Price' and 'Unit' column, per category:



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Unit</th>
    </tr>
    <tr>
      <th>Category</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Breakfast</th>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Fruits</th>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>International</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Pastas</th>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Vegetables</th>
      <td>4</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>


### Exercise 14

Use the groupby indexing to compute the mean for the Price and Stock columns per Category. Your result should be the same as the earlier mean example, but you cannot use `numeric_only=True` here.



```python
df = get_df()
mean_per_cat = None

# YOUR CODE HERE

display(mean_per_cat)
```


```python
test_14(mean_per_cat)
```

Pandas supports many more methods of aggregating data, which you can use through the `grouped_df.agg()` method. Rather than 'just' computing the mean, you can give a list of methods to aggregate the groups in your DataFrame:


```python
df = get_df()
grouped_df = df.groupby('Category')

# For each column, compute the number of unique values and the number of rows per category
display(
    grouped_df.agg(['nunique', 'count'])
)
```

### Exercise 15

For this last assignment you will need to compute some statistics on the Prices for each Category.

Create a new DataFrame called `price_stats` that contains the number of items in each category, together with the maximum, minimum and mean Price in each category.


```python
df = get_df()
price_stats = None

# YOUR CODE HERE

display(price_stats)
```


```python
test_15(price_stats)
```

*Further Reading:* On [grouping data](https://jakevdp.github.io/PythonDataScienceHandbook/03.08-aggregation-and-grouping.html).
