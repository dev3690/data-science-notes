# Video 5: Python Sets, Dictionaries and Tuples

**Tracker:** Python sheet, #5  |  **Length:** about 16 minutes  |  **Type:** coding

He says these data structures matter a lot in exploratory data analysis. You don't need to memorize every built in function. Know how each one works, especially **how to get data out of it**, and look up the rest when you need it.

## Quick comparison

| | List | Set | Dictionary | Tuple |
| --- | --- | --- | --- | --- |
| Brackets | `[ ]` | `{ }` | `{key: value}` | `( )` |
| Ordered? | Yes | No | Yes (keeps insertion order) | Yes |
| Can change it? | Yes | Yes | Yes | **No** |
| Duplicates allowed? | Yes | **No** | Keys: no. Values: yes | Yes |
| How you get items | By position `[0]` | No indexing | By key `["car1"]` | By position `[0]` |

## Sets

> **🧒 Simple version (like you're 5)**
>
> A set is like a bag of marbles where every marble must be a different color. If you try to add a second red marble, the bag just says "I already have red" and ignores it. The marbles are all mixed up inside, so there's no "first" or "second" marble.

> **🔧 Technical version**
>
> A set is an **unordered, mutable** collection with **no duplicate elements**. It is iterable, so you can loop through it. It follows the math idea of a set and is built on a **hash table**, which makes checking "is this item in the set?" very fast.

```python
empty_set = set()              # the way to make an empty set
type(empty_set)                # <class 'set'>

nums = {1, 2, 3, 4, 3}
nums                           # {1, 2, 3, 4}   the duplicate 3 is dropped

movies = {"Avengers", "Iron Man", "Hitman"}
```

> **⚠️ Heads up**
>
> Empty curly braces `{}` make an empty **dictionary**, not a set. Always use `set()` for an empty set.

### No indexing

```python
movies[0]           # TypeError: 'set' object is not subscriptable
```

Since a set has no order, there's no position 0. To see items, loop through it or check if something is inside:

```python
for m in movies:
    print(m)

"Avengers" in movies    # True
```

### Adding items

```python
movies.add("Hulk")
```

### Set math: difference and intersection

> **🧒 Simple version (like you're 5)**
>
> You and a friend each have a box of stickers. **Intersection** means the stickers you both have. **Difference** means the stickers only you have, after taking out the ones your friend also has.

```python
set1 = {"Avengers", "Iron Man", "Hitman"}
set2 = {"Avengers", "Iron Man", "Hitman", "Hulk"}

set2.difference(set1)      # {'Hulk'}   items in set2 that are NOT in set1
set2.intersection(set1)    # {'Avengers', 'Iron Man', 'Hitman'}   items in BOTH
```

> **🔧 Technical version**
>
> `difference()` and `intersection()` **return a new set**. The original stays the same. To change the original set, use the `_update` versions:

```python
set2.difference_update(set1)     # set2 is now {'Hulk'}
set2.intersection_update(set1)   # set2 keeps only the common items
```

Other set methods you'll see: `union()` (everything from both), `discard()` (remove an item), `copy()`. Press **Tab** after `movies.` in Jupyter to see them all.

## Dictionaries

> **🧒 Simple version (like you're 5)**
>
> A dictionary is like a row of lockers. Each locker has a name tag on the door (the **key**), and something stored inside (the **value**). To get your stuff, you don't count lockers. You just look for your name tag.

> **🔧 Technical version**
>
> A dictionary stores **key: value pairs**. It is mutable. Keys must be unique, and you look up values by key, not by position. Data from APIs and from databases like MongoDB usually comes as JSON, which maps directly to Python dictionaries.

```python
empty_dict = {}          # or dict()
type(empty_dict)         # <class 'dict'>

my_dict = {"car1": "Audi", "car2": "BMW", "car3": "Mercedes Benz"}
```

Notice the difference: `{"a", "b"}` is a set, but `{"a": 1, "b": 2}` is a dictionary. The colon `:` makes it a dictionary.

### Getting values by key

```python
my_dict["car1"]          # 'Audi'
my_dict["car9"]          # KeyError: the key doesn't exist
```

**Extra tip (not in the video):** `my_dict.get("car9")` returns `None` instead of crashing when a key is missing.

### Looping through a dictionary

```python
for x in my_dict:               # loops through KEYS by default
    print(x)                    # car1, car2, car3

for x in my_dict.values():      # loops through VALUES
    print(x)                    # Audi, BMW, Mercedes Benz

for k, v in my_dict.items():    # loops through BOTH
    print(k, v)                 # car1 Audi, car2 BMW, ...
```

### Adding and changing values

```python
my_dict["car4"] = "Audi 2.0"    # new key, so it gets ADDED
my_dict["car1"] = "Maruti"      # key already exists, so the value gets REPLACED
```

> **🧒 Simple version (like you're 5)**
>
> If you put something in a locker that already has your name on it, the old thing gets thrown out and the new thing goes in. You can't have two lockers with the same name tag.

### Nested dictionaries

> **🧒 Simple version (like you're 5)**
>
> A nested dictionary is a locker with a smaller box inside, and the box has its own name tags. To reach something, you open the locker first, then open the box.

```python
car1_model = {"Mercedes": 1960}
car2_model = {"Audi": 1970}
car3_model = {"Ambassador": 1980}

car_type = {"car1": car1_model, "car2": car2_model, "car3": car3_model}

car_type["car1"]               # {'Mercedes': 1960}   first key opens the outer dict
car_type["car1"]["Mercedes"]   # 1960                 second key opens the inner dict
```

> **🔧 Technical version**
>
> Each `[key]` goes one level deeper. However deep the nesting goes, you just chain more keys. This is exactly how you'll read nested JSON data later.

> **⚠️ Heads up**
>
> He says dictionaries are "unordered." That was true in old Python. Since Python 3.7, dictionaries **keep the order you added items in**. You still look items up by key, not by position.

## Tuples

> **🧒 Simple version (like you're 5)**
>
> A tuple is like a list written in permanent marker. Once you write it, you can read it, but you can't erase or change any item. If you want something different, you have to throw it away and write a whole new one.

> **🔧 Technical version**
>
> A tuple is an **ordered, immutable** collection written with round brackets `()`. You can index it like a list, but you can't change, add, or remove items. You *can* point the variable to a brand new tuple. Tuples are used for data that should stay fixed, like coordinates or a row of settings.

```python
empty_tuple = ()          # or tuple()

my_tuple = ("Krish", "Ankur", "John")
my_tuple[0]               # 'Krish'

my_tuple[0] = "Mike"      # TypeError: 'tuple' object does not support item assignment

my_tuple = ("Hello", "World")   # this works: a whole NEW tuple replaces the old one
```

### Tuple methods

Tuples have only two methods:

```python
names = ("Krish", "John", "Krish")
names.count("Krish")      # 2   how many times it appears
names.index("John")       # 1   position of the first match
```

**Extra tip (not in the video):** a tuple with one item needs a comma: `("Krish",)`. Without the comma, `("Krish")` is just a string.

## Small tips he mentioned

- **First question for any new data structure:** "How do I get data out of it?" Learn its indexing or lookup first. Everything else you can Google.
- **Set methods to explore yourself:** `copy()`, `discard()`, `union()`, `difference_update()`, `intersection_update()`. Press **Tab** after a set name to see them.
- **Dictionaries and MongoDB:** MongoDB stores data in key value form. When you load JSON from it, you work with it as dictionaries. That's why dictionaries matter in data work.
- **When to use tuples:** when the data is defined once and shouldn't change.

## Self-check

1. What does `{5, 5, 6, 7, 7}` become, and why?
2. Why does `movies[0]` give an error for a set?
3. What's the difference between `set2.intersection(set1)` and `set2.intersection_update(set1)`?
4. Is `{}` an empty set or an empty dictionary?
5. If `d = {"a": 1, "b": 2}`, what does `d["b"] = 5` do? What about `d["c"] = 9`?
6. Given `data = {"student": {"name": "Dev", "year": 2027}}`, how do you get `2027`?
7. Can you change `t[0]` if `t = (1, 2, 3)`? Why or why not?

<details>
<summary>Show answers</summary>

1. `{5, 6, 7}`. Sets don't allow duplicates, so the extra 5 and 7 are dropped.
2. Sets are unordered, so there's no position 0. They don't support indexing.
3. `intersection()` returns a new set and leaves `set2` unchanged. `intersection_update()` changes `set2` itself to keep only the common items.
4. An empty dictionary. Use `set()` for an empty set.
5. `d["b"] = 5` replaces the old value 2 with 5, because key `"b"` exists. `d["c"] = 9` adds a new pair, because `"c"` is a new key.
6. `data["student"]["year"]`
7. No. Tuples are immutable, so you get a `TypeError`. You can only replace the whole tuple with a new one.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
# Video 5: Python Sets, Dictionaries and Tuples

**Tracker:** Python sheet, #5  |  **Length:** about 16 minutes  |  **Type:** coding

He says these data structures matter a lot in exploratory data analysis. You don't need to memorize every built in function. Know how each one works, especially **how to get data out of it**, and look up the rest when you need it.

## Quick comparison

| | List | Set | Dictionary | Tuple |
| --- | --- | --- | --- | --- |
| Brackets | `[ ]` | `{ }` | `{key: value}` | `( )` |
| Ordered? | Yes | No | Yes (keeps insertion order) | Yes |
| Can change it? | Yes | Yes | Yes | **No** |
| Duplicates allowed? | Yes | **No** | Keys: no. Values: yes | Yes |
| How you get items | By position `[0]` | No indexing | By key `["car1"]` | By position `[0]` |

## Sets

> **🧒 Simple version (like you're 5)**
>
> A set is like a bag of marbles where every marble must be a different color. If you try to add a second red marble, the bag just says "I already have red" and ignores it. The marbles are all mixed up inside, so there's no "first" or "second" marble.

> **🔧 Technical version**
>
> A set is an **unordered, mutable** collection with **no duplicate elements**. It is iterable, so you can loop through it. It follows the math idea of a set and is built on a **hash table**, which makes checking "is this item in the set?" very fast.

```python
empty_set = set()              # the way to make an empty set
type(empty_set)                # <class 'set'>

nums = {1, 2, 3, 4, 3}
nums                           # {1, 2, 3, 4}   the duplicate 3 is dropped

movies = {"Avengers", "Iron Man", "Hitman"}
```

> **⚠️ Heads up**
>
> Empty curly braces `{}` make an empty **dictionary**, not a set. Always use `set()` for an empty set.

### No indexing

```python
movies[0]           # TypeError: 'set' object is not subscriptable
```

Since a set has no order, there's no position 0. To see items, loop through it or check if something is inside:

```python
for m in movies:
    print(m)

"Avengers" in movies    # True
```

### Adding items

```python
movies.add("Hulk")
```

### Set math: difference and intersection

> **🧒 Simple version (like you're 5)**
>
> You and a friend each have a box of stickers. **Intersection** means the stickers you both have. **Difference** means the stickers only you have, after taking out the ones your friend also has.

```python
set1 = {"Avengers", "Iron Man", "Hitman"}
set2 = {"Avengers", "Iron Man", "Hitman", "Hulk"}

set2.difference(set1)      # {'Hulk'}   items in set2 that are NOT in set1
set2.intersection(set1)    # {'Avengers', 'Iron Man', 'Hitman'}   items in BOTH
```

> **🔧 Technical version**
>
> `difference()` and `intersection()` **return a new set**. The original stays the same. To change the original set, use the `_update` versions:

```python
set2.difference_update(set1)     # set2 is now {'Hulk'}
set2.intersection_update(set1)   # set2 keeps only the common items
```

Other set methods you'll see: `union()` (everything from both), `discard()` (remove an item), `copy()`. Press **Tab** after `movies.` in Jupyter to see them all.

## Dictionaries

> **🧒 Simple version (like you're 5)**
>
> A dictionary is like a row of lockers. Each locker has a name tag on the door (the **key**), and something stored inside (the **value**). To get your stuff, you don't count lockers. You just look for your name tag.

> **🔧 Technical version**
>
> A dictionary stores **key: value pairs**. It is mutable. Keys must be unique, and you look up values by key, not by position. Data from APIs and from databases like MongoDB usually comes as JSON, which maps directly to Python dictionaries.

```python
empty_dict = {}          # or dict()
type(empty_dict)         # <class 'dict'>

my_dict = {"car1": "Audi", "car2": "BMW", "car3": "Mercedes Benz"}
```

Notice the difference: `{"a", "b"}` is a set, but `{"a": 1, "b": 2}` is a dictionary. The colon `:` makes it a dictionary.

### Getting values by key

```python
my_dict["car1"]          # 'Audi'
my_dict["car9"]          # KeyError: the key doesn't exist
```

**Extra tip (not in the video):** `my_dict.get("car9")` returns `None` instead of crashing when a key is missing.

### Looping through a dictionary

```python
for x in my_dict:               # loops through KEYS by default
    print(x)                    # car1, car2, car3

for x in my_dict.values():      # loops through VALUES
    print(x)                    # Audi, BMW, Mercedes Benz

for k, v in my_dict.items():    # loops through BOTH
    print(k, v)                 # car1 Audi, car2 BMW, ...
```

### Adding and changing values

```python
my_dict["car4"] = "Audi 2.0"    # new key, so it gets ADDED
my_dict["car1"] = "Maruti"      # key already exists, so the value gets REPLACED
```

> **🧒 Simple version (like you're 5)**
>
> If you put something in a locker that already has your name on it, the old thing gets thrown out and the new thing goes in. You can't have two lockers with the same name tag.

### Nested dictionaries

> **🧒 Simple version (like you're 5)**
>
> A nested dictionary is a locker with a smaller box inside, and the box has its own name tags. To reach something, you open the locker first, then open the box.

```python
car1_model = {"Mercedes": 1960}
car2_model = {"Audi": 1970}
car3_model = {"Ambassador": 1980}

car_type = {"car1": car1_model, "car2": car2_model, "car3": car3_model}

car_type["car1"]               # {'Mercedes': 1960}   first key opens the outer dict
car_type["car1"]["Mercedes"]   # 1960                 second key opens the inner dict
```

> **🔧 Technical version**
>
> Each `[key]` goes one level deeper. However deep the nesting goes, you just chain more keys. This is exactly how you'll read nested JSON data later.

> **⚠️ Heads up**
>
> He says dictionaries are "unordered." That was true in old Python. Since Python 3.7, dictionaries **keep the order you added items in**. You still look items up by key, not by position.

## Tuples

> **🧒 Simple version (like you're 5)**
>
> A tuple is like a list written in permanent marker. Once you write it, you can read it, but you can't erase or change any item. If you want something different, you have to throw it away and write a whole new one.

> **🔧 Technical version**
>
> A tuple is an **ordered, immutable** collection written with round brackets `()`. You can index it like a list, but you can't change, add, or remove items. You *can* point the variable to a brand new tuple. Tuples are used for data that should stay fixed, like coordinates or a row of settings.

```python
empty_tuple = ()          # or tuple()

my_tuple = ("Krish", "Ankur", "John")
my_tuple[0]               # 'Krish'

my_tuple[0] = "Mike"      # TypeError: 'tuple' object does not support item assignment

my_tuple = ("Hello", "World")   # this works: a whole NEW tuple replaces the old one
```

### Tuple methods

Tuples have only two methods:

```python
names = ("Krish", "John", "Krish")
names.count("Krish")      # 2   how many times it appears
names.index("John")       # 1   position of the first match
```

**Extra tip (not in the video):** a tuple with one item needs a comma: `("Krish",)`. Without the comma, `("Krish")` is just a string.

## Self-check

1. What does `{5, 5, 6, 7, 7}` become, and why?
2. Why does `movies[0]` give an error for a set?
3. What's the difference between `set2.intersection(set1)` and `set2.intersection_update(set1)`?
4. Is `{}` an empty set or an empty dictionary?
5. If `d = {"a": 1, "b": 2}`, what does `d["b"] = 5` do? What about `d["c"] = 9`?
6. Given `data = {"student": {"name": "Dev", "year": 2027}}`, how do you get `2027`?
7. Can you change `t[0]` if `t = (1, 2, 3)`? Why or why not?

<details>
<summary>Show answers</summary>

1. `{5, 6, 7}`. Sets don't allow duplicates, so the extra 5 and 7 are dropped.
2. Sets are unordered, so there's no position 0. They don't support indexing.
3. `intersection()` returns a new set and leaves `set2` unchanged. `intersection_update()` changes `set2` itself to keep only the common items.
4. An empty dictionary. Use `set()` for an empty set.
5. `d["b"] = 5` replaces the old value 2 with 5, because key `"b"` exists. `d["c"] = 9` adds a new pair, because `"c"` is a new key.
6. `data["student"]["year"]`
7. No. Tuples are immutable, so you get a `TypeError`. You can only replace the whole tuple with a new one.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
