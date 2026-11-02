# Video 7: Pandas, DataFrame and Data Series (Part 1)

**Tracker:** Python sheet, #7  |  **Type:** coding

He says **NumPy and Pandas are the backbone of exploratory data analysis (EDA)**, so you need to be very good at both. Pandas is split into parts. This first part covers what Pandas is, DataFrames, Series, and basic operations.

## What is Pandas?

> **🧒 Simple version (like you're 5)**
>
> Pandas turns Python into a super smart spreadsheet. You can open a big table of data, look at it, find things, fix mistakes, and count things, all with short commands.

> **🔧 Technical version**
>
> Pandas is an **open source, BSD-licensed** Python library that gives you **high performance, easy to use data structures and data analysis tools**. Its two main data structures are the **DataFrame** (a table) and the **Series** (a single row or column). It is built on top of NumPy.

> **⚠️ Heads up**
>
> The captions say "PhD licensed." He means **BSD**, a type of open source license that lets anyone use the code freely.

## Importing

```python
import pandas as pd
import numpy as np
```

`pd` is the standard alias for Pandas, just like `np` for NumPy. Import both, because you'll often use them together.

## What is a DataFrame?

> **🧒 Simple version (like you're 5)**
>
> A DataFrame is like a sheet in Excel. It has rows going across, columns going down, names on top of the columns, and labels on the side of the rows.

> **🔧 Technical version**
>
> A DataFrame is a **2D table** with **rows and columns**. Each column has a name (**column index**) and each row has a label (**row index**). When you load a CSV or Excel file with Pandas, it becomes a DataFrame that looks just like the original sheet.

## Creating a DataFrame

`pd.DataFrame()` has these main parameters (press **Shift + Tab** to see them):

| Parameter | What it is |
| --- | --- |
| `data` | The values, in 2D form (rows and columns) |
| `index` | Names for the **rows** |
| `columns` | Names for the **columns** |
| `dtype` | Data type for the values (optional) |

```python
df = pd.DataFrame(
    np.arange(0, 20).reshape(5, 4),
    index=["Row1", "Row2", "Row3", "Row4", "Row5"],
    columns=["Column1", "Column2", "Column3", "Column4"]
)
df
```

|  | Column1 | Column2 | Column3 | Column4 |
| --- | --- | --- | --- | --- |
| **Row1** | 0 | 1 | 2 | 3 |
| **Row2** | 4 | 5 | 6 | 7 |
| **Row3** | 8 | 9 | 10 | 11 |
| **Row4** | 12 | 13 | 14 | 15 |
| **Row5** | 16 | 17 | 18 | 19 |

**What's happening:**
- `np.arange(0, 20)` makes 20 numbers (0 to 19). `.reshape(5, 4)` makes them 5 rows by 4 columns.
- You need **5 row names** because there are 5 rows, and **4 column names** because there are 4 columns. The counts must match.
- Row and column names matter because you use them to **find and pull out data** later.

**The three things to give a DataFrame:** data, row index, and column names.

## Saving to a CSV file

```python
df.to_csv("Test1.csv")
```

> **🧒 Simple version (like you're 5)**
>
> This saves your table as a file, so you can open it later in Excel or share it.

> **🔧 Technical version**
>
> CSV means **comma separated values**: a plain text file where each row is a line and values are separated by commas. `to_csv()` writes the DataFrame to a CSV file in the same folder as your notebook. You can find it in the Jupyter file browser and open it there.

**Extra tip (not in the video):** `df.to_csv("Test1.csv", index=False)` saves without the row labels, which is often what you want.

## Accessing data: .loc and .iloc

> **🧒 Simple version (like you're 5)**
>
> There are two ways to find a seat in a classroom. **loc** uses name tags: "find the desk labeled Row1." **iloc** uses counting: "find the desk in the first row, second seat." The "i" in iloc stands for **integer** (counting numbers).

> **🔧 Technical version**
>
> - **`.loc[]`** selects by **label** (the names of rows and columns). He focuses on rows with it.
> - **`.iloc[]`** selects by **integer position**, like NumPy. Rows go left of the comma, columns go right: `df.iloc[rows, columns]`.

### Using .loc

```python
df.loc["Row1"]
# Column1    0
# Column2    1
# Column3    2
# Column4    3

type(df.loc["Row1"])     # <class 'pandas.core.series.Series'>
```

Picking a single row gives you a **Series**.

### Using .iloc

```python
df.iloc[:, :]        # all rows, all columns
df.iloc[0:2, 0:2]    # rows 0-1, columns 0-1
#       Column1  Column2
# Row1        0        1
# Row2        4        5

df.iloc[:, 1:]       # all rows, skip the first column
```

Like lists and NumPy, the **stop number is not included**, and counting **starts at 0**.

**Small tip he gives:** In the **R** programming language, indexing starts at **1**. In Python, it starts at **0**. Easy to mix up if you've used R.

## DataFrame vs Series

> **🧒 Simple version (like you're 5)**
>
> A DataFrame is the whole chocolate bar. A Series is one strip broken off it, either one row or one column.

> **🔧 Technical version**
>
> A **Series** is **1-dimensional**: a single row or a single column, with an index of labels. A **DataFrame** is **2-dimensional**: rows and columns together. A DataFrame is basically a collection of Series that share the same row index.

### When do you get a Series vs a DataFrame?

```python
type(df.iloc[0, :])      # Series     (one row picked by a single number)
type(df.iloc[0:1, :])    # DataFrame  (a slice, even though it's one row)
type(df.iloc[0:2, 0:1])  # DataFrame  (a slice, even though it's one column)
type(df["Column3"])      # Series     (one column by name)
type(df[["Column3"]])    # DataFrame  (a list with one column name)
```

> **⚠️ Heads up**
>
> In the video, he says you get a DataFrame when there's more than one row **and** more than one column, and he gets a bit confused during the demo. The clearer rule is:
>
> - Picking with a **single label or number** → that dimension disappears → **Series**.
> - Picking with a **slice** (`0:2`) or a **list** (`[...]`) → the shape stays a table → **DataFrame**.
>
> A Series also has no column names across the top, and its "name" shows at the bottom. That's a quick way to tell them apart when you print them.

## Converting a DataFrame to a NumPy array

```python
df.iloc[:, 1:].values
# array([[ 1,  2,  3],
#        [ 5,  6,  7],
#        [ 9, 10, 11],
#        [13, 14, 15],
#        [17, 18, 19]])

df.iloc[:, 1:].values.shape    # (5, 3)
```

> **🔧 Technical version**
>
> `.values` drops the row and column labels and gives you just the numbers as a NumPy array. He says you'll do this a lot when feeding data into **machine learning algorithms**, which usually expect arrays.

**Extra tip (not in the video):** `.to_numpy()` does the same thing and is the newer, recommended way.

## Must know operations

### Check for missing values: isnull().sum()

```python
df.isnull().sum()
# Column1    0
# Column2    0
# Column3    0
# Column4    0
```

> **🧒 Simple version (like you're 5)**
>
> This counts the empty boxes in each column of your table, like checking a worksheet for questions you forgot to answer.

> **🔧 Technical version**
>
> `isnull()` marks each cell `True` if it's missing (NaN) and `False` if not. `.sum()` adds up the `True` values per column. He says this is **one of the first things to check as soon as you load any dataset.**

### See the first rows: head()

```python
df.head()     # shows the first 5 rows
```

### Count how often each value appears: value_counts()

```python
df["Column1"].value_counts()
# 0     1
# 4     1
# 8     1
# 12    1
# 16    1
```

> **🧒 Simple version (like you're 5)**
>
> If a column lists everyone's favorite fruit, this tells you "apple: 5 people, banana: 3 people."

> **🔧 Technical version**
>
> `value_counts()` counts how many times each unique value appears in a column. It's most useful for **categorical features** (like city, gender, or product type), to see how many of each category there are.

### See the unique values: unique()

```python
df["Column1"].unique()     # array([ 0,  4,  8, 12, 16])
```

`unique()` lists each different value **once**, even if it's repeated many times.

## Selecting columns by name

```python
df["Column3"]                  # one column  -> Series
df[["Column3", "Column4"]]     # two columns -> DataFrame (note the double brackets)
```

> **🔧 Technical version**
>
> For **multiple columns, put the names in a list** inside the brackets. The outer `[]` selects, the inner `[]` is the list.

**Mistakes he makes on purpose (and leaves in the video):**
1. `df["Column3", "Column4"]` without the inner list → **error**. You need `df[["Column3", "Column4"]]`.
2. A typo in the column name → `KeyError: ... not in index`. **Column names must match exactly**, including capitals and spaces. Copy and paste the names if unsure.

He keeps these mistakes in so you see what real errors look like.

## Coming up in Part 2

He says the next part covers `info()`, `describe()`, correlation, and reading data from CSV files and other sources.

## Small tips he mentioned

- **NumPy and Pandas are must haves for EDA.** Practice both a lot.
- **Use Shift + Tab** on `pd.DataFrame(` to see its parameters.
- **Open files in Jupyter:** after saving a CSV, you can find and open it from the Jupyter file list.
- **Run `isnull().sum()` first** whenever you load a new dataset.
- **R starts counting at 1, Python at 0.**

## Self-check

1. What three things do you usually give `pd.DataFrame()`?
2. What's the difference between `.loc` and `.iloc`?
3. What type is `df.loc["Row2"]`? What does it contain?
4. Using the table above, what does `df.iloc[2:4, 1:3]` give?
5. How do you select `Column1` and `Column4` together?
6. Why would you use `.values` on a DataFrame?
7. Which command shows how many missing values each column has?
8. What's the difference between `value_counts()` and `unique()`?

<details>
<summary>Show answers</summary>

1. The data, the row index (row names), and the column names.
2. `.loc` selects by **label** (names). `.iloc` selects by **integer position** (counting from 0).
3. A **Series** with the Row2 values: Column1 = 4, Column2 = 5, Column3 = 6, Column4 = 7.
4. Rows 2-3 (Row3, Row4) and columns 1-2 (Column2, Column3):
```
         Column2  Column3
   Row3        9       10
   Row4       13       14
```
5. `df[["Column1", "Column4"]]`
6. To turn it into a NumPy array (no labels), which machine learning algorithms usually expect.
7. `df.isnull().sum()`
8. `value_counts()` shows each value **and how many times** it appears. `unique()` just lists each different value once.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
