# pandas-series-Dataframe
# PANDAS SERIES,DATAFRAME
## _Introduction_

### What is a Series?

- A Pandas Series is like a column in a table.
- It is a one-dimensional array holding data of any type.

**Example**
Create a simple Pandas Series from a list:

``` 
import pandas as pd

a = [1, 7, 2]

myvar = pd.Series(a)

print(myvar)
```

**Output**

``` 
0    1
1    7
2    2
dtype: int64
```

## Labels
If nothing else is specified, the values are labeled with their index number. First value has index 0, second value has index 1 etc.

This label can be used to access a specified value.

**Example**
``` 
Return the first value of the Series:

print(myvar[0])
```
**Output**
```
1
```

## Create Labels

With the `index` argument, you can name your own labels.

**Example**
```
Create you own labels:

import pandas as pd

a = [1, 7, 2]

myvar = pd.Series(a, index = ["x", "y", "z"])

print(myvar)
```
**Output**
```
x    1
y    7
z    2
dtype: int64
```
When you have created labels, you can access an item by referring to the label.

**Example**

```
Return the value of "y":

print(myvar["y"])
```
**Output**

```
7
```

## Key/Value Objects as Series

You can also use a key/value object, like a dictionary, when creating a Series

**Example**

```
import pandas as pd

calories = {"day1": 420, "day2": 380, "day3": 390}

myvar = pd.Series(calories)

print(myvar)
```
**Output**
```
day1    420
day2    380
day3    390
dtype: int64
```


```Note: The keys of the dictionary become the labels.```

To select only some of the items in the dictionary, use the `index` argument and specify only the items you want to include in the Series.

**Example**
```
Create a Series using only data from "day1" and "day2":

import pandas as pd

calories = {"day1": 420, "day2": 380, "day3": 390}

myvar = pd.Series(calories, index = ["day1", "day2"])

print(myvar)
```
**Output**
```
day1    420
day2    380
dtype: int64
```

# DataFrames
Data sets in Pandas are usually multi-dimensional tables, called DataFrames.

Series is like a column, a DataFrame is the whole table.
```
Create a DataFrame from two Series:

import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

myvar = pd.DataFrame(data)

print(myvar)
```
**Output**

```
      calories   duration
0       420        50
1       380        40
2       390        45
```
## Locate Row
As you can see from the result above, the DataFrame is like a table with rows and columns.

Pandas use the `loc` attribute to return one or more specified row(s)

**Example**

```
Return row 0:

#refer to the row index:
print(df.loc[0])
```

**Output**

```
calories    420
duration     50
Name:    0, dtype: int64
```
```Note: This example returns a Pandas Series.```

**Example**

```
Return row 0 and 1:

#use a list of indexes:
print(df.loc[[0, 1]])
```
**Output**

```
       calories  duration
  0       420        50
  1       380        40
```
`Note: When using [], the result is a Pandas DataFrame.`

## Named Indexes
With the index argument, you can name your own indexes.

**Example**
```
Add a list of names to give each row a name:

import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

print(df) 
```
**Output**

```
           calories   duration
  day1       420        50
  day2       380        40
  day3       390        45
```

## Locate Named Indexes
Use the named index in the loc attribute to return the specified row(s).

**Example**

```
Return "day2":

#refer to the named index:
print(df.loc["day2"])
```
**Output**
```
calories    380
duration     40
Name: 0, dtype: int64
```

## Load Files Into a DataFrame
If your data sets are stored in a file, Pandas can load them into a DataFrame.

**Example**
```
Load a comma separated file (CSV file) into a DataFrame:

import pandas as pd

df = pd.read_csv('data.csv')

print(df) 
```
**Output**
```
          Duration  Pulse  Maxpulse  Calories
  0          60    110       130     409.1
  1          60    117       145     479.0
  2          60    103       135     340.0
  3          45    109       175     282.4
  4          45    117       148     406.0
  ..        ...    ...       ...       ...
  164        60    105       140     290.8
  165        60    110       145     300.4
  166        60    115       145     310.2
  167        75    120       150     320.4
  168        75    125       150     330.4
  
  [169 rows x 4 columns]
  ```
