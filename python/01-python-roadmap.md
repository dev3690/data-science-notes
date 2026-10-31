# Video 1: Complete Roadmap to Be Expert in Python

**Tracker:** Python sheet, #1  |  **Length:** about 29 minutes  |  **Type:** advice and planning, no coding

## The big idea: learn for your goal

> **🧒 Simple version (like you're 5)**
>
> Python is like a giant toolbox. A carpenter, a painter, and a plumber all use a toolbox, but they don't use the same tools. You only need the tools for the job you want to do. My job is data science, so I learn the data science tools.

> **🔧 Technical version**
>
> Python is a general purpose, open source language with separate ecosystems for different work:
>
> **Web development:** Flask, Django
>
> **Desktop apps:** Tkinter, PyQt, Kivy
>
> **Data science and ML:** NumPy, Pandas, Matplotlib, Seaborn, SciPy, scikit-learn, TensorFlow, PyTorch, Keras
>
> Everyone needs the same core language first. After that, the path splits by career goal.

## His 4 rules before you start

1. **Know your end goal.** It decides what you learn and what you skip.
2. **Set a time frame.** For example: finish Python basics in 2 months.
3. **Learn every day.** Even 1 to 2 hours. Write your plan down.
4. **Google is your friend.** Looking things up is normal, even for experts. What matters is understanding enough to know what to search for.

## The learning path

| Part | What to learn | Simple picture |
| --- | --- | --- |
| 1. Basic syntax | Math operations, variables, if/else, for and while loops, user input, data types, type casting, indentation | Learning the alphabet and simple words |
| 2. Data structures | Strings, lists, booleans, sets, dictionaries, tuples, functions, iterators, generators, exception handling, imports | Learning different kinds of boxes to keep things in |
| 3. OOP | Classes, objects, methods, inheritance, polymorphism, abstraction, encapsulation | Making your own blueprints and building things from them |
| 4. Libraries | NumPy, Pandas, Matplotlib, Seaborn, SciPy | Getting power tools instead of hand tools |
| 5. Specialize | Data science: ML libraries plus Flask to make APIs | Choosing your job and getting really good at it |

After Part 4, he says you are an **intermediate** Python developer.

## Indentation

> **🧒 Simple version (like you're 5)**
>
> Indentation is the empty space at the start of a line. In Python, it shows which lines belong together, like how stepping inside a room shows you are part of that room.

> **🔧 Technical version**
>
> Python uses indentation (usually 4 spaces) to define code blocks, instead of curly braces `{}` like C or Java. Wrong indentation causes an `IndentationError`, or makes code run in a way you did not intend.

```python
age = 20
if age >= 18:
    print("Adult")      # indented = inside the if
print("Done")            # not indented = outside the if
```

## Why OOP matters in data science

> **🧒 Simple version (like you're 5)**
>
> Imagine a recipe card for making a cake. Once you write it, anyone can follow it and get the same cake every time. A class is like that recipe card for your code.

> **🔧 Technical version**
>
> Real data science work is not only building one model. You build **pipelines**: loading data, cleaning it, feature engineering, feature selection, training, and saving the model. Writing these as classes makes the whole flow reusable and lets it run end to end with one call.

## What is an API?

> **🧒 Simple version (like you're 5)**
>
> An API is like a waiter in a restaurant. You tell the waiter what you want. The waiter takes it to the kitchen and brings back your food. You never go into the kitchen yourself.

> **🔧 Technical version**
>
> An API (Application Programming Interface) lets other programs talk to your code. For data science, you wrap a trained model in an API (often with **Flask**). Another app sends data in a web request, and the API sends back a prediction. He says data scientists need to know how to make APIs, but don't need much front end web design.

## Mindset tips

- Don't be hard on yourself. Everyone learns at a different speed.
- Don't compare yourself to others.
- Focus on learning, not only on the outcome.
- Keep learning all the time. Tech keeps changing.
- Use Google (and practice) whenever you are stuck.

## Heads up

> **⚠️ Heads up**
>
> His day estimates (2 to 4 days per part) only cover a quick overview. Taking a week or more per part, with practice, is completely fine.
>
> He mentions deploying on Heroku. Heroku's free plan no longer exists, so that part is outdated.

## Self-check

1. Why don't you need to learn all of Python?
2. At which part does the path split by career?
3. Why is OOP useful for data science jobs?
4. In your own words, what does an API do?

<details>
<summary>Show answers</summary>

1. Python is huge. You only need the parts that match your goal, which for data science means the core language, then data libraries and ML tools.
2. After Part 4 (libraries), at Part 5, where you specialize in data science, web development, or desktop apps.
3. Real data science work uses pipelines (cleaning, features, training). Writing them as classes makes them reusable and lets them run end to end.
4. It lets other programs send a request to your code and get a result back, like a waiter between you and the kitchen. For example, an app sends data and gets a prediction from your model.

</details>

## My own notes

*Write what you learned in your own words, questions you still have, and anything you tried in Jupyter.*

-
