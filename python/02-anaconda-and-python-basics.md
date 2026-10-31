# Video 2: Anaconda Installation and Python Basics

**Tracker:** Python sheet, #2  |  **Length:** about 19 minutes  |  **Type:** setup and first coding

## Anaconda

> **🧒 Simple version (like you're 5)**
>
> Anaconda is like a school backpack that already comes packed with pencils, a ruler, and notebooks. You install one thing, and you get Python plus lots of useful tools inside.

> **🔧 Technical version**
>
> Anaconda is a **distribution** of Python. It includes Python, the `conda` package and environment manager, hundreds of data science libraries, and tools like **Jupyter Notebook** and **Spyder**.

**Steps:**

1. Search "Anaconda download" and open the official site.
2. Download the installer for your system (Windows, Mac, or Linux).
3. Run it and accept the default options (he says check all the boxes).
4. Open **Anaconda Prompt** (Windows) or Terminal (Mac) and type `jupyter notebook`.

To open Jupyter in a specific folder, go there first with `cd`, then launch it:

```python
cd D:\my_python_notes
jupyter notebook
```

## Jupyter Notebook

> **🧒 Simple version (like you're 5)**
>
> Jupyter is a notebook made of little boxes. Some boxes hold notes for you to read. Other boxes hold instructions for the computer. When you press a button, the computer follows the instructions in that box and shows the answer right below it.

> **🔧 Technical version**
>
> Jupyter Notebook is a browser based, interactive environment. A notebook (`.ipynb` file) is made of **cells**:
>
> **Code cell:** runs Python and shows the output under it.
>
> **Markdown cell:** formatted text for notes and headings.
>
> It opens at a `localhost` address, which means it runs on your own computer, not on the internet. It's great for learning and data analysis because you see results step by step.

## The kernel

> **🧒 Simple version (like you're 5)**
>
> The kernel is the brain behind the notebook. It does all the thinking and remembers your work. If the brain gets confused or stuck, you restart it, like taking a nap and waking up fresh.

> **🔧 Technical version**
>
> The kernel is a background process that executes your code and keeps variables in memory. **Kernel > Restart** stops it and clears everything in memory, so you need to re-run your cells afterward. Use it when the notebook freezes.

## Useful shortcuts

| Keys | What it does |
| --- | --- |
| Shift + Enter | Run the cell and move to the next one |
| Esc, then A | Add a new cell above |
| Esc, then B | Add a new cell below |
| Esc, then M | Change cell to Markdown |
| Esc, then Y | Change cell to Code |
| Shift + Tab | Show help for a function (cursor inside its brackets) |

## Markdown basics

```python
# Big heading
## Smaller heading
- a bullet point
```

There must be a space after the `#`.

## Comments

> **🧒 Simple version (like you're 5)**
>
> Comments are sticky notes for people. The computer sees them and skips right over them.

> **🔧 Technical version**
>
> A `#` starts a single line comment. Python ignores everything after it on that line. Triple quotes `""" """` are often used for longer notes. Technically they are text strings, not comments, but Python ignores them if they are not stored anywhere.

```python
# This is a one line comment

"""
This is a longer note.
It can be many lines.
"""
```

## Data types

> **🧒 Simple version (like you're 5)**
>
> Data types are different kinds of things the computer can hold. Whole numbers like 5. Numbers with a dot like 5.5. Words like "hello". And yes or no answers, which Python calls True and False.

> **🔧 Technical version**
>
> The four basic types:

| Type | Name | Example | Meaning |
| --- | --- | --- | --- |
| `int` | Integer | `10` | Whole number |
| `float` | Floating point | `10.0` | Decimal number |
| `str` | String | `"hello"` | Text |
| `bool` | Boolean | `True`, `False` | Yes or no value |

Use `type()` to check what type something is:

```python
type(1)        # <class 'int'>
type(10.0)     # <class 'float'>
type("hello")  # <class 'str'>
type(True)     # <class 'bool'>
```

Strings can use single quotes `'hi'` or double quotes `"hi"`. Both work the same. `True` and `False` are reserved keywords, so they need a capital letter.

## Math operators

| Symbol | Meaning | Example | Result |
| --- | --- | --- | --- |
| `+` | Add | `1 + 1` | `2` |
| `-` | Subtract | `5 - 2` | `3` |
| `*` | Multiply | `2 * 5` | `10` |
| `/` | Divide | `10 / 2` | `5.0` |
| `%` | Remainder (modulus) | `10 % 3` | `1` |
| `**` | Power | `2 ** 3` | `8` |

> **🧒 Simple version (like you're 5)**
>
> The `%` sign tells you what is left over. If you share 10 candies between 3 friends, each gets 3, and 1 candy is left over. So 10 % 3 is 1.

> **🔧 Technical version**
>
> `/` always returns a `float`, even if the answer is whole (`10 / 2` gives `5.0`). `%` returns the remainder after division. It is often used to check if a number is even: `n % 2 == 0`.

## Order of operations (BODMAS)

> **🧒 Simple version (like you're 5)**
>
> Python does math in a fixed order, just like in school: brackets first, then powers, then multiply and divide, then add and subtract.

```python
2 + 3 * 4      # 14  (multiply first)
(2 + 3) * 4    # 20  (brackets first)
```

## Strings and math

Multiplying a string by a number repeats it:

```python
"Hi" * 3       # 'HiHiHi'
"10" * 2       # '1010'  (text, not the number 20!)
```

This is why data types matter. `"10"` in quotes is text, not a number.

## Variables

> **🧒 Simple version (like you're 5)**
>
> A variable is like a jar with a label on it. You put something inside the jar, write a name on the label, and later you can ask for the jar by its name.

> **🔧 Technical version**
>
> A variable is a name that points to a value, created with `=` (the assignment operator). Python is **dynamically typed**: you don't declare the type like `int a = 10` in C or Java. Python works out the type from the value, and a variable can later point to a different type.

```python
a = 10
type(a)          # int
a = "Krish"
type(a)          # str  (same name, new type)

a = 10
b = 20
print(a * b)     # 200
print(a / b)     # 0.5
```

## print()

`print()` shows something on the screen. In Jupyter, the last line of a cell displays automatically, but `print()` lets you show several things from one cell.

```python
print("Hello")
```

## Printing with .format()

> **🧒 Simple version (like you're 5)**
>
> Imagine a sentence with blank spaces in it, like a fill in the blanks worksheet. `.format()` fills the blanks with your words.

> **🔧 Technical version**
>
> `.format()` is a string method. Each `{}` is a placeholder filled with the arguments, in order. You can also use named placeholders, so the order of the arguments does not matter.

```python
first_name = "Krish"
last_name = "Naik"

# By position (order matters)
print("My first name is {} and last name is {}".format(first_name, last_name))

# By name (order does not matter)
print("My last name is {last}, first is {first}".format(first=first_name, last=last_name))
```

**Modern way (not in the video):** f-strings are shorter and used more today.

```python
print(f"My first name is {first_name} and last name is {last_name}")
```

## len()

> **🧒 Simple version (like you're 5)**
>
> `len()` counts how many letters (and spaces) are in a word or sentence.

> **🔧 Technical version**
>
> `len()` is a built in function that returns the number of items in an object. For a string, that is the number of characters, including spaces.

```python
len("Krish")      # 5
len("Hi there")   # 8  (the space counts)
```

## A first look at lists

> **🧒 Simple version (like you're 5)**
>
> A list is like a lunchbox with several things inside. You can put a sandwich, an apple, and a juice box together, even though they are different.

> **🔧 Technical version**
>
> A list is an ordered collection written with square brackets. It can hold items of different types. Lists are covered fully in the next video.

```python
type([1, 2, "apple"])   # <class 'list'>
```

## Heads up

> **⚠️ Heads up**
>
> He uses Python 3.7. Just install whatever version Anaconda currently offers.
>
> He says Python 2.7 support is ending soon. It already ended in January 2020, so always use Python 3.

## Small tips he mentioned

- **Tools inside Anaconda:** Besides Jupyter Notebook, you get **Spyder** (a coding editor, or IDE), and you can also launch RStudio and VS Code from it.
- **Why Jupyter for learning:** It's interactive. You see results right away, and help for functions is easy to see.
- **File menu:** open a notebook, **make a copy**, **rename**, **save and checkpoint** (a save point you can go back to).
- **Edit menu:** delete cells, move cells, and **merge** (combine) cells.
- **Insert menu:** insert a cell above or below.
- **Kernel menu:** **Restart** or **Restart & Clear Output** when things freeze.
- **The kernel is like a compiler:** He calls it a "compiler kind of stuff." Technically, Python is *interpreted*, and the kernel is the process running the interpreter. But the idea is the same: it's what runs your code.
- **Python errors are helpful:** Python gives clear error messages, which is one reason it's easy to learn. Read the last line of an error first.
- **Reserved keywords:** Words like `True`, `False`, `int`, `float` have special meaning in Python. Don't use them as variable names.
- **His code is on GitHub,** linked from his videos.

## Self-check

1. What does `10 % 3` give, and why?
2. What will `type(5.0)` return?
3. What is the difference between a code cell and a Markdown cell?
4. What does `"5" * 3` give? Why isn't it 15?
5. Rewrite the `.format()` example using an f-string.
6. What happens to your variables when you restart the kernel?

<details>
<summary>Show answers</summary>

1. `1`. 10 divided by 3 is 3 with 1 left over, and `%` gives the leftover.
2. `<class 'float'>`, because it has a decimal point.
3. A code cell runs Python. A Markdown cell shows formatted text, like notes and headings.
4. `'555'`. The `"5"` is a string (text) because of the quotes, so it repeats instead of multiplying.
5. `print(f"My first name is {first_name} and last name is {last_name}")`
6. They are all cleared from memory. You need to re-run your cells to create them again.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
# Video 2: Anaconda Installation and Python Basics

**Tracker:** Python sheet, #2  |  **Length:** about 19 minutes  |  **Type:** setup and first coding

## Anaconda

> **🧒 Simple version (like you're 5)**
>
> Anaconda is like a school backpack that already comes packed with pencils, a ruler, and notebooks. You install one thing, and you get Python plus lots of useful tools inside.

> **🔧 Technical version**
>
> Anaconda is a **distribution** of Python. It includes Python, the `conda` package and environment manager, hundreds of data science libraries, and tools like **Jupyter Notebook** and **Spyder**.

**Steps:**

1. Search "Anaconda download" and open the official site.
2. Download the installer for your system (Windows, Mac, or Linux).
3. Run it and accept the default options (he says check all the boxes).
4. Open **Anaconda Prompt** (Windows) or Terminal (Mac) and type `jupyter notebook`.

To open Jupyter in a specific folder, go there first with `cd`, then launch it:

```python
cd D:\my_python_notes
jupyter notebook
```

## Jupyter Notebook

> **🧒 Simple version (like you're 5)**
>
> Jupyter is a notebook made of little boxes. Some boxes hold notes for you to read. Other boxes hold instructions for the computer. When you press a button, the computer follows the instructions in that box and shows the answer right below it.

> **🔧 Technical version**
>
> Jupyter Notebook is a browser based, interactive environment. A notebook (`.ipynb` file) is made of **cells**:
>
> **Code cell:** runs Python and shows the output under it.
>
> **Markdown cell:** formatted text for notes and headings.
>
> It opens at a `localhost` address, which means it runs on your own computer, not on the internet. It's great for learning and data analysis because you see results step by step.

## The kernel

> **🧒 Simple version (like you're 5)**
>
> The kernel is the brain behind the notebook. It does all the thinking and remembers your work. If the brain gets confused or stuck, you restart it, like taking a nap and waking up fresh.

> **🔧 Technical version**
>
> The kernel is a background process that executes your code and keeps variables in memory. **Kernel > Restart** stops it and clears everything in memory, so you need to re-run your cells afterward. Use it when the notebook freezes.

## Useful shortcuts

| Keys | What it does |
| --- | --- |
| Shift + Enter | Run the cell and move to the next one |
| Esc, then A | Add a new cell above |
| Esc, then B | Add a new cell below |
| Esc, then M | Change cell to Markdown |
| Esc, then Y | Change cell to Code |
| Shift + Tab | Show help for a function (cursor inside its brackets) |

## Markdown basics

```python
# Big heading
## Smaller heading
- a bullet point
```

There must be a space after the `#`.

## Comments

> **🧒 Simple version (like you're 5)**
>
> Comments are sticky notes for people. The computer sees them and skips right over them.

> **🔧 Technical version**
>
> A `#` starts a single line comment. Python ignores everything after it on that line. Triple quotes `""" """` are often used for longer notes. Technically they are text strings, not comments, but Python ignores them if they are not stored anywhere.

```python
# This is a one line comment

"""
This is a longer note.
It can be many lines.
"""
```

## Data types

> **🧒 Simple version (like you're 5)**
>
> Data types are different kinds of things the computer can hold. Whole numbers like 5. Numbers with a dot like 5.5. Words like "hello". And yes or no answers, which Python calls True and False.

> **🔧 Technical version**
>
> The four basic types:

| Type | Name | Example | Meaning |
| --- | --- | --- | --- |
| `int` | Integer | `10` | Whole number |
| `float` | Floating point | `10.0` | Decimal number |
| `str` | String | `"hello"` | Text |
| `bool` | Boolean | `True`, `False` | Yes or no value |

Use `type()` to check what type something is:

```python
type(1)        # <class 'int'>
type(10.0)     # <class 'float'>
type("hello")  # <class 'str'>
type(True)     # <class 'bool'>
```

Strings can use single quotes `'hi'` or double quotes `"hi"`. Both work the same. `True` and `False` are reserved keywords, so they need a capital letter.

## Math operators

| Symbol | Meaning | Example | Result |
| --- | --- | --- | --- |
| `+` | Add | `1 + 1` | `2` |
| `-` | Subtract | `5 - 2` | `3` |
| `*` | Multiply | `2 * 5` | `10` |
| `/` | Divide | `10 / 2` | `5.0` |
| `%` | Remainder (modulus) | `10 % 3` | `1` |
| `**` | Power | `2 ** 3` | `8` |

> **🧒 Simple version (like you're 5)**
>
> The `%` sign tells you what is left over. If you share 10 candies between 3 friends, each gets 3, and 1 candy is left over. So 10 % 3 is 1.

> **🔧 Technical version**
>
> `/` always returns a `float`, even if the answer is whole (`10 / 2` gives `5.0`). `%` returns the remainder after division. It is often used to check if a number is even: `n % 2 == 0`.

## Order of operations (BODMAS)

> **🧒 Simple version (like you're 5)**
>
> Python does math in a fixed order, just like in school: brackets first, then powers, then multiply and divide, then add and subtract.

```python
2 + 3 * 4      # 14  (multiply first)
(2 + 3) * 4    # 20  (brackets first)
```

## Strings and math

Multiplying a string by a number repeats it:

```python
"Hi" * 3       # 'HiHiHi'
"10" * 2       # '1010'  (text, not the number 20!)
```

This is why data types matter. `"10"` in quotes is text, not a number.

## Variables

> **🧒 Simple version (like you're 5)**
>
> A variable is like a jar with a label on it. You put something inside the jar, write a name on the label, and later you can ask for the jar by its name.

> **🔧 Technical version**
>
> A variable is a name that points to a value, created with `=` (the assignment operator). Python is **dynamically typed**: you don't declare the type like `int a = 10` in C or Java. Python works out the type from the value, and a variable can later point to a different type.

```python
a = 10
type(a)          # int
a = "Krish"
type(a)          # str  (same name, new type)

a = 10
b = 20
print(a * b)     # 200
print(a / b)     # 0.5
```

## print()

`print()` shows something on the screen. In Jupyter, the last line of a cell displays automatically, but `print()` lets you show several things from one cell.

```python
print("Hello")
```

## Printing with .format()

> **🧒 Simple version (like you're 5)**
>
> Imagine a sentence with blank spaces in it, like a fill in the blanks worksheet. `.format()` fills the blanks with your words.

> **🔧 Technical version**
>
> `.format()` is a string method. Each `{}` is a placeholder filled with the arguments, in order. You can also use named placeholders, so the order of the arguments does not matter.

```python
first_name = "Krish"
last_name = "Naik"

# By position (order matters)
print("My first name is {} and last name is {}".format(first_name, last_name))

# By name (order does not matter)
print("My last name is {last}, first is {first}".format(first=first_name, last=last_name))
```

**Modern way (not in the video):** f-strings are shorter and used more today.

```python
print(f"My first name is {first_name} and last name is {last_name}")
```

## len()

> **🧒 Simple version (like you're 5)**
>
> `len()` counts how many letters (and spaces) are in a word or sentence.

> **🔧 Technical version**
>
> `len()` is a built in function that returns the number of items in an object. For a string, that is the number of characters, including spaces.

```python
len("Krish")      # 5
len("Hi there")   # 8  (the space counts)
```

## A first look at lists

> **🧒 Simple version (like you're 5)**
>
> A list is like a lunchbox with several things inside. You can put a sandwich, an apple, and a juice box together, even though they are different.

> **🔧 Technical version**
>
> A list is an ordered collection written with square brackets. It can hold items of different types. Lists are covered fully in the next video.

```python
type([1, 2, "apple"])   # <class 'list'>
```

## Heads up

> **⚠️ Heads up**
>
> He uses Python 3.7. Just install whatever version Anaconda currently offers.
>
> He says Python 2.7 support is ending soon. It already ended in January 2020, so always use Python 3.

## Self-check

1. What does `10 % 3` give, and why?
2. What will `type(5.0)` return?
3. What is the difference between a code cell and a Markdown cell?
4. What does `"5" * 3` give? Why isn't it 15?
5. Rewrite the `.format()` example using an f-string.
6. What happens to your variables when you restart the kernel?

<details>
<summary>Show answers</summary>

1. `1`. 10 divided by 3 is 3 with 1 left over, and `%` gives the leftover.
2. `<class 'float'>`, because it has a decimal point.
3. A code cell runs Python. A Markdown cell shows formatted text, like notes and headings.
4. `'555'`. The `"5"` is a string (text) because of the quotes, so it repeats instead of multiplying.
5. `print(f"My first name is {first_name} and last name is {last_name}")`
6. They are all cleared from memory. You need to re-run your cells to create them again.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
