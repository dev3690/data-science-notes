# Video 4: Python Lists and Boolean Variables

**Tracker:** Python sheet, #4  |  **Length:** about 22 minutes  |  **Type:** coding

He says data structures like lists, dictionaries, and sets matter a lot in data analysis, because once you load data you need to work with it in these forms.

## Boolean values

> **🧒 Simple version (like you're 5)**
>
> A boolean is a light switch. It can only be ON or OFF. In Python, ON is `True` and OFF is `False`.

> **🔧 Technical version**
>
> `True` and `False` are the two boolean constants, of type `bool`. They need a capital first letter. The `bool()` function turns another value into a boolean. Empty or zero values become `False`, and most other values become `True`.

```python
type(True)      # <class 'bool'>
bool(0)         # False
bool(5)         # True
bool("")        # False  (empty string)
bool("hi")      # True
```

## String methods that return True or False

> **🧒 Simple version (like you're 5)**
>
> These are yes or no questions you can ask a word. Is it all letters? Does it start with K? Python answers True or False.

> **🔧 Technical version**
>
> Strings have many built in methods. Type a string variable, then a dot, then press **Tab** in Jupyter to see them all. You don't need to memorize them. Know they exist and look them up when needed.

| Method | Asks | Example | Result |
| --- | --- | --- | --- |
| `.isalnum()` | Only letters and/or numbers? | `"Krish123".isalnum()` | `True` |
| `.isalpha()` | Only letters? | `"Krish123".isalpha()` | `False` |
| `.isdigit()` | Only digits? | `"123".isdigit()` | `True` |
| `.istitle()` | Every word starts with a capital? | `"Hello World".istitle()` | `True` |
| `.isupper()` | All capitals? | `"HI".isupper()` | `True` |
| `.islower()` | All small letters? | `"hi".islower()` | `True` |
| `.isspace()` | Only spaces? | `"   ".isspace()` | `True` |
| `.startswith()` | Starts with this? | `"Krish".startswith("K")` | `True` |
| `.endswith()` | Ends with this? | `"Krish".endswith("h")` | `True` |

`startswith()` and `endswith()` are **case sensitive**. `"Krish".startswith("k")` is `False` because of the small k.

> **⚠️ Heads up**
>
> **From his notebook:** he tests these methods on `my_str = "Krish123"`. Run them yourself on that string. You'll get `isalnum()` True, `isalpha()` False, `isdigit()` False, `istitle()` True.
>
> The comments in his notebook have a few mistakes, so trust the table above instead:
>
> - `isalnum()` is commented "check if all char are numbers." Wrong: it checks for **letters and/or numbers**. Even `"Krish".isalnum()` is `True`. It's only `False` if there's a space or symbol, like `"Krish Naik"`.
> - `isdigit()` is commented "test if string contains digits." It actually checks that **every** character is a digit. `"Krish123".isdigit()` is `False`.

> **⚠️ Heads up**
>
> In his notebook, the and/or example uses `str_example.isnum()`. There is **no** `isnum()` method, so that line gives an `AttributeError`. The real method is `isnumeric()`, which is what this note uses below.

## Logical operators: and, or

> **🧒 Simple version (like you're 5)**
>
> **and** is like a parent saying: you can go out if you finish homework AND clean your room. Both must be done. **or** is like: you can have ice cream OR cake. Just one is enough.

> **🔧 Technical version**
>
> `and` returns `True` only if both sides are `True`. `or` returns `True` if at least one side is `True`. There is also `not`, which flips a value. These work like logic gates in digital electronics.

| A | B | A and B | A or B |
| --- | --- | --- | --- |
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

```python
my_str = "Krish"
my_str.isalpha() or my_str.isnumeric()    # True or False  ->  True
my_str.isalpha() and my_str.isnumeric()   # True and False ->  False
not True                                   # False
```

## Lists

> **🧒 Simple version (like you're 5)**
>
> A list is a lunchbox with little sections, lined up in order. You can put different things in it, take things out, swap them, and add more. Each section has a number so you can find things.

> **🔧 Technical version**
>
> A list is an **ordered, mutable** collection of items, written in square brackets `[]` with commas between items. **Ordered** means items keep their position. **Mutable** means you can change it after creating it. Items can be different types.

```python
empty1 = []
empty2 = list()          # another way to make an empty list

subjects = ["Maths", "Chemistry", 100, 200, 300, 204]
type(subjects)           # <class 'list'>
len(subjects)            # 6
```

## Indexing: finding an item by its position

> **🧒 Simple version (like you're 5)**
>
> Python starts counting at 0, not 1. So the first item is at spot 0, the second at spot 1, and so on. It's like floors in some buildings, where the ground floor is floor 0.

| Index | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- |
| Item | "Maths" | "Chemistry" | 100 | 200 | 300 | 204 |

```python
subjects[0]     # 'Maths'
subjects[2]     # 100
subjects[5]     # 204
subjects[6]     # IndexError: there is no index 6
```

**Extra tip (not in the video):** negative numbers count from the end. `subjects[-1]` gives `204`, the last item.

## Slicing: getting a range of items

> **🧒 Simple version (like you're 5)**
>
> Slicing is like cutting a piece of a sandwich. You say where to start cutting and where to stop. The stop spot itself is not included in your piece.

> **🔧 Technical version**
>
> The syntax is `list[start:stop]`. It includes `start` but **excludes** `stop`. If you leave out `start`, it begins at 0. If you leave out `stop`, it goes to the end.

```python
subjects[:]       # everything
subjects[1:]      # ['Chemistry', 100, 200, 300, 204]
subjects[1:5]     # ['Chemistry', 100, 200, 300]   (index 5 not included)
subjects[:2]      # ['Maths', 'Chemistry']
```

## Adding items: append, insert, extend

> **🧒 Simple version (like you're 5)**
>
> **append** puts one thing at the very end of the line. **insert** squeezes a thing into a spot you pick. **extend** pours a whole bag of things into the end, one by one.

| Method | What it does | Example |
| --- | --- | --- |
| `.append(x)` | Adds one item at the end | `lst.append("Krish")` |
| `.insert(i, x)` | Adds item x at index i | `lst.insert(2, "Ravi")` |
| `.extend(items)` | Adds each item from another list at the end | `lst.extend([8, 9])` |

```python
lst = [1, 2, 3]
lst.append([8, 9])    # [1, 2, 3, [8, 9]]   <- a list inside a list (nested)

lst = [1, 2, 3]
lst.extend([8, 9])    # [1, 2, 3, 8, 9]     <- added as separate items
```

A list inside another list is called a **nested list**.

> **⚠️ Heads up**
>
> The captions make it sound like `append("John", "Bala")`, but his notebook shows the correct version with brackets: `lst.append(["John", "Bala"])`. Without the brackets, you'd get an error, because `append()` takes only one item.

## Removing items: pop

> **🧒 Simple version (like you're 5)**
>
> `pop()` takes the last thing out of the lunchbox and hands it to you. If you give it a number, it takes out the thing in that spot instead.

> **🔧 Technical version**
>
> `.pop()` removes and **returns** the last item. `.pop(i)` removes and returns the item at index `i`.

```python
lst = [1, 2, 3, 4, 5]
lst.pop()       # returns 5, list is now [1, 2, 3, 4]
lst.pop(0)      # returns 1, list is now [2, 3, 4]
```

## Counting and searching: count, index

```python
lst = [1, 1, 2, 3, 4, 5]
lst.count(1)        # 2   (1 appears two times)
lst.index(1)        # 0   (position of the FIRST 1)
lst.index(1, 1, 4)  # 1   (search for 1 starting from index 1, stopping before 4)
```

`count()` and `index()` take a **value** to look for. The extra numbers in `index()` are **positions** that limit where it searches.

## Built in functions that work on lists

```python
lst = [1, 2, 3, 4, 5]
len(lst)    # 5
sum(lst)    # 15
min(lst)    # 1
max(lst)    # 5
```

These are general Python functions, not list methods. That's why you write `sum(lst)` and not `lst.sum()`.

## Multiplying a list

> **🧒 Simple version (like you're 5)**
>
> Multiplying a list does not multiply the numbers inside. It makes copies of the whole list and sticks them together, like photocopying a page.

```python
lst = [1, 2, 3]
lst * 2     # [1, 2, 3, 1, 2, 3]
```

To multiply each number, you'll use a loop, list comprehension, or NumPy later.

## Small tips he mentioned

- **From his notebook: booleans act like numbers.** In math, `True` behaves like `1` and `False` like `0`. So `True + True` is `2`. This becomes handy later: `sum()` on a list of True/False values counts how many are True.
- **From his notebook:** after the insert example (`lst.insert(2, "Naik")`), he appends `["Hello", "World"]` and `[4, 5]` to show more nested lists. Try them and print the list each time.

- **Comparison operators** (`==`, `!=`, `>`, `<`, `>=`, `<=`) are listed at the start of this session but not really taught. They compare two values and give `True` or `False`, like `5 > 3` gives `True`.
- **Don't memorize all the methods.** Press **Tab** to see them and **Shift + Tab** to read what one does. Searching Google with the right keywords is a real skill.
- **This all comes back later.** He'll reuse lists and booleans a lot when doing exploratory data analysis.
- **Different indexing styles** show up again in NumPy arrays and Pandas, so learn list indexing well now.
- **Ways to build a list:** type the items directly, or start empty with `[]` or `list()` and keep appending.

## Self-check

1. What does `bool(0)` return?
2. What does `True and False` give? What about `True or False`?
3. If `lst = ["a", "b", "c", "d"]`, what is `lst[1:3]`?
4. What is the difference between `append([8, 9])` and `extend([8, 9])`?
5. What does `[5, 6] * 3` give?
6. Is `"Krish".endswith("H")` True or False? Why?

<details>
<summary>Show answers</summary>

1. `False`, because zero counts as false.
2. `True and False` gives `False`. `True or False` gives `True`.
3. `['b', 'c']`. It starts at index 1 and stops before index 3.
4. `append` adds the whole list as one item, making a nested list `[..., [8, 9]]`. `extend` adds 8 and 9 as separate items.
5. `[5, 6, 5, 6, 5, 6]`. It repeats the list three times.
6. `False`. The name ends with a small h, and the check is case sensitive.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
# Video 4: Python Lists and Boolean Variables

**Tracker:** Python sheet, #4  |  **Length:** about 22 minutes  |  **Type:** coding

He says data structures like lists, dictionaries, and sets matter a lot in data analysis, because once you load data you need to work with it in these forms.

## Boolean values

> **🧒 Simple version (like you're 5)**
>
> A boolean is a light switch. It can only be ON or OFF. In Python, ON is `True` and OFF is `False`.

> **🔧 Technical version**
>
> `True` and `False` are the two boolean constants, of type `bool`. They need a capital first letter. The `bool()` function turns another value into a boolean. Empty or zero values become `False`, and most other values become `True`.

```python
type(True)      # <class 'bool'>
bool(0)         # False
bool(5)         # True
bool("")        # False  (empty string)
bool("hi")      # True
```

## String methods that return True or False

> **🧒 Simple version (like you're 5)**
>
> These are yes or no questions you can ask a word. Is it all letters? Does it start with K? Python answers True or False.

> **🔧 Technical version**
>
> Strings have many built in methods. Type a string variable, then a dot, then press **Tab** in Jupyter to see them all. You don't need to memorize them. Know they exist and look them up when needed.

| Method | Asks | Example | Result |
| --- | --- | --- | --- |
| `.isalnum()` | Only letters and/or numbers? | `"Krish123".isalnum()` | `True` |
| `.isalpha()` | Only letters? | `"Krish123".isalpha()` | `False` |
| `.isdigit()` | Only digits? | `"123".isdigit()` | `True` |
| `.istitle()` | Every word starts with a capital? | `"Hello World".istitle()` | `True` |
| `.isupper()` | All capitals? | `"HI".isupper()` | `True` |
| `.islower()` | All small letters? | `"hi".islower()` | `True` |
| `.isspace()` | Only spaces? | `"   ".isspace()` | `True` |
| `.startswith()` | Starts with this? | `"Krish".startswith("K")` | `True` |
| `.endswith()` | Ends with this? | `"Krish".endswith("h")` | `True` |

`startswith()` and `endswith()` are **case sensitive**. `"Krish".startswith("k")` is `False` because of the small k.

> **⚠️ Heads up**
>
> In the video, `isalnum()` on a plain name seems to show False. That is not right. `"Krish".isalnum()` is `True`, because letters alone count. It only becomes `False` if there is a space or symbol, like `"Krish Naik"` or `"Krish!"`.

## Logical operators: and, or

> **🧒 Simple version (like you're 5)**
>
> **and** is like a parent saying: you can go out if you finish homework AND clean your room. Both must be done. **or** is like: you can have ice cream OR cake. Just one is enough.

> **🔧 Technical version**
>
> `and` returns `True` only if both sides are `True`. `or` returns `True` if at least one side is `True`. There is also `not`, which flips a value. These work like logic gates in digital electronics.

| A | B | A and B | A or B |
| --- | --- | --- | --- |
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

```python
my_str = "Krish"
my_str.isalpha() or my_str.isnumeric()    # True or False  ->  True
my_str.isalpha() and my_str.isnumeric()   # True and False ->  False
not True                                   # False
```

## Lists

> **🧒 Simple version (like you're 5)**
>
> A list is a lunchbox with little sections, lined up in order. You can put different things in it, take things out, swap them, and add more. Each section has a number so you can find things.

> **🔧 Technical version**
>
> A list is an **ordered, mutable** collection of items, written in square brackets `[]` with commas between items. **Ordered** means items keep their position. **Mutable** means you can change it after creating it. Items can be different types.

```python
empty1 = []
empty2 = list()          # another way to make an empty list

subjects = ["Maths", "Chemistry", 100, 200, 300, 204]
type(subjects)           # <class 'list'>
len(subjects)            # 6
```

## Indexing: finding an item by its position

> **🧒 Simple version (like you're 5)**
>
> Python starts counting at 0, not 1. So the first item is at spot 0, the second at spot 1, and so on. It's like floors in some buildings, where the ground floor is floor 0.

| Index | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- |
| Item | "Maths" | "Chemistry" | 100 | 200 | 300 | 204 |

```python
subjects[0]     # 'Maths'
subjects[2]     # 100
subjects[5]     # 204
subjects[6]     # IndexError: there is no index 6
```

**Extra tip (not in the video):** negative numbers count from the end. `subjects[-1]` gives `204`, the last item.

## Slicing: getting a range of items

> **🧒 Simple version (like you're 5)**
>
> Slicing is like cutting a piece of a sandwich. You say where to start cutting and where to stop. The stop spot itself is not included in your piece.

> **🔧 Technical version**
>
> The syntax is `list[start:stop]`. It includes `start` but **excludes** `stop`. If you leave out `start`, it begins at 0. If you leave out `stop`, it goes to the end.

```python
subjects[:]       # everything
subjects[1:]      # ['Chemistry', 100, 200, 300, 204]
subjects[1:5]     # ['Chemistry', 100, 200, 300]   (index 5 not included)
subjects[:2]      # ['Maths', 'Chemistry']
```

## Adding items: append, insert, extend

> **🧒 Simple version (like you're 5)**
>
> **append** puts one thing at the very end of the line. **insert** squeezes a thing into a spot you pick. **extend** pours a whole bag of things into the end, one by one.

| Method | What it does | Example |
| --- | --- | --- |
| `.append(x)` | Adds one item at the end | `lst.append("Krish")` |
| `.insert(i, x)` | Adds item x at index i | `lst.insert(2, "Ravi")` |
| `.extend(items)` | Adds each item from another list at the end | `lst.extend([8, 9])` |

```python
lst = [1, 2, 3]
lst.append([8, 9])    # [1, 2, 3, [8, 9]]   <- a list inside a list (nested)

lst = [1, 2, 3]
lst.extend([8, 9])    # [1, 2, 3, 8, 9]     <- added as separate items
```

A list inside another list is called a **nested list**.

> **⚠️ Heads up**
>
> In the video, he writes `append("John", "Bala")` with two values. That actually gives an error, because `append()` takes only one item. To add a nested list, put the items in brackets: `append(["John", "Bala"])`.

## Removing items: pop

> **🧒 Simple version (like you're 5)**
>
> `pop()` takes the last thing out of the lunchbox and hands it to you. If you give it a number, it takes out the thing in that spot instead.

> **🔧 Technical version**
>
> `.pop()` removes and **returns** the last item. `.pop(i)` removes and returns the item at index `i`.

```python
lst = [1, 2, 3, 4, 5]
lst.pop()       # returns 5, list is now [1, 2, 3, 4]
lst.pop(0)      # returns 1, list is now [2, 3, 4]
```

## Counting and searching: count, index

```python
lst = [1, 1, 2, 3, 4, 5]
lst.count(1)        # 2   (1 appears two times)
lst.index(1)        # 0   (position of the FIRST 1)
lst.index(1, 1, 4)  # 1   (search for 1 starting from index 1, stopping before 4)
```

`count()` and `index()` take a **value** to look for. The extra numbers in `index()` are **positions** that limit where it searches.

## Built in functions that work on lists

```python
lst = [1, 2, 3, 4, 5]
len(lst)    # 5
sum(lst)    # 15
min(lst)    # 1
max(lst)    # 5
```

These are general Python functions, not list methods. That's why you write `sum(lst)` and not `lst.sum()`.

## Multiplying a list

> **🧒 Simple version (like you're 5)**
>
> Multiplying a list does not multiply the numbers inside. It makes copies of the whole list and sticks them together, like photocopying a page.

```python
lst = [1, 2, 3]
lst * 2     # [1, 2, 3, 1, 2, 3]
```

To multiply each number, you'll use a loop, list comprehension, or NumPy later.

## Small tips he mentioned

- **Comparison operators** (`==`, `!=`, `>`, `<`, `>=`, `<=`) are listed at the start of this session but not really taught. They compare two values and give `True` or `False`, like `5 > 3` gives `True`.
- **Don't memorize all the methods.** Press **Tab** to see them and **Shift + Tab** to read what one does. Searching Google with the right keywords is a real skill.
- **This all comes back later.** He'll reuse lists and booleans a lot when doing exploratory data analysis.
- **Different indexing styles** show up again in NumPy arrays and Pandas, so learn list indexing well now.
- **Ways to build a list:** type the items directly, or start empty with `[]` or `list()` and keep appending.

## Self-check

1. What does `bool(0)` return?
2. What does `True and False` give? What about `True or False`?
3. If `lst = ["a", "b", "c", "d"]`, what is `lst[1:3]`?
4. What is the difference between `append([8, 9])` and `extend([8, 9])`?
5. What does `[5, 6] * 3` give?
6. Is `"Krish".endswith("H")` True or False? Why?

<details>
<summary>Show answers</summary>

1. `False`, because zero counts as false.
2. `True and False` gives `False`. `True or False` gives `True`.
3. `['b', 'c']`. It starts at index 1 and stops before index 3.
4. `append` adds the whole list as one item, making a nested list `[..., [8, 9]]`. `extend` adds 8 and 9 as separate items.
5. `[5, 6, 5, 6, 5, 6]`. It repeats the list three times.
6. `False`. The name ends with a small h, and the check is case sensitive.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
# Video 4: Python Lists and Boolean Variables

**Tracker:** Python sheet, #4  |  **Length:** about 22 minutes  |  **Type:** coding

He says data structures like lists, dictionaries, and sets matter a lot in data analysis, because once you load data you need to work with it in these forms.

## Boolean values

> **🧒 Simple version (like you're 5)**
>
> A boolean is a light switch. It can only be ON or OFF. In Python, ON is `True` and OFF is `False`.

> **🔧 Technical version**
>
> `True` and `False` are the two boolean constants, of type `bool`. They need a capital first letter. The `bool()` function turns another value into a boolean. Empty or zero values become `False`, and most other values become `True`.

```python
type(True)      # <class 'bool'>
bool(0)         # False
bool(5)         # True
bool("")        # False  (empty string)
bool("hi")      # True
```

## String methods that return True or False

> **🧒 Simple version (like you're 5)**
>
> These are yes or no questions you can ask a word. Is it all letters? Does it start with K? Python answers True or False.

> **🔧 Technical version**
>
> Strings have many built in methods. Type a string variable, then a dot, then press **Tab** in Jupyter to see them all. You don't need to memorize them. Know they exist and look them up when needed.

| Method | Asks | Example | Result |
| --- | --- | --- | --- |
| `.isalnum()` | Only letters and/or numbers? | `"Krish123".isalnum()` | `True` |
| `.isalpha()` | Only letters? | `"Krish123".isalpha()` | `False` |
| `.isdigit()` | Only digits? | `"123".isdigit()` | `True` |
| `.istitle()` | Every word starts with a capital? | `"Hello World".istitle()` | `True` |
| `.isupper()` | All capitals? | `"HI".isupper()` | `True` |
| `.islower()` | All small letters? | `"hi".islower()` | `True` |
| `.isspace()` | Only spaces? | `"   ".isspace()` | `True` |
| `.startswith()` | Starts with this? | `"Krish".startswith("K")` | `True` |
| `.endswith()` | Ends with this? | `"Krish".endswith("h")` | `True` |

`startswith()` and `endswith()` are **case sensitive**. `"Krish".startswith("k")` is `False` because of the small k.

> **⚠️ Heads up**
>
> In the video, `isalnum()` on a plain name seems to show False. That is not right. `"Krish".isalnum()` is `True`, because letters alone count. It only becomes `False` if there is a space or symbol, like `"Krish Naik"` or `"Krish!"`.

## Logical operators: and, or

> **🧒 Simple version (like you're 5)**
>
> **and** is like a parent saying: you can go out if you finish homework AND clean your room. Both must be done. **or** is like: you can have ice cream OR cake. Just one is enough.

> **🔧 Technical version**
>
> `and` returns `True` only if both sides are `True`. `or` returns `True` if at least one side is `True`. There is also `not`, which flips a value. These work like logic gates in digital electronics.

| A | B | A and B | A or B |
| --- | --- | --- | --- |
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

```python
my_str = "Krish"
my_str.isalpha() or my_str.isnumeric()    # True or False  ->  True
my_str.isalpha() and my_str.isnumeric()   # True and False ->  False
not True                                   # False
```

## Lists

> **🧒 Simple version (like you're 5)**
>
> A list is a lunchbox with little sections, lined up in order. You can put different things in it, take things out, swap them, and add more. Each section has a number so you can find things.

> **🔧 Technical version**
>
> A list is an **ordered, mutable** collection of items, written in square brackets `[]` with commas between items. **Ordered** means items keep their position. **Mutable** means you can change it after creating it. Items can be different types.

```python
empty1 = []
empty2 = list()          # another way to make an empty list

subjects = ["Maths", "Chemistry", 100, 200, 300, 204]
type(subjects)           # <class 'list'>
len(subjects)            # 6
```

## Indexing: finding an item by its position

> **🧒 Simple version (like you're 5)**
>
> Python starts counting at 0, not 1. So the first item is at spot 0, the second at spot 1, and so on. It's like floors in some buildings, where the ground floor is floor 0.

| Index | 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- | --- |
| Item | "Maths" | "Chemistry" | 100 | 200 | 300 | 204 |

```python
subjects[0]     # 'Maths'
subjects[2]     # 100
subjects[5]     # 204
subjects[6]     # IndexError: there is no index 6
```

**Extra tip (not in the video):** negative numbers count from the end. `subjects[-1]` gives `204`, the last item.

## Slicing: getting a range of items

> **🧒 Simple version (like you're 5)**
>
> Slicing is like cutting a piece of a sandwich. You say where to start cutting and where to stop. The stop spot itself is not included in your piece.

> **🔧 Technical version**
>
> The syntax is `list[start:stop]`. It includes `start` but **excludes** `stop`. If you leave out `start`, it begins at 0. If you leave out `stop`, it goes to the end.

```python
subjects[:]       # everything
subjects[1:]      # ['Chemistry', 100, 200, 300, 204]
subjects[1:5]     # ['Chemistry', 100, 200, 300]   (index 5 not included)
subjects[:2]      # ['Maths', 'Chemistry']
```

## Adding items: append, insert, extend

> **🧒 Simple version (like you're 5)**
>
> **append** puts one thing at the very end of the line. **insert** squeezes a thing into a spot you pick. **extend** pours a whole bag of things into the end, one by one.

| Method | What it does | Example |
| --- | --- | --- |
| `.append(x)` | Adds one item at the end | `lst.append("Krish")` |
| `.insert(i, x)` | Adds item x at index i | `lst.insert(2, "Ravi")` |
| `.extend(items)` | Adds each item from another list at the end | `lst.extend([8, 9])` |

```python
lst = [1, 2, 3]
lst.append([8, 9])    # [1, 2, 3, [8, 9]]   <- a list inside a list (nested)

lst = [1, 2, 3]
lst.extend([8, 9])    # [1, 2, 3, 8, 9]     <- added as separate items
```

A list inside another list is called a **nested list**.

> **⚠️ Heads up**
>
> In the video, he writes `append("John", "Bala")` with two values. That actually gives an error, because `append()` takes only one item. To add a nested list, put the items in brackets: `append(["John", "Bala"])`.

## Removing items: pop

> **🧒 Simple version (like you're 5)**
>
> `pop()` takes the last thing out of the lunchbox and hands it to you. If you give it a number, it takes out the thing in that spot instead.

> **🔧 Technical version**
>
> `.pop()` removes and **returns** the last item. `.pop(i)` removes and returns the item at index `i`.

```python
lst = [1, 2, 3, 4, 5]
lst.pop()       # returns 5, list is now [1, 2, 3, 4]
lst.pop(0)      # returns 1, list is now [2, 3, 4]
```

## Counting and searching: count, index

```python
lst = [1, 1, 2, 3, 4, 5]
lst.count(1)        # 2   (1 appears two times)
lst.index(1)        # 0   (position of the FIRST 1)
lst.index(1, 1, 4)  # 1   (search for 1 starting from index 1, stopping before 4)
```

`count()` and `index()` take a **value** to look for. The extra numbers in `index()` are **positions** that limit where it searches.

## Built in functions that work on lists

```python
lst = [1, 2, 3, 4, 5]
len(lst)    # 5
sum(lst)    # 15
min(lst)    # 1
max(lst)    # 5
```

These are general Python functions, not list methods. That's why you write `sum(lst)` and not `lst.sum()`.

## Multiplying a list

> **🧒 Simple version (like you're 5)**
>
> Multiplying a list does not multiply the numbers inside. It makes copies of the whole list and sticks them together, like photocopying a page.

```python
lst = [1, 2, 3]
lst * 2     # [1, 2, 3, 1, 2, 3]
```

To multiply each number, you'll use a loop, list comprehension, or NumPy later.

## Self-check

1. What does `bool(0)` return?
2. What does `True and False` give? What about `True or False`?
3. If `lst = ["a", "b", "c", "d"]`, what is `lst[1:3]`?
4. What is the difference between `append([8, 9])` and `extend([8, 9])`?
5. What does `[5, 6] * 3` give?
6. Is `"Krish".endswith("H")` True or False? Why?

<details>
<summary>Show answers</summary>

1. `False`, because zero counts as false.
2. `True and False` gives `False`. `True or False` gives `True`.
3. `['b', 'c']`. It starts at index 1 and stops before index 3.
4. `append` adds the whole list as one item, making a nested list `[..., [8, 9]]`. `extend` adds 8 and 9 as separate items.
5. `[5, 6, 5, 6, 5, 6]`. It repeats the list three times.
6. `False`. The name ends with a small h, and the check is case sensitive.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
