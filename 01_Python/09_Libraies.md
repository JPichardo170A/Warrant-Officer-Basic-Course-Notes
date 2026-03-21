# 📦 Python Libraries

*Module 01 — Python | Day 4*

---

## 🎯 Learning Objectives

- Import standard libraries with the `import` keyword
- Use the `math` library for mathematical operations
- Use the `random` library for pseudo-random selections
- Import specific functions with `from ... import`
- Use aliases with `import ... as`

---

# Importing Libraries

## The import Keyword

The keyword `import` is useful for literally importing standard Python (and other third-party) libraries (also known as Modules). 

These modules/libraries give access to a multitude of other tools/functions/methods that can be useful to a program but aren't necessary for basic Python execution.

More information about `import` can be found at:

[GeeksforGeeks](https://www.geeksforgeeks.org/import-module-python/)

[W3Schools](https://www.w3schools.com/python/python_modules.asp)

[Python Docs](https://docs.python.org/3/reference/simple_stmts.html#import)


## Basic Libraries

We will only scratch the surface of Python's available libraries. For a more complete list of standard and other third-party libraries you can visit [Python Docs - The Python Standard Library](https://docs.python.org/3/library/index.html)

### Where Python Standard Libraries Live?

When Python is downloaded onto your system a group of standard libraries are included for programmers to use as needed. The following code will show you the directories in which those libraries live.

```python
import sys

print(sys.path)
```

You can explore the `random` library that should be found in the `/usr/lib/python3.8` directory (CVTE Ubunutu may have a more recent version of Python).

### Math Library/Module

The `math` library/Module provides access to multiple functions/methods that house commonly used formulas and values for math operations

Pi is a great example of one of these values

Import the math library and access the value of Pi

```python
import math
print(math.pi)
```

Use the `dir()` built-in function for a full listing of functions available from the `math` library/module

```python
dir(math)
```

Try out the `sqrt` function (square root) of the `math` library

```python
import math

num = math.sqrt(25)
print(num)
```

### Random Library/Module

The `random` library/module is great for making pseudo-random selections from either a range of numbers or collections of items.

Python Docs warns programmers that this module should not be used for security purposes and suggests the use of the [secrets](https://docs.python.org/3/library/secrets.html#module-secrets) library/module instead.

Test out the `random` library on the `list` of names below to return a random name for bathroom cleaning duty!

```python
names = ['Smith', 'Barnes', 'Perry', 'Johnson']

import random

bathroom_duty = random.choice(names)
print(bathroom_duty)
```

Execute this code a few times to see how the name changes

The `random` library is also great at choosing a random number out of a range of numbers you can specify by using the `.randint(start, stop)` function. The start and stop values must be `int` and ARE inclusive.

```python
import random

num = random.randint(5, 10)
print(num)
```

Let's say you want a random number from 2 to 100, but only want even numbers. The `.randrange(start,stop,step)` function works well here. Note that like `range`, the `stop` is exclusive.

```python
import random

num = random.randrange(2, 101, 2)
print(num)
```

If you don't need to import the entire contents of a library/module, python does allow you to import a specific function or constant

Import just the `choice` function from the `random` library/module.

```python
from random import choice

lst = [1,2,3,4,5,6]
x = choice(lst)
print(x)
```

Maybe you don't like the name of the function, python also allows you to alter it upon import.

Import the `randint` function and call it `RANDnum`

```python
from random import randint as RANDnum
y = RANDnum(1,100)
print(y)
```

The `shuffle` function from the `random` module/library takes a `list` and jumbles it up. Note that it modifies the `list` in place. It returns `None`. The below code instantiates a 52-card deck, shuffles it three times, deals five cards each to two players, and displays the cards.

```python
from random import shuffle

# make the deck
suits = ['\u2660\uFE0F', '\u2663\uFE0F', '\u2666\uFE0F', '\u2665\uFE0F'] # spades, clubs, diamonds, hearts
values = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A']
deck = []
for suit in suits:
    for val in values:
        deck.append(f'{val} of {suit}')

# shuffle the deck 3 times
for i in range(3):
    shuffle(deck)

# deal five cards to each player (assume index 0 is the top of the deck)
p1 = []
p2 = []
for i in range(5):
    p1.append(deck.pop(0))
    p2.append(deck.pop(0))

# display the cards
print(p1)
print(p2)
```

There are so many more libraries/modules available that can be useful for so many things. Later, in networking we will revisit this topic!


---

[⬆️ Back to Module Index](../README.md)
