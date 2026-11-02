# Video 6: NumPy and Inbuilt Functions

**Tracker:** Python sheet, #6  |  **Length:** about 26 minutes  |  **Type:** coding

This is the first big data science library. He says you'll use NumPy all the time in exploratory data analysis, and the next video (Pandas) builds on it.

## What is NumPy?

> **🧒 Simple version (like you're 5)**
>
> Imagine an egg carton. Every spot holds the same kind of thing (eggs), and the spots are in neat rows and columns. NumPy makes "egg cartons" for numbers, and it can do math on every egg at once, super fast.

> **🔧 Technical version**
>
> NumPy (Numerical Python) is a general purpose **array processing package**. It gives you a fast, **multi-dimensional array** object (`ndarray`) and many built in tools to work with arrays. It is fast because its core is written in **C and C++**. His notebook also calls it **the fundamental package for scientific computing with Python**. Machine learning is mostly math on large amounts of numbers, which is why NumPy matters so much.

## Array vs list

> **🧒 Simple version (like you're 5)**
>
> A list is a junk drawer: you can throw in a pencil, a toy, and a sock. An array is the egg carton: everything inside must be the same kind.

> **🔧 Technical version**
>
> An **array** stores values of the **same data type**. A Python **list** can mix types. Because all items are the same type, NumPy can store them tightly in memory and run operations much faster than looping through a list.

**Extra tip (not in the video):** If you give NumPy mixed types, it converts everything to one common type. `np.array([1, 2, "a"])` turns all items into strings.

## Installing and importing

NumPy comes with Anaconda, so you probably already have it. If not:

```bash
pip install numpy          # if you installed plain Python
conda install numpy        # if you use Anaconda
```

Run these in Command Prompt / Anaconda Prompt, not inside Python.

```python
import numpy as np
```

`np` is an **alias**, a short nickname. Everyone uses `np`, so you'll see it in almost all data science code. After this, every NumPy function starts with `np.`

## Creating a 1D array

```python
my_lst = [1, 2, 3, 4, 5]
arr = np.array(my_lst)      # converts the list into an array

type(arr)                   # <class 'numpy.ndarray'>
arr                         # array([1, 2, 3, 4, 5])
arr.shape                   # (5,)
```

- `ndarray` means "n-dimensional array."
- Press **Shift + Tab** inside `np.array(` to read what it does.
- **Count the brackets** to know the dimensions. One `[` at the start means 1D.
- For a 1D array, `.shape` just shows how many elements: `(5,)`.

## Creating a 2D array

> **🧒 Simple version (like you're 5)**
>
> A 1D array is one line of kids standing in a row. A 2D array is a whole class sitting in rows and columns of desks.

```python
lst1 = [1, 2, 3, 4, 5]
lst2 = [2, 3, 4, 5, 6]
lst3 = [9, 7, 6, 8, 9]

arr = np.array([lst1, lst2, lst3])
arr
# array([[1, 2, 3, 4, 5],
#        [2, 3, 4, 5, 6],
#        [9, 7, 6, 8, 9]])

arr.shape        # (3, 5)  -> 3 rows, 5 columns
```

> **🔧 Technical version**
>
> Passing a list of lists creates a 2D array. Each inner list becomes a **row**. In `.shape`, the **first number is always rows**, the second is columns. Two opening brackets `[[` means 2D, three `[[[` means 3D, and so on.

**Why 2D matters:** Most data you work with is a table: rows are records, columns are features. After cleaning and feature engineering, the data is turned into arrays and given to machine learning algorithms, and fast array math makes training faster.

## Reshaping

> **🧒 Simple version (like you're 5)**
>
> You have 15 LEGO bricks in 3 rows of 5. You can rebuild them as 5 rows of 3. But you can't make 5 rows of 4, because that needs 20 bricks and you only have 15.

```python
arr.reshape(5, 3)     # 5 rows, 3 columns  (5 x 3 = 15, works)
arr.reshape(5, 4)     # ValueError: cannot reshape array of size 15 into shape (5,4)
arr.reshape(1, 15)    # 1 row, 15 columns
```

> **🔧 Technical version**
>
> `reshape()` returns an array with the **same data in a new shape**. The total number of elements must stay the same. `reshape(1, 15)` looks like one line, but it is still **2D** (notice the double brackets `[[...]]`).

## Indexing

He repeats his rule: **for any new data structure, first learn how to get data out of it.**

### 1D indexing

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr[3]        # 4   (index starts at 0)
```

### 2D indexing

> **🧒 Simple version (like you're 5)**
>
> To find a seat in a movie theater, you need the row AND the seat number. A 2D array works the same way: `[row, column]`.

```python
arr = np.array([[1, 2, 3, 4, 5],
                [2, 3, 4, 5, 6],
                [9, 7, 6, 8, 9]])
```

| | col 0 | col 1 | col 2 | col 3 | col 4 |
| --- | --- | --- | --- | --- | --- |
| **row 0** | 1 | 2 | 3 | 4 | 5 |
| **row 1** | 2 | 3 | 4 | 5 | 6 |
| **row 2** | 9 | 7 | 6 | 8 | 9 |

> **🔧 Technical version**
>
> The syntax is `arr[rows, columns]`. **Left of the comma = rows, right of the comma = columns.** Each side can be a slice `start:stop`, and like lists, `stop` is **not included**. A lone `:` means "all."

```python
arr[:, :]        # all rows, all columns (the whole array)

arr[0:2, 0:2]    # rows 0-1, columns 0-1
# array([[1, 2],
#        [2, 3]])

arr[1:3, 3:]     # rows 1-2, columns 3 to the end
# array([[5, 6],
#        [8, 9]])
```

**How to work it out:** Find the value in the table. Write down which rows it's in and which columns. Then turn those into slices, remembering to add 1 to the stop.

### His assignment

He asks you to pick out more pieces of this array on your own. The transcript is a bit unclear on the exact numbers, so here are two versions to practice:

1. Get `[[3, 4, 5], [4, 5, 6]]`
2. Get `[[4, 5, 6], [6, 8, 9]]`

(Answers are in the self-check section.)

## np.arange(): a range of numbers

```python
np.arange(0, 10)        # array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
np.arange(0, 10, 2)     # array([0, 2, 4, 6, 8])
```

> **🔧 Technical version**
>
> `np.arange(start, stop, step)` creates a 1D array from `start` up to but **not including** `stop`, jumping by `step`. Note the spelling: **arange** (one r), short for "array range." It's a quick way to make sample arrays.

## np.linspace(): evenly spaced points

> **🧒 Simple version (like you're 5)**
>
> You have a 10 meter rope and want to place 5 flags with exactly equal gaps, including one at each end. `linspace` tells you where to put each flag.

```python
np.linspace(1, 10, 50)     # 50 evenly spaced numbers from 1 to 10 (10 included)
```

> **🔧 Technical version**
>
> `np.linspace(start, stop, num)` returns `num` **evenly spaced** values. Unlike `arange`, the `stop` value **is included** by default. He mentions it's useful in deep learning when you need to quickly create or initialize a set of points.

> **⚠️ Heads up**
>
> In the video it sounds like he says the points are "not equally divided." That's a caption mix-up. `linspace` points are always **evenly** spaced.

## Broadcasting

> **🧒 Simple version (like you're 5)**
>
> Instead of painting each fence board one by one, you pour paint over a whole section at once.

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr[3:] = 100
arr      # array([1, 2, 3, 100, 100, 100, 100, 100, 100])
```

> **🔧 Technical version**
>
> **Broadcasting** means NumPy applies a single value (or a smaller array) across many elements at once, without a loop.

## Copy vs reference (very important)

> **🧒 Simple version (like you're 5)**
>
> `arr1 = arr` is like giving your friend a **second key to your same house**. If your friend paints a wall, your house changes too. `arr.copy()` is like building your friend **their own house** that looks the same. Painting theirs doesn't touch yours.

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr1 = arr               # NOT a copy, both names point to the SAME array
arr1[3:] = 500
arr                      # array([1, 2, 3, 500, 500, 500, 500, 500, 500])  arr changed too!

arr1 = arr.copy()        # a real, separate copy
arr1[3:] = 1000
arr                      # unchanged
arr1                     # has the 1000s
```

> **🔧 Technical version**
>
> NumPy arrays are **reference types**: assigning with `=` makes both variables share the **same memory**, so a change through one shows up in the other. `.copy()` creates a **new block of memory**. He compares this to **value types** (like a single integer), where assigning makes an independent value. He says you'll hit this bug in bigger projects if you're not careful.

> **⚠️ Heads up**
>
> Technically, every Python variable is a reference. Integers and strings only *seem* like value types because they can't be changed in place. Lists behave like arrays here too: `b = a` shares the same list.

## Conditions and element-wise math

He says these are **very useful in exploratory data analysis.**

```python
arr = np.array([1, 2, 3, 100, 100, 500])

arr < 2          # array([ True, False, False, False, False, False])
arr * 2          # every element times 2
arr / 2          # every element divided by 2
arr % 2          # remainder of every element
```

> **🧒 Simple version (like you're 5)**
>
> Asking `arr < 2` is like asking every kid in line, "Are you shorter than 2 feet?" Each kid answers yes or no. Putting that question inside brackets, `arr[arr < 2]`, is like saying, "Only the kids who said yes, step forward."

```python
arr[arr < 2]       # array([1])          only the values that pass the test
arr[arr < 300]     # array([1, 2, 3, 100, 100])
```

> **🔧 Technical version**
>
> Comparisons on an array return a **boolean array**. Using a boolean array inside `[]` is called **boolean indexing** (or filtering). It keeps only the elements where the condition is `True`. Math operators work **element-wise**, on every item at once.

He mentions you can use **multiple conditions** too. **Extra tip:** use `&` (and) and `|` (or), with brackets around each condition:

```python
arr[(arr > 1) & (arr < 300)]    # array([2, 3, 100, 100])
```

Plain `and` / `or` don't work here.

### Math between two arrays (from his notebook)

```python
arr1 = np.arange(0, 10).reshape(2, 5)
arr2 = np.arange(0, 10).reshape(2, 5)
arr1 * arr2
# array([[ 0,  1,  4,  9, 16],
#        [25, 36, 49, 64, 81]])
```

> **🧒 Simple version (like you're 5)**
>
> Two egg cartons of the same size are lined up. Each egg is multiplied with the egg in the same spot in the other carton.

> **🔧 Technical version**
>
> When two arrays have the **same shape**, `*`, `+`, `-`, `/` work **element by element**: position `[0, 0]` with `[0, 0]`, and so on. This is **not** matrix multiplication (that's `@` or `np.dot()`, which you'll meet later).

## np.ones()

```python
np.ones(4)                 # array([1., 1., 1., 1.])   floats by default
np.ones(4, dtype=int)      # array([1, 1, 1, 1])
np.ones((2, 5))            # 2 rows, 5 columns of 1s
```

- The `1.` with a dot means float. The **default `dtype` is float**.
- Use `dtype=int` or `dtype=float` to choose.
- For 2D, pass the shape as a tuple: `(rows, columns)`.

**Extra tip (not in the video):** `np.zeros()` works the same way but fills with 0s.

## Random numbers

> **🧒 Simple version (like you're 5)**
>
> These are like rolling dice. Every time you roll, you get different numbers. Different functions are like different kinds of dice.

| Function | What you get | Example |
| --- | --- | --- |
| `np.random.rand(3, 3)` | Decimals between 0 and 1, every value equally likely (**uniform distribution**) | 3 x 3 array |
| `np.random.randn(4, 4)` | Decimals from a **standard normal distribution** (mean 0, std 1). Most near 0, a few far away | 4 x 4 array |
| `np.random.randint(0, 100, 8)` | 8 whole numbers from 0 up to (not including) 100 | 1D array of 8 |
| `np.random.random_sample((1, 5))` | Decimals between 0.0 and 1.0 | 1 x 5 array |

```python
np.random.randint(0, 100, 8).reshape(2, 4)    # 8 random ints as 2 rows x 4 columns
```

- **Values change every time you run the cell,** because they're random.
- For standard normal distribution, he points you to his **statistics playlist** (in your tracker).
- He uses `rand` with a 3 x 3 shape, `randn` with a 4 x 4 shape. Shapes are up to you.

**Extra tip (not in the video):** Use `np.random.seed(42)` before generating to get the same "random" numbers every run. This matters when you want results others can repeat.

### Seeing the bell curve

He takes values from `randn`, puts them into a Pandas DataFrame, and plots them with Seaborn. The chart shows a **bell curve**, the shape of a **Gaussian (normal) distribution**. It isn't perfectly smooth because it's a sample. He says not to worry about Pandas and Seaborn yet. Both get their own videos.

```python
import pandas as pd
import seaborn as sns

df = pd.DataFrame(np.random.randn(1000, 1))
sns.histplot(df, kde=True)
```

> **⚠️ Heads up**
>
> Older videos use `sns.distplot()`. It's deprecated in newer Seaborn. Use `sns.histplot(..., kde=True)` or `sns.kdeplot()` instead, as above.
>
> His notebook's exact line is `sns.distplot(pd.DataFrame(arr_ex.reshape(16, 1)))`. It reshapes the 4 x 4 `randn` array into 16 rows and 1 column first, so all 16 values form one column to plot. Also, the notebook never runs `import pandas as pd`, so `pd` would be undefined. Add that import if you run it.

## Small tips he mentioned

- **Extra practice from his notebook,** using `arr1 = np.arange(0, 10).reshape(2, 5)`:
  - `arr1[1:, :2]` → `array([[5, 6]])` (row 1 onward, first two columns)
  - `arr1[:, 3:]` → `array([[3, 4], [8, 9]])` (all rows, columns 3 onward)
  - `np.arange(0, 10).reshape(5, 2)` → 5 rows, 2 columns
  - `np.random.randint(0, 100, 8).reshape(4, 2)` → his notebook uses 4 x 2, the video says 2 x 4. Both work, since 4 x 2 = 2 x 4 = 8.

- **Shift + Tab** inside any function's brackets shows its parameters. He uses it for `array`, `reshape`, `arange`, `linspace`, `ones`, and the random functions.
- **Practice indexing a lot.** He admits it can be confusing at first. It's the skill you'll use most.
- **There are many more built in functions.** Don't try to learn them all now.
- **NumPy comes back** in the Pandas video and throughout EDA.

## Self-check

1. Why is NumPy faster than plain Python lists?
2. What does `arr.shape` return for a 2D array with 4 rows and 6 columns?
3. Can you reshape an array of 12 elements into `(3, 5)`? Why or why not?
4. Using the 3 x 5 array above, what does `arr[2, 0]` give?
5. What's the difference between `np.arange(0, 10, 2)` and `np.linspace(0, 10, 5)`?
6. After `b = a` and `b[0] = 99`, does `a` change? How do you avoid it?
7. How do you get only the values greater than 5 from an array `x`?
8. What's the difference between `np.random.rand` and `np.random.randn`?

<details>
<summary>Show answers</summary>

1. Its core is written in C and C++, and arrays store one data type tightly in memory, so operations run on all elements at once without Python loops.
2. `(4, 6)`. Rows first, then columns.
3. No. `3 x 5 = 15`, but you only have 12 elements. The total must match.
4. `9`. Row 2, column 0.
5. `arange` uses a **step** and excludes the stop: `[0, 2, 4, 6, 8]`. `linspace` uses a **count** of points and includes the stop: `[0, 2.5, 5, 7.5, 10]`.
6. Yes, because both names share the same memory. Use `b = a.copy()`.
7. `x[x > 5]`
8. `rand` gives uniform values between 0 and 1. `randn` gives values from a standard normal distribution (mean 0, standard deviation 1), which can be negative.

**Assignment answers:**

1. `arr[0:2, 2:5]` gives `[[3, 4, 5], [4, 5, 6]]`
2. `arr[1:3, 2:5]` gives `[[4, 5, 6], [6, 8, 9]]`

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
# Video 6: NumPy and Inbuilt Functions

**Tracker:** Python sheet, #6  |  **Length:** about 26 minutes  |  **Type:** coding

This is the first big data science library. He says you'll use NumPy all the time in exploratory data analysis, and the next video (Pandas) builds on it.

## What is NumPy?

> **🧒 Simple version (like you're 5)**
>
> Imagine an egg carton. Every spot holds the same kind of thing (eggs), and the spots are in neat rows and columns. NumPy makes "egg cartons" for numbers, and it can do math on every egg at once, super fast.

> **🔧 Technical version**
>
> NumPy (Numerical Python) is a general purpose **array processing package**. It gives you a fast, **multi-dimensional array** object (`ndarray`) and many built in tools to work with arrays. It is fast because its core is written in **C and C++**. Machine learning is mostly math on large amounts of numbers, which is why NumPy matters so much.

## Array vs list

> **🧒 Simple version (like you're 5)**
>
> A list is a junk drawer: you can throw in a pencil, a toy, and a sock. An array is the egg carton: everything inside must be the same kind.

> **🔧 Technical version**
>
> An **array** stores values of the **same data type**. A Python **list** can mix types. Because all items are the same type, NumPy can store them tightly in memory and run operations much faster than looping through a list.

**Extra tip (not in the video):** If you give NumPy mixed types, it converts everything to one common type. `np.array([1, 2, "a"])` turns all items into strings.

## Installing and importing

NumPy comes with Anaconda, so you probably already have it. If not:

```bash
pip install numpy          # if you installed plain Python
conda install numpy        # if you use Anaconda
```

Run these in Command Prompt / Anaconda Prompt, not inside Python.

```python
import numpy as np
```

`np` is an **alias**, a short nickname. Everyone uses `np`, so you'll see it in almost all data science code. After this, every NumPy function starts with `np.`

## Creating a 1D array

```python
my_lst = [1, 2, 3, 4, 5]
arr = np.array(my_lst)      # converts the list into an array

type(arr)                   # <class 'numpy.ndarray'>
arr                         # array([1, 2, 3, 4, 5])
arr.shape                   # (5,)
```

- `ndarray` means "n-dimensional array."
- Press **Shift + Tab** inside `np.array(` to read what it does.
- **Count the brackets** to know the dimensions. One `[` at the start means 1D.
- For a 1D array, `.shape` just shows how many elements: `(5,)`.

## Creating a 2D array

> **🧒 Simple version (like you're 5)**
>
> A 1D array is one line of kids standing in a row. A 2D array is a whole class sitting in rows and columns of desks.

```python
lst1 = [1, 2, 3, 4, 5]
lst2 = [2, 3, 4, 5, 6]
lst3 = [9, 7, 6, 8, 9]

arr = np.array([lst1, lst2, lst3])
arr
# array([[1, 2, 3, 4, 5],
#        [2, 3, 4, 5, 6],
#        [9, 7, 6, 8, 9]])

arr.shape        # (3, 5)  -> 3 rows, 5 columns
```

> **🔧 Technical version**
>
> Passing a list of lists creates a 2D array. Each inner list becomes a **row**. In `.shape`, the **first number is always rows**, the second is columns. Two opening brackets `[[` means 2D, three `[[[` means 3D, and so on.

**Why 2D matters:** Most data you work with is a table: rows are records, columns are features. After cleaning and feature engineering, the data is turned into arrays and given to machine learning algorithms, and fast array math makes training faster.

## Reshaping

> **🧒 Simple version (like you're 5)**
>
> You have 15 LEGO bricks in 3 rows of 5. You can rebuild them as 5 rows of 3. But you can't make 5 rows of 4, because that needs 20 bricks and you only have 15.

```python
arr.reshape(5, 3)     # 5 rows, 3 columns  (5 x 3 = 15, works)
arr.reshape(5, 4)     # ValueError: cannot reshape array of size 15 into shape (5,4)
arr.reshape(1, 15)    # 1 row, 15 columns
```

> **🔧 Technical version**
>
> `reshape()` returns an array with the **same data in a new shape**. The total number of elements must stay the same. `reshape(1, 15)` looks like one line, but it is still **2D** (notice the double brackets `[[...]]`).

## Indexing

He repeats his rule: **for any new data structure, first learn how to get data out of it.**

### 1D indexing

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr[3]        # 4   (index starts at 0)
```

### 2D indexing

> **🧒 Simple version (like you're 5)**
>
> To find a seat in a movie theater, you need the row AND the seat number. A 2D array works the same way: `[row, column]`.

```python
arr = np.array([[1, 2, 3, 4, 5],
                [2, 3, 4, 5, 6],
                [9, 7, 6, 8, 9]])
```

| | col 0 | col 1 | col 2 | col 3 | col 4 |
| --- | --- | --- | --- | --- | --- |
| **row 0** | 1 | 2 | 3 | 4 | 5 |
| **row 1** | 2 | 3 | 4 | 5 | 6 |
| **row 2** | 9 | 7 | 6 | 8 | 9 |

> **🔧 Technical version**
>
> The syntax is `arr[rows, columns]`. **Left of the comma = rows, right of the comma = columns.** Each side can be a slice `start:stop`, and like lists, `stop` is **not included**. A lone `:` means "all."

```python
arr[:, :]        # all rows, all columns (the whole array)

arr[0:2, 0:2]    # rows 0-1, columns 0-1
# array([[1, 2],
#        [2, 3]])

arr[1:3, 3:]     # rows 1-2, columns 3 to the end
# array([[5, 6],
#        [8, 9]])
```

**How to work it out:** Find the value in the table. Write down which rows it's in and which columns. Then turn those into slices, remembering to add 1 to the stop.

### His assignment

He asks you to pick out more pieces of this array on your own. The transcript is a bit unclear on the exact numbers, so here are two versions to practice:

1. Get `[[3, 4, 5], [4, 5, 6]]`
2. Get `[[4, 5, 6], [6, 8, 9]]`

(Answers are in the self-check section.)

## np.arange(): a range of numbers

```python
np.arange(0, 10)        # array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
np.arange(0, 10, 2)     # array([0, 2, 4, 6, 8])
```

> **🔧 Technical version**
>
> `np.arange(start, stop, step)` creates a 1D array from `start` up to but **not including** `stop`, jumping by `step`. Note the spelling: **arange** (one r), short for "array range." It's a quick way to make sample arrays.

## np.linspace(): evenly spaced points

> **🧒 Simple version (like you're 5)**
>
> You have a 10 meter rope and want to place 5 flags with exactly equal gaps, including one at each end. `linspace` tells you where to put each flag.

```python
np.linspace(1, 10, 50)     # 50 evenly spaced numbers from 1 to 10 (10 included)
```

> **🔧 Technical version**
>
> `np.linspace(start, stop, num)` returns `num` **evenly spaced** values. Unlike `arange`, the `stop` value **is included** by default. He mentions it's useful in deep learning when you need to quickly create or initialize a set of points.

> **⚠️ Heads up**
>
> In the video it sounds like he says the points are "not equally divided." That's a caption mix-up. `linspace` points are always **evenly** spaced.

## Broadcasting

> **🧒 Simple version (like you're 5)**
>
> Instead of painting each fence board one by one, you pour paint over a whole section at once.

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr[3:] = 100
arr      # array([1, 2, 3, 100, 100, 100, 100, 100, 100])
```

> **🔧 Technical version**
>
> **Broadcasting** means NumPy applies a single value (or a smaller array) across many elements at once, without a loop.

## Copy vs reference (very important)

> **🧒 Simple version (like you're 5)**
>
> `arr1 = arr` is like giving your friend a **second key to your same house**. If your friend paints a wall, your house changes too. `arr.copy()` is like building your friend **their own house** that looks the same. Painting theirs doesn't touch yours.

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
arr1 = arr               # NOT a copy, both names point to the SAME array
arr1[3:] = 500
arr                      # array([1, 2, 3, 500, 500, 500, 500, 500, 500])  arr changed too!

arr1 = arr.copy()        # a real, separate copy
arr1[3:] = 1000
arr                      # unchanged
arr1                     # has the 1000s
```

> **🔧 Technical version**
>
> NumPy arrays are **reference types**: assigning with `=` makes both variables share the **same memory**, so a change through one shows up in the other. `.copy()` creates a **new block of memory**. He compares this to **value types** (like a single integer), where assigning makes an independent value. He says you'll hit this bug in bigger projects if you're not careful.

> **⚠️ Heads up**
>
> Technically, every Python variable is a reference. Integers and strings only *seem* like value types because they can't be changed in place. Lists behave like arrays here too: `b = a` shares the same list.

## Conditions and element-wise math

He says these are **very useful in exploratory data analysis.**

```python
arr = np.array([1, 2, 3, 100, 100, 500])

arr < 2          # array([ True, False, False, False, False, False])
arr * 2          # every element times 2
arr / 2          # every element divided by 2
arr % 2          # remainder of every element
```

> **🧒 Simple version (like you're 5)**
>
> Asking `arr < 2` is like asking every kid in line, "Are you shorter than 2 feet?" Each kid answers yes or no. Putting that question inside brackets, `arr[arr < 2]`, is like saying, "Only the kids who said yes, step forward."

```python
arr[arr < 2]       # array([1])          only the values that pass the test
arr[arr < 300]     # array([1, 2, 3, 100, 100])
```

> **🔧 Technical version**
>
> Comparisons on an array return a **boolean array**. Using a boolean array inside `[]` is called **boolean indexing** (or filtering). It keeps only the elements where the condition is `True`. Math operators work **element-wise**, on every item at once.

He mentions you can use **multiple conditions** too. **Extra tip:** use `&` (and) and `|` (or), with brackets around each condition:

```python
arr[(arr > 1) & (arr < 300)]    # array([2, 3, 100, 100])
```

Plain `and` / `or` don't work here.

## np.ones()

```python
np.ones(4)                 # array([1., 1., 1., 1.])   floats by default
np.ones(4, dtype=int)      # array([1, 1, 1, 1])
np.ones((2, 5))            # 2 rows, 5 columns of 1s
```

- The `1.` with a dot means float. The **default `dtype` is float**.
- Use `dtype=int` or `dtype=float` to choose.
- For 2D, pass the shape as a tuple: `(rows, columns)`.

**Extra tip (not in the video):** `np.zeros()` works the same way but fills with 0s.

## Random numbers

> **🧒 Simple version (like you're 5)**
>
> These are like rolling dice. Every time you roll, you get different numbers. Different functions are like different kinds of dice.

| Function | What you get | Example |
| --- | --- | --- |
| `np.random.rand(3, 3)` | Decimals between 0 and 1, every value equally likely (**uniform distribution**) | 3 x 3 array |
| `np.random.randn(4, 4)` | Decimals from a **standard normal distribution** (mean 0, std 1). Most near 0, a few far away | 4 x 4 array |
| `np.random.randint(0, 100, 8)` | 8 whole numbers from 0 up to (not including) 100 | 1D array of 8 |
| `np.random.random_sample((1, 5))` | Decimals between 0.0 and 1.0 | 1 x 5 array |

```python
np.random.randint(0, 100, 8).reshape(2, 4)    # 8 random ints as 2 rows x 4 columns
```

- **Values change every time you run the cell,** because they're random.
- For standard normal distribution, he points you to his **statistics playlist** (in your tracker).
- He uses `rand` with a 3 x 3 shape, `randn` with a 4 x 4 shape. Shapes are up to you.

**Extra tip (not in the video):** Use `np.random.seed(42)` before generating to get the same "random" numbers every run. This matters when you want results others can repeat.

### Seeing the bell curve

He takes values from `randn`, puts them into a Pandas DataFrame, and plots them with Seaborn. The chart shows a **bell curve**, the shape of a **Gaussian (normal) distribution**. It isn't perfectly smooth because it's a sample. He says not to worry about Pandas and Seaborn yet. Both get their own videos.

```python
import pandas as pd
import seaborn as sns

df = pd.DataFrame(np.random.randn(1000, 1))
sns.histplot(df, kde=True)
```

> **⚠️ Heads up**
>
> Older videos use `sns.distplot()`. It's deprecated in newer Seaborn. Use `sns.histplot(..., kde=True)` or `sns.kdeplot()` instead, as above.

## Small tips he mentioned

- **Shift + Tab** inside any function's brackets shows its parameters. He uses it for `array`, `reshape`, `arange`, `linspace`, `ones`, and the random functions.
- **Practice indexing a lot.** He admits it can be confusing at first. It's the skill you'll use most.
- **There are many more built in functions.** Don't try to learn them all now.
- **NumPy comes back** in the Pandas video and throughout EDA.

## Self-check

1. Why is NumPy faster than plain Python lists?
2. What does `arr.shape` return for a 2D array with 4 rows and 6 columns?
3. Can you reshape an array of 12 elements into `(3, 5)`? Why or why not?
4. Using the 3 x 5 array above, what does `arr[2, 0]` give?
5. What's the difference between `np.arange(0, 10, 2)` and `np.linspace(0, 10, 5)`?
6. After `b = a` and `b[0] = 99`, does `a` change? How do you avoid it?
7. How do you get only the values greater than 5 from an array `x`?
8. What's the difference between `np.random.rand` and `np.random.randn`?

<details>
<summary>Show answers</summary>

1. Its core is written in C and C++, and arrays store one data type tightly in memory, so operations run on all elements at once without Python loops.
2. `(4, 6)`. Rows first, then columns.
3. No. `3 x 5 = 15`, but you only have 12 elements. The total must match.
4. `9`. Row 2, column 0.
5. `arange` uses a **step** and excludes the stop: `[0, 2, 4, 6, 8]`. `linspace` uses a **count** of points and includes the stop: `[0, 2.5, 5, 7.5, 10]`.
6. Yes, because both names share the same memory. Use `b = a.copy()`.
7. `x[x > 5]`
8. `rand` gives uniform values between 0 and 1. `randn` gives values from a standard normal distribution (mean 0, standard deviation 1), which can be negative.

**Assignment answers:**

1. `arr[0:2, 2:5]` gives `[[3, 4, 5], [4, 5, 6]]`
2. `arr[1:3, 2:5]` gives `[[4, 5, 6], [6, 8, 9]]`

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
