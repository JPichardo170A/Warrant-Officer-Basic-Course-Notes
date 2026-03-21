# 🐍 Personal Python Notes & Quizzes

*Module 01 — Python | Complete Course Reference & Exam Prep*

---

## 🎯 Learning Objectives

- Understand Python fundamentals — syntax, semantics, and grammar
- Work with core data types: `int`, `float`, `bool`, `str`, `list`, `tuple`, `NoneType`
- Use variables, naming conventions, and dynamic typing
- Master list methods, string methods, slicing, and sorting
- Write functions with `*args` and `**kwargs`
- Handle file I/O with `open()`, `read()`, `write()`, and `seek()`
- Build and use dictionaries and sets
- Apply loops (`for`, `while`), conditionals (`if`/`elif`/`else`), and operators
- Import and use Python standard libraries
- Create classes with `__init__`, `__str__`, inheritance, and polymorphism
- Prepare for Python module exams with practice quizzes (Days 1–9)

---

# 📅 Python Day 1

## 🧱 Python Fundamentals

Python is a high-level, interpreted programming language known for its simplicity and readability. It is used in web development, data analysis, artificial intelligence, cybersecurity, and more.

---

### 🧱 Basic Syntax and Semantics

#### Errors

Python's syntax refers to the set of rules and structures that dictate how code is written. It includes conventions for defining variables, writing statements, and organizing code.

> ⚠️ **Warning:** When writing code, errors will arise often. These errors may cause programs to crash, run forever, or provide inaccurate results. They are usually caused by syntax violations or logic mistakes.

#### Semantics

Semantic errors are a type of logic error — more subtle and harder to detect. The code is grammatically correct but doesn't produce the intended results.

```python
def multiply_by_five():
    num + int(input("Enter a number: "))
    answer = num * 5
    print(answer)
```

> ⚠️ **Warning:** This code has a semantic error — `num + int(...)` should be `num = int(...)`. The assignment operator `=` is missing, so `num` is never stored.

#### Case Sensitivity

Python is case-sensitive — uppercase and lowercase characters are treated differently.

```python
the_Person = "Him"
the_person = "Her"

print("the_Person: ", the_Person)
print("the_person: ", the_person)
```

> ✅ **Expected Result:**
> ```
> the_Person:  Him
> the_person:  Her
> ```

---

### 🧱 Python Grammar

**Whitespace** — In Python, whitespace (spaces, tabs, newlines) is used for formatting and structuring code. Unlike other languages, Python uses whitespace for indentation and block delineation.

- **Indentation:** Defines blocks of code (loops, conditionals, functions, classes)
- **Spaces in expressions:** Separate elements in a block
- **Blank lines:** Improve readability

> 🧠 **Tip:** Use spaces (not tabs) for indentation. This is the preferred Python convention and avoids mixing issues.

**Comments** — Used to explain code; ignored by the interpreter. Use `#` for single-line comments and triple quotes for multi-line documentation.

```python
# This is a single-line comment

"""
This is a multi-line
docstring or comment block
"""
```

**Statements** — A sequence of instructions that perform specific actions. In Python, the statement terminator is the end of a line (newline character), not a semicolon.

---

### 🧱 Python Execution Modes

| Mode | Description |
|------|-------------|
| **REPL (Interactive)** | Read-Evaluate-Print-Loop — type commands, see results immediately |
| **Batch (Script)** | Write code in a `.py` file, execute the entire file at once |
| **IDE** | Integrated Development Environment — edit, organize, and debug code in one tool |

**REPL** — The Python interpreter reads what the user types, evaluates it, prints the result, and loops back for more input.

**Batch** — Create a `.py` file with all instructions, then execute it. Many scripts include a shebang line:

```python
#!/usr/bin/env python3
```

> 🧠 **Tip:** The shebang (`#!`) tells Linux which interpreter to use when running the script directly.

**IDE** — Software like VS Code, PyCharm, or Jupyter that provides code editing, syntax highlighting, auto-completion, debugging, and more.

---

## 🧱 Python Data Types

### Print Function Introduction

The `print()` function outputs data to the console. Use it to test code and verify logic.

```python
print("Hello, World!")
print(42)
print(3.14)
```

---

### Data Types Overview

| Type | Description | Example |
|------|-------------|---------|
| `int` | Whole numbers (unbounded) | `5`, `-1`, `1000` |
| `float` | Decimal numbers | `3.14`, `-0.5` |
| `bool` | Boolean values | `True`, `False` |
| `str` | Character sequences (immutable) | `"hello"`, `'world'` |
| `list` | Ordered, mutable collection | `[1, 2, 3]` |
| `tuple` | Ordered, immutable collection | `(1, 2, 3)` |
| `NoneType` | Represents "nothing" | `None` |

---

#### Integers — A Numeric Data Type

Integers are whole numbers with no decimal value. Python 3 does not limit the maximum value of an integer — it is unbounded.

```python
5
4
-1
type(5)
```

> ✅ **Expected Result:** `<class 'int'>`

---

#### Floating Point — Another Numeric Data Type

Numbers with a decimal are type `float`. Precision depends on system architecture.

| Operation | Result |
|-----------|--------|
| `x + y` | Sum |
| `x - y` | Difference |
| `x * y` | Product |
| `x / y` | Quotient |
| `x // y` | Floor division |
| `x % y` | Modulus (remainder) |
| `x ** y` | Exponentiation |

---

#### Boolean

The `bool` type holds only `True` (1) or `False` (0).

```python
bool(1)    # True
bool(0)    # False
```

> 🧠 **Tip:** Any non-zero value evaluates to `True`. Only `0`, `None`, empty strings, and empty collections evaluate to `False`.

---

#### Strings

Strings are immutable sequences of characters, enclosed in single or double quotes.

```python
'hello'
"world"
```

**Escape Characters:**

| Sequence | Meaning |
|----------|---------|
| `\\` | Backslash |
| `\'` | Single quote |
| `\"` | Double quote |
| `\n` | Newline |
| `\t` | Horizontal tab |
| `\r` | Carriage return |

**Triple-Quoted Strings** — Span multiple lines and preserve whitespace:

```python
'''the benefit is that
you can make a
multi-lined string'''
```

> ✅ **Expected Result:** `'the benefit is that\nyou can make a \nmulti-lined string'`

---

#### Lists

An ordered, mutable collection of zero or more elements. Similar to arrays in other languages.

```python
[]        # empty list
list()    # also an empty list
[1, 2, 3, "mixed", True]
```

> 🧠 **Tip:** Lists support efficient element access using integer indices and slice notation.

---

#### Tuples

Similar to lists but **immutable** — cannot be changed once created.

```python
()          # empty tuple
tuple()     # also an empty tuple
(1, 2, 3)
('one', 'two', 'three')
```

---

#### NoneType

`None` represents "nothing" — similar to `null` in other languages. Evaluates to `False` in conditionals.

```python
None
type(None)   # NoneType
```

---

#### Why Knowing Your Type Is Important

Python is strongly typed — some types work together, others produce errors.

```python
1 + 2.5           # 3.5 (int + float works)
# 1 + 'hello'     # TypeError: unsupported operand type(s)
'hello ' * 3      # 'hello hello hello ' (str * int works)
```

> ⚠️ **Warning:** You cannot add `str` and `int` directly. Use `str()` or `int()` to convert first.

---

### 🧱 Python Keywords

Keywords are reserved words that cannot be used as variable or function names.

```python
help('keywords')
```

| | | | | |
|---|---|---|---|---|
| `False` | `class` | `finally` | `is` | `return` |
| `None` | `continue` | `for` | `lambda` | `try` |
| `True` | `def` | `from` | `nonlocal` | `while` |
| `and` | `del` | `global` | `not` | `with` |
| `as` | `elif` | `if` | `or` | `yield` |
| `assert` | `else` | `import` | `pass` | `break` |
| `except` | `in` | `raise` | | |

---

### 🧱 Dealing with Variables

#### Naming Conventions

- Must start with a letter or underscore (`_`)
- Can contain letters, digits, and underscores
- Variable/function names → lowercase (`my_variable`)
- Class names → CamelCase (`MyClass`)
- Cannot use Python keywords

#### Dynamic Variable Declaration

Python uses dynamic typing — a variable is simply a value bound to a name. Multiple variables can be assigned at once:

```python
s, x, y = 'hello', 10, 5.0
tab = " \t"

print(s, tab, type(s), tab, id(s))
print(x, tab, type(x), tab, id(x))
print(y, tab, type(y), tab, id(y))
```

> 🧠 **Tip:** Python uses pass-by-object-reference. The variable itself has no type — the value it points to does.

---

### 🔧 Data Conversion Functions

| Function | Converts To |
|----------|------------|
| `int()` | Integer |
| `str()` | String |
| `float()` | Float |
| `list()` | List |
| `tuple()` | Tuple |
| `bool()` | Boolean |
| `chr()` | Character (from int) |
| `ord()` | Integer (from char) |
| `oct()` | Octal string |
| `hex()` | Hexadecimal string |

---

### 🧱 Print and Input Functions

The `print()` function supports multiple objects and formatting:

```python
x = 1
y = 'two'
print(x, y)                                    # 1 two
print('this', 'that', x, y)                    # this that 1 two
print(f'formatted: {x}, {y}')                  # formatted: 1, two
```

**Parameters:** `print(*objects, sep=' ', end='\n')`

The `input()` function reads user input as a **string**:

```python
num = int(input("Enter a number: "))
remainder = num % 16
print(remainder)
```

> ⚠️ **Warning:** `input()` always returns a `str`. Use `int()` or `float()` to convert for math operations.

---

## 🔍 Help in Python

Use Python's built-in help system to explore documentation:

```python
help('keywords')      # List all keywords
help(print)           # Help on print function
dir(str)              # List all string methods
```

> 🧠 **Tip:** Run `python3 --version` to check your Python version, then reference the matching documentation.

---

💡 **Key Takeaway:** Day 1 covers the foundation — syntax rules, data types, variables, and how Python executes code. Everything in Python is an object with a type, and knowing that type determines what operations you can perform.

---

# 📅 Python Day 2

## 🧱 List Methods

Access individual characters within nested structures using chained indexing:

```python
word_lst = ['cyber', 'is', 'so', 'much', 'fun']
print(word_lst[2][1])
```

> ✅ **Expected Result:** `o` (the letter 'o' from the word 'so')

Access the last item in any iterable using `[-1]`:

```python
lst = [5, 6, 7, 8]
print(lst[-1])
```

> ✅ **Expected Result:** `8`

### Adding Items to a List

```python
# Append — adds a single item to the end
lst = [1, 2, 3, [4, 5]]
lst.append("four")
print(lst)

# Concatenation — combine two lists
lst = [1, 2, 3]
new_lst = [4, 5, 6]
lst = lst + new_lst
print(lst)

# Insert — add at a specific index
lst = [1, 2, 3]
lst.insert(0, 'zero')
print(lst)
```

> ✅ **Expected Result:** `['zero', 1, 2, 3]`

---

## 🧱 Removing Items

Three ways to remove items from a list:

```python
# remove() — removes FIRST occurrence of a value
lst = [1, 2, 3, 1, 2, 3]
lst.remove(1)
print(lst)          # [2, 3, 1, 2, 3]

# del — deletes by index
lst = [1, 2, 3]
del lst[0]
print(lst)          # [2, 3]

# pop() — removes by index and returns the value
lst = [1, 2, 3]
lst.pop(0)
print(lst)          # [2, 3]
```

> ⚠️ **Warning:** `remove()` only removes the **first** instance of the value, not all occurrences.

---

## 🧱 Counting Items

```python
lst = [1, 2, 3, 4, 5, 1, 2, 3]
one_count = lst.count(1)
print(one_count)
```

> ✅ **Expected Result:** `2`

---

## 🧱 Tuple Methods

Tuples support `count()` and `index()` methods:

```python
tup = (9, 8, 7, 9, 8, 7)
nine_count = tup.count(9)
print(nine_count)        # 2

tup = (1, 2, 3)
where_is_2 = tup.index(2)
print(where_is_2)        # 1
```

**Workaround for modifying tuples** — convert to list, modify, convert back:

```python
soldier_159 = ('Joe', 'Smith', '88M', 'Ft. Drum, NY')
soldier_159 = list(soldier_159)
soldier_159[-1] = 'Ft. Eisenhower, GA'
soldier_159 = tuple(soldier_159)
print(soldier_159)
```

> ✅ **Expected Result:** `('Joe', 'Smith', '88M', 'Ft. Eisenhower, GA')`

> 🧠 **Tip:** Convert tuple → list to modify, then back to tuple to "lock down" the data.

---

## 🧱 String Methods — Part 1

| Method | Description |
|--------|-------------|
| `upper()` | All characters to uppercase |
| `lower()` | All characters to lowercase |
| `casefold()` | Aggressive lowercase (handles unicode) |
| `title()` | First letter of each word capitalized |
| `capitalize()` | First letter of string capitalized |

```python
string = "python is fun"
print("upper:", string.upper())           # PYTHON IS FUN
print("lower:", string.lower())           # python is fun
print("casefold:", string.casefold())     # python is fun
print("title:", string.title())           # Python Is Fun
print("capitalize:", string.capitalize()) # Python is fun
```

---

## 🧱 String Methods Part 2 (Finding Substrings)

| Method | Description | On Not Found |
|--------|-------------|-------------|
| `count(s)` | Number of occurrences | Returns 0 |
| `index(s)` | Index of first occurrence | Raises `ValueError` |
| `find(s)` | Index of first occurrence | Returns `-1` |

```python
string = "python is fun"
print(string.count("n"))     # 2
print(string.index("n"))     # 5
print(string.find("n"))      # 5
print(string.find('z'))      # -1
```

> 🧠 **Tip:** All these methods perform **case-sensitive** searches.

---

## 🧱 String Methods Part 3 (Modified Copies)

| Method | Description |
|--------|-------------|
| `strip()` | Remove leading and trailing whitespace |
| `lstrip()` | Remove leading whitespace |
| `rstrip()` | Remove trailing whitespace |
| `replace(old, new)` | Replace all instances |

```python
s = "\t 123-456-7890 \t"
stripped = s.strip()
print(stripped)                       # 123-456-7890
print(stripped.replace("-", " "))     # 123 456 7890
```

### Splitting and Joining Strings

```python
phrase = 'hello world'
split_phrase = phrase.split()
print(split_phrase)                   # ['hello', 'world']

sentence = 'Hello class! Welcome to Python.'
split_sentence = sentence.split('!')
print(split_sentence)                 # ['Hello class', ' Welcome to Python.']
```

> ⚠️ **Warning:** The delimiter passed to `.split()` is **removed** from the result.

### Isolating Parts of a String

```python
full_name = 'Joe Smith'
fname = full_name.split()[0]
lname = full_name.split()[1]
print(fname)    # Joe
print(lname)    # Smith
```

### Changing Characters in a String (via list conversion)

Since strings are immutable, convert to a list to modify individual characters:

```python
strng = 'jello'
str_lst = list(strng)
str_lst[0] = 'h'
result = ''.join(str_lst)
print(result)    # hello
```

---

## 🧱 `is` Methods for Strings

| Method | Returns `True` When |
|--------|---------------------|
| `isdigit()` | All characters are digits |
| `islower()` | All characters are lowercase |
| `isupper()` | All characters are uppercase |
| `isalnum()` | All characters are alphanumeric |

> ⚠️ **Warning:** Whitespace does NOT count as alphanumeric — `"hello world".isalnum()` returns `False`.

---

## 🧱 String Formatting

**f-strings** (recommended — Python 3.6+):

```python
coding_language = "Python"
print(f'{coding_language} is fun')
```

**`str.format()`** (older method):

```python
difficulty = "easy"
output = "Formatting in python is {}".format(difficulty)
print(output)
```

---

## 🧱 Escape Characters

| Sequence | Meaning |
|----------|---------|
| `\\` | Backslash |
| `\'` | Single quote |
| `\"` | Double quote |
| `\n` | Newline / Line feed |
| `\t` | Horizontal tab |
| `\r` | Carriage return |
| `\v` | Vertical tab |
| `\xhh` | ASCII character (hex) |
| `\uxxxx` | Unicode (16-bit hex) |
| `\Uxxxxxxxx` | Unicode (32-bit hex) |

```python
print("Strings are \'easy\' in Python")            # Strings are 'easy' in Python
print(r"Strings are \'easy\' in Python")            # Strings are \'easy\' in Python (raw string)
print('\U0000265F')                                  # ♟
```

---

## 🧱 Function Definitions

Functions are defined with the `def` keyword and called by name:

```python
def function_name(parameter1, parameter2):
    print(parameter1, parameter2)

function_name(parameter2=17, parameter1=12)
function_name(17, 12)
```

---

## 🧱 Functions Examples

```python
# Simple function with no parameters
def multiply():
    return 2 * 4

# Function with parameters
def multiply(num1, num2):
    return num1 * num2

# Function returning a formatted string
def username(first, last):
    return f"{last}.{first}"
```

---

## 🧱 Calling Functions

When a function is called, arguments are the data passed into the method's parameters:

```python
def function_name(parameter1, parameter2):
    print(parameter1, parameter2)

parameter1 = ["This", "is", "a", "argument"]
parameter2 = ("This is another argument")

function_name(parameter1, parameter2)
```

Arguments can be passed by position or by keyword:

```python
def func(num1, num2):
    print(num1, num2)

func(num1=1, num2=2)    # keyword arguments
```

---

## 🧱 Returning Data

Functions return values via the `return` statement:

```python
def func_1(num):
    return num

print(func_1([1, 2, 3]))

def new_func(param1):
    return param1.upper()

return_value = new_func('hello world')
print(return_value.split())
```

> ✅ **Expected Result:** `['HELLO', 'WORLD']`

---

## 🧱 The Four Python Scopes (LEGB)

| Scope | Description |
|-------|-------------|
| **L** — Local | Names created inside a function |
| **E** — Enclosed | Names in a function that encloses another function |
| **G** — Global | Names created in a script outside all functions |
| **B** — Built-in | Names Python reserves for internal use |

```python
# Local scope
def func():
    within_function = "This is locally defined"
    print(within_function)
func()
```

```python
# Enclosed scope
def func_1():
    num = 20
    def func_2():
        print(num)       # accesses enclosed scope
        print(num2)      # accesses global scope
    func_2()
num2 = 50
func_1()
```

```python
# Global scope
global_var = "I am global"

def func_1():
    global_var = "New global"    # creates LOCAL variable, does NOT change global
    print(global_var)

def func_2():
    print(global_var)            # accesses GLOBAL variable

func_1()    # New global
func_2()    # I am global
```

> ⚠️ **Warning:** A function cannot change the value of a global variable without the `global` keyword. Assigning inside a function creates a local variable with the same name.

---

💡 **Key Takeaway:** Day 2 covers the essential data manipulation tools — list/tuple/string methods, functions, and scope rules. Understanding LEGB scope prevents subtle bugs.

---

# 📅 Python Day 3

## 🧮 Relational vs. Logical vs. Membership Operators

### Relational Operators

| Operator | Meaning |
|----------|---------|
| `<` | Strictly less than |
| `<=` | Less than or equal |
| `>` | Strictly greater than |
| `>=` | Greater than or equal |
| `==` | Equal |
| `!=` | Not equal |
| `is` | Object identity |
| `is not` | Negated object identity |

```python
print(5 < 10)       # True
print(5 >= 10)      # False
print(5 == 5)       # True
print(5 != 5)       # False
print(type([1,2,3]) is list)  # True
```

> ⚠️ **Warning:** Use `==` for value comparison. Use `is` only for identity checks (e.g., `is None`). Avoid `is` with literals.

### Logical Operators

| Operator | Type | Result is True When... |
|----------|------|----------------------|
| `not` | Unary | Operand is `False` |
| `and` | Binary | Both operands are `True` |
| `or` | Binary | At least one operand is `True` |

**Truth Tables:**

| X | Y | `X or Y` | `X and Y` |
|---|---|-----------|-----------|
| True | True | True | True |
| True | False | True | False |
| False | True | True | False |
| False | False | False | False |

```python
print(5 < 10 and 5 > 3)     # True
print(5 < 10 or 5 > 20)     # True
print(5 < 10 and 5 > 20)    # False
```

---

## 🧮 Membership Operators

| Operator | Meaning |
|----------|---------|
| `in` | `True` if object is found in sequence |
| `not in` | `True` if object is NOT found in sequence |

```python
lst = [1, 2, 3, 4, 5]
print(5 in lst)          # True
print(5 not in lst)      # False
print(50 not in lst)     # True
```

---

## 🧮 IF, ELSE, ELIF Conditions

### `if` Statement

Code inside an `if` block executes only when the condition is `True`:

```python
number = 25
if number <= 25:
    print("number is smaller or equal to 25")

lst = [1, 2, 3, 4, 5]
if 5 in lst:
    print('5 is found in lst')

if 50 not in lst:
    print('50 not found in lst')
```

### `else` Statement

Executes when no `if` condition is met:

```python
lst = [1, 2, 3, 4, 5]
if 50 in lst:
    print('50 found in lst')
else:
    print('50 was not found')
```

### `elif` Statement

Prevents testing multiple `if` statements when only one can be `True`:

```python
number = 68
if number <= 25:
    print("number is smaller or equal to 25")
elif number == 50:
    print("number is 50")
elif number <= 75:
    print("number is less than or equal to 75")
else:
    print("number is greater than 75")
```

### Evaluating Multiple Conditions

```python
num_1 = 10
num_2 = 0

if num_1 == 10 and num_2 == 0:
    print("num_1 is 10 and num_2 is 0")

if num_1 == 10 or num_2 == 10:
    print("num_1 is 10 or num_2 is 10")
```

---

### ⚠️ Logic Errors with Conditional Blocks

**Broken logic** — order matters! This version has a bug:

```python
grade = int(input("Give me your Python grade: "))
if grade < 70:
    print('You fail.')
elif grade > 70:
    print('Congrats, you pass with a C')    # BUG: grade 85 hits here!
elif grade > 80:
    print('Congrats, you pass with a B')    # Never reached
else:
    print('You get an A')
```

**Fixed logic** — check from highest to lowest:

```python
grade = int(input("Give me your Python grade: "))
if grade >= 90:
    print('You get an A, smarty')
elif grade >= 80:
    print('Congrats, you pass with a B')
elif grade >= 70:
    print('Congrats, you pass with a C')
else:
    print('You fail. Sorry, but Cyber is not for everybody :(')
```

> 🧠 **Tip:** When using `elif` chains, always order conditions from most restrictive to least restrictive.

---

## 🧱 Slicing and More

### Slicing Iterable Objects

**Syntax:** `item[start:stop:step]` — colon-separated, `stop` is **exclusive**.

```python
lst = ['zero', 1, 'two', 3, 'four', 5]
print(lst[0:3])        # ['zero', 1, 'two']

sentence = "This is an example sentence."
print(sentence[5:18])  # 'is an example'
print(sentence[5:])    # 'is an example sentence.'
print(sentence[:18])   # 'This is an example'
print(sentence[:-1])   # 'This is an example sentence' (all but last)
print(sentence[-9:])   # 'sentence.'
```

---

### Length and Sum Functions

`len()` returns the total number of items in an iterable:

```python
lst = [1, 2, 3, 4]
print(len(lst))        # 4

str1 = 'Hello world'
print(len(str1))       # 11
```

Evaluate the length of nested items:

```python
lst2 = [1, 2, 3, ['a', 'b', 'c'], (9, '8', 7)]
tup_len = len(lst2[-1])
print(tup_len)         # 3
```

---

## 🧮 Range Function

**Syntax:** `range(start, stop, step)` — comma-separated, `stop` is **exclusive**.

```python
# Default start=0, step=1
x = range(10)           # range(0, 10)

# Both start and stop
x = range(1, 11)        # range(1, 11)

# Create a list of integers 5 to 100
num_lst = list(range(5, 101))

# Even numbers 0-100
even_nums = list(range(0, 101, 2))

# Odd numbers 1-99
odd_nums = list(range(1, 101, 2))

# Countdown from 50 to 0
countdown = list(range(50, -1, -1))
```

---

## 🧮 Sum and Round Functions

`sum()` takes one iterable and returns the total:

```python
num_lst = [10, 20, 30, 40]
print(sum(num_lst))    # 100
```

`round()` rounds to a specified precision:

```python
pi = 3.141592653589793
print(round(pi))       # 3
print(round(pi, 1))    # 3.1
print(round(pi, 4))    # 3.1416
```

Combine them:

```python
nums = [1.48, 6.58793, 6.254789, 100.25741, 129.4587]
rounded = round(sum(nums), 4)
print(rounded)         # 244.0389
```

---

💡 **Key Takeaway:** Day 3 covers decision-making (conditionals), data access (slicing), and essential built-in functions (`len`, `range`, `sum`, `round`). Always check your `elif` ordering to avoid logic errors.

---

# 📅 Python Day 4

## 🔁 While Loops

The `while` loop executes a block of code as long as the condition is `True`:

```python
counter = 1
while counter <= 5:
    print(counter)
    counter += 1
```

> ✅ **Expected Result:** Prints 1 through 5

Collecting user input with a `while` loop:

```python
user_input = input()
user_list = []
while user_input:
    user_list.append(user_input)
    user_input = input()
```

### Break Statement

`break` exits the loop immediately:

```python
lst = []
while True:
    ui = input()
    if not ui:
        break
    else:
        lst.append(ui)
print(lst)
```

### Continue Statement

`continue` skips the rest of the loop body and goes back to the top:

```python
def playGame():
    while True:
        action = input("Action? ")
        if action == 'help':
            print("N S E W help quit")
            continue
        elif action == 'quit':
            print('Thanks for playing')
            break
        elif action in ['N', 'S', 'E', 'W']:
            print(f'You moved {action}')
        else:
            pass

playGame()
```

> 🧠 **Tip:** Always include an exit condition (`break` or counter update) in `while` loops to prevent infinite loops.

---

## 🔁 For Loops

The `for` loop iterates over items in a sequence:

```python
# Iterate over a string
strng = 'hello world'
for each_letter in strng:
    print(each_letter)

# Iterate over a list
lst = [1, 'two', 3, 'four']
for each_num in lst:
    print(each_num)
```

### Counting with For Loops

```python
str_lst = ['this', 'is', 'a', 'list', 'of', 'words']
total = 0
for word in str_lst:
    total += len(word)
print(total)    # 18
```

### Nested For Loops — Building a Deck of Cards

```python
def makedeck():
    deck = []
    suits = ['\u2660', '\u2665', '\u2666', '\u2663']
    ranks = ['A', 2, 3, 4, 5, 6, 7, 8, 9, 10, 'J', 'Q', 'K']
    for suit in suits:
        for rank in ranks:
            deck.append(f'{rank}{suit}')
    print(deck)

makedeck()
```

### Using `break` in For Loops

```python
names = ['bob', 'joe', 'sally', 'harold']
for each_name in names:
    if each_name == 'sally':
        print('we found sally!')
        break
    else:
        print(f'{each_name} is not sally')
```

---

## 🔁 For Loops — Extended (Tuple Unpacking)

When iterating over a list of tuples, unpack directly:

```python
data = [("California", 39937489, "Sacramento"),
        ("Texas", 29472295, "Austin"),
        ("Florida", 21992985, "Tallahassee")]

for state, population, capital in data:
    print(f'The state of {state} has a population of {population} and its capital is {capital}')
```

---

## 🧮 `range(len())` and `enumerate()` Functions

### Isolating Index Positions with `range(len())`

```python
lst = ['zero', 'one', 'two', 'three']
for index_num in range(len(lst)):
    print(lst[index_num])
```

**Queue position scenario:**

```python
customers = ['Jim', 'Bob', 'Sue', 'Mary', 'Allen']
for position in range(len(customers)):
    print(f'{customers[position]} is in position {position}')
```

### `enumerate()` Function

Assigns numbers to each item — cleaner alternative to `range(len())`:

**Syntax:** `enumerate(iterable, start=0)`

```python
lst = ['zero', 'one', 'two', 'three']
for num in enumerate(lst):
    print(num)
```

> ✅ **Expected Result:**
> ```
> (0, 'zero')
> (1, 'one')
> (2, 'two')
> (3, 'three')
> ```

Change the start value:

```python
for num in enumerate(lst, 1):
    print(num)
# (1, 'zero'), (2, 'one'), etc.
```

---

## 📦 Python Standard Libraries (Importing)

Use the `import` keyword to bring in standard and third-party libraries:

```python
import sys
print(sys.path)    # Shows where Python looks for libraries
```

### Math Library

```python
import math
print(math.pi)            # 3.141592653589793
print(math.sqrt(25))      # 5.0
```

### Random Library

```python
import random

names = ['Smith', 'Barnes', 'Perry', 'Johnson']
print(random.choice(names))       # Random name from list
print(random.randint(5, 10))      # Random int between 5 and 10 (inclusive)
```

**Import specific functions:**

```python
from random import choice
lst = [1, 2, 3, 4, 5, 6]
x = choice(lst)
```

**Import with alias:**

```python
from random import randint as RANDnum
y = RANDnum(1, 100)
```

> ⚠️ **Warning:** The `random` module is NOT suitable for security purposes. Use the `secrets` module instead.

---

💡 **Key Takeaway:** Day 4 covers iteration (`while`, `for`), loop control (`break`, `continue`), and Python's library system. Use `enumerate()` over `range(len())` for cleaner code.

---

# 📅 Python Day 5

## 📁 Python File Input/Output

### File Overview

Three key operations: `open()` → `read()`/`write()` → `close()`

```python
file_obj = open("info.txt", "w")
file_obj.write("Hello World")
file_obj.close()
```

---

### Opening Files

**File Modes:**

| Mode | Description |
|------|-------------|
| `r` | Read (default) |
| `w` | Write (overwrites if file exists) |
| `a` | Append (does not overwrite) |
| `x` | Create (fails if file exists) |
| `b` | Binary mode |
| `t` | Text mode |
| `w+` / `r+` | Read and write |

```python
file_obj = open("info.txt", "r")     # read
file_obj = open("info.txt", "w")     # write
file_obj = open("info.txt", "a")     # append
file_obj = open("info.dat", "rb")    # read binary
```

> ⚠️ **Warning:** Using `w` mode on an existing file **overwrites** all content!

---

### Reading Files

| Method | Returns |
|--------|---------|
| `read()` | Entire file as a single string |
| `readline()` | One line at a time |
| `readlines()` | All lines as a list of strings |

```python
# Using 'with' — automatically closes the file
with open("Test.txt") as file_obj:
    print(file_obj.readline())

# Read all lines into a list
with open("Test.txt") as file_obj:
    file_content = file_obj.readlines()
    print(file_content)

# Read without newline characters
with open("Test.txt") as file_obj:
    file_content = file_obj.read()
    file_lines = file_content.splitlines()

# Split file into words
with open("Test.txt") as file_obj:
    words = file_obj.read().split(" ")
```

> 🧠 **Tip:** Always use the `with` statement — it automatically closes the file, even if an error occurs.

**CSV parsing example:**

```python
def OpenNRead(filepath):
    with open(filepath, "r") as fileobj:
        contents = fileobj.read().replace('"', '').split(",")
    return contents
```

---

### Writing Files

| Method | Description |
|--------|-------------|
| `write()` | Writes a single string |
| `writelines()` | Writes a list of strings (no newlines added) |

```python
data = [("California", 39937489, "Sacramento"),
        ("Texas", 29472295, "Austin"),
        ("Florida", 21992985, "Tallahassee")]

with open("Test.txt", "a") as data_obj:
    for state, population, capital in data:
        data_obj.write(f'The state of {state} has a population of {population} and the capital is {capital}.\n')
```

---

### Closing Files

```python
# Manual close
file_obj = open("info.txt", "w")
file_obj.write("Hello World")
file_obj.close()

# Automatic close with 'with'
with open("info.txt", "a") as file_obj:
    file_obj.write("Hello World")
# File is automatically closed here
```

---

### Seek and Tell

| Function | Description |
|----------|-------------|
| `seek(pos)` | Move the read/write pointer to position `pos` |
| `tell()` | Return the current pointer position |

```python
with open("Test.txt") as file_obj:
    print(file_obj.tell())     # 0 (beginning of file)

file_obj = open("Test.txt")
file_obj.seek(0)               # Reset to beginning
print(file_obj.readline())
file_obj.close()
```

---

💡 **Key Takeaway:** Day 5 covers file I/O — always use `with` for automatic cleanup, remember that `w` overwrites while `a` appends, and use `seek(0)` to reset the file pointer.

---

# 📅 Python Day 6

## 🧱 Dictionaries

A `dict` is an ordered collection of `key:value` pairs. Keys must be unique and hashable. Maintains insertion order (LIFO).

### Creating Dictionaries

```python
# Two ways to create
dictionary = dict()
dictionary2 = {}

# Using {}
names = {"key_1": "Bill", "key_2": "Jill", "key_3": "Gill"}
numbers = {1: 1, 2: 2, 3: 3}

# Using dict()
also_names = dict(key_1="Bill", key_2="Jill", key_3="Gill")
```

> ⚠️ **Warning:** Using `dict()` does NOT allow integer keys — keys become string parameter names.

---

### Dictionary Methods

| Method | Returns |
|--------|---------|
| `.keys()` | View of all keys |
| `.values()` | View of all values |
| `.items()` | View of all `(key, value)` tuples |

```python
states = {'GA': 'Georgia', 'FL': 'Florida', 'CA': 'California', 'AR': 'Arkansas'}

print(states.keys())       # dict_keys(['GA', 'FL', 'CA', 'AR'])
print(states.values())     # dict_values(['Georgia', 'Florida', 'California', 'Arkansas'])
print(states.items())      # dict_items([('GA', 'Georgia'), ('FL', 'Florida'), ...])

# Convert to list
state_keys = list(states.keys())
```

---

### Looping Through a Dictionary

```python
states = {'GA': 'Georgia', 'FL': 'Florida', 'CA': 'California', 'AR': 'Arkansas'}

# Loop over keys (default behavior)
for key in states:
    print(key)

# Loop over values
for value in states.values():
    print(value)

# Loop over key-value pairs
for key, value in states.items():
    print(f'The state of {value} is abbreviated {key}')
```

**Scenario — Sum dictionary values:**

```python
lottery = {'Mega Millions': 11111111111, 'Georgia Lottery': 222222222, 'Power Ball': 3333333}
print(sum(lottery.values()))    # 11336666666
```

---

### Accessing Items in a Dictionary

```python
names = {'key_1': 'Bill', 'key_2': 'Jill', 'key_3': 'Gill'}

# Bracket notation (raises KeyError if not found)
print(names['key_1'])              # Bill

# .get() method (returns None or default if not found)
print(names.get('key_1'))          # Bill
print(names.get('key_10'))         # None
print(names.get('key_10', 'Key does not exist'))  # Key does not exist
```

> 🧠 **Tip:** Use `.get()` to avoid `KeyError` exceptions when a key might not exist.

---

### Finding Keys/Values

```python
numbers = {'one': 1, 'two': 2, 'three': 3}

print("one" in numbers)         # True
print("one" not in numbers)     # False
```

---

### Adding and Updating Key:Value Pairs

```python
names['key_4'] = 'Phil'     # Add new pair
names['key_1'] = 'Hill'     # Update existing value
```

---

### Removing Key:Value Pairs

| Method | Description |
|--------|-------------|
| `del dict[key]` | Remove pair; not returned |
| `del dict` | Delete entire dictionary |
| `.pop(key, default)` | Remove and return value |
| `.popitem()` | Remove and return last pair as tuple |

```python
names = {'key_1': 'Bill', 'key_2': 'Jill', 'key_3': 'Gill', 'key_4': 'Phil', 'key_5': 'Will'}

# pop with default
removed = names.pop("key_1", None)
print(names)

# popitem — removes last item
numbers = {1: 1, 2: 2, 3: 3}
removed = numbers.popitem()
print(numbers)    # {1: 1, 2: 2}
```

> ⚠️ **Warning:** `.popitem()` raises `KeyError` on an empty dictionary.

---

## 🧱 Sets

Sets are **unordered**, **no duplicates**, and all items must be **immutable**.

```python
s = {1, 2, 3, False, "String"}
s_two = set((1, 2, 3, False, "String"))
```

### Adding Items

```python
s = {1, 2, 3}
s.add(10)       # {1, 2, 3, 10}
s.add(10)       # No error, no duplicate — still {1, 2, 3, 10}
```

### Removing Items

```python
s.remove(2)     # Removes 2; raises KeyError if not found
```

### Set Methods

| Method | Description |
|--------|-------------|
| `.union(other)` | All items from both sets |
| `.difference(other)` | Items in first set but NOT in other |
| `.intersection(other)` | Items found in ALL sets |

**Military clearance scenario:**

```python
A_company = {'Nelson', 'Scott', 'Miller', 'King', 'Walker', 'Green', 'Jones', 'Hall', 'Campbell'}
B_company = {'Smith', 'Holly', 'Taylor', 'Martin', 'Jackson', 'Lewis', 'Lee', 'Moore'}
secret_clearance = {'Smith', 'Taylor', 'Lewis', 'Lee', 'Moore', 'Miller', 'Walker', 'Green', 'Jones', 'Hall', 'Campbell'}
ts_clearance = {'Taylor', 'Lee', 'Moore', 'Walker', 'Green', 'Campbell'}

# All soldiers
all_soldiers = A_company.union(B_company)

# B Co without TS clearance
B_TS_uncleared = B_company.difference(ts_clearance)

# A Co with no clearance at all
A_uncleared = A_company.difference(secret_clearance, ts_clearance)

# A Co with ONLY Secret (not TS)
a_secret_only = A_company.intersection(secret_clearance).difference(ts_clearance)
print(a_secret_only)    # {'Miller', 'Hall', 'Jones'}
```

> 🧠 **Tip:** You can chain set methods — `.intersection().difference()` works!

---

## 🧱 Args and Kwargs

### Positional Arguments

Arguments are bound to parameters in order:

```python
def function_name(parameter1, parameter2):
    print(f'argument_1 is assigned to {parameter1}')
    print(f'argument_2 is assigned to {parameter2}')

function_name('this is argument_1', 'this is argument_2')
```

### Default Parameters

Default values are used when an argument isn't provided:

```python
def func_1(para1, para2="default"):
    return (para1, para2)
```

> ⚠️ **Warning:** Default parameters MUST come after non-default parameters, or you get `SyntaxError`.

### Keyword Arguments

Arguments bound by parameter name:

```python
def func_1(para1, para2):
    return (para1, para2)

print(func_1(para1=100, para2="This is a string"))
```

### `**kwargs` — Keyword Arbitrary Arguments

Packs keyword=value pairs into a dictionary:

```python
def func(**dict_arg):
    print("Length:", len(dict_arg))
    print("Arguments:", dict_arg)

func(arg1="String", arg2=[1, 2, 3], arg3=(1, 2, 3))

# Unpack a dictionary into kwargs
kwarg_dict = {'arg1': ['Value 1'], 'arg2': 'Value 2'}
func(**kwarg_dict)
```

### `*args` — Positional Arbitrary Arguments

Packs positional arguments into a tuple:

```python
def func(*arbitrary_args):
    print(arbitrary_args)

func(1, 2, 3, 4)           # (1, 2, 3, 4)

tup = (1, 2, "string")
func(*tup)                  # (1, 2, 'string') — unpacked
func(tup)                   # ((1, 2, 'string'),) — packed as single element
```

### Lambdas

Anonymous functions for simple operations:

```python
# Lambda syntax
add_10 = lambda num: num + 10
print(add_10(50))    # 60

# Equivalent function
def add_10(num):
    return num + 10
```

> ⚠️ **Warning:** Lambdas cannot contain `return`, `pass`, `assert`, or `raise` statements.

---

💡 **Key Takeaway:** Day 6 covers dictionaries (key:value lookup), sets (unique collections with powerful comparison methods), and flexible function signatures with `*args`/`**kwargs`.

---

# 📅 Python Day 7

## 🧮 Sorting Numerically vs. Alphabetically

At a computer's most basic level, sorting uses numerical values for `int`/`float` or ordinal values for `str` characters. By default, Python sorts smallest to largest.

### Two Ways to Sort

| Function | Works On | Behavior |
|----------|----------|----------|
| `sorted(item, key, reverse)` | `str`, `tuple`, `list`, `dict` | Returns a **new** sorted copy |
| `.sort(key, reverse)` | `list` only | Sorts **in place** (permanently) |

---

### Sorting a List

```python
num_lst = [5, 4, 3, 9, 20, 5, 40, 89, 46]
num_lst_sorted = sorted(num_lst)
print(num_lst_sorted)    # [3, 4, 5, 5, 9, 20, 40, 46, 89]
```

### Using the Reverse Parameter

```python
num_lst_lg_sm = sorted(num_lst, reverse=True)
print(num_lst_lg_sm)     # [89, 46, 40, 20, 9, 5, 5, 4, 3]
```

---

### Revisiting `ord()` and `chr()`

```python
x = 'a'
print(ord(x))       # 97

letter = chr(97)
print(letter)        # a
```

---

### Sorting Characters "Alphabetically"

Default sorting uses ordinal values (uppercase before lowercase):

```python
characters = ['z', 'd', 'B', 'A', 'a', 'Z']
print(sorted(characters))                    # ['A', 'B', 'Z', 'a', 'd', 'z']
print(sorted(characters, key=str.lower))     # ['A', 'a', 'B', 'd', 'z', 'Z']
```

> 🧠 **Tip:** Use `key=str.lower` (or `str.upper`) to get true alphabetical sorting regardless of case.

---

### Sorting by Length

```python
words = ['This', 'is', 'a', 'list', 'with', 'words']
short_long = sorted(words, key=len)
print(short_long)    # ['a', 'is', 'This', 'list', 'with', 'words']
```

---

### Sorting a String

```python
strng = 'hello world'
sorted_strng = sorted(strng)
print(sorted_strng)
```

> ⚠️ **Warning:** `sorted()` on a string returns a **list** of characters, not a string.

---

### Custom Key Functions

Build a function to sort by a specific element:

```python
ports_monitored = [('HTTPS', 443), ('SSH', 22), ('FTP-data', 20), ('HTTP', 80)]

def find_port(tup):
    return tup[1]

sorted_by_ports = sorted(ports_monitored, key=find_port)
print(sorted_by_ports)
# [('FTP-data', 20), ('SSH', 22), ('HTTP', 80), ('HTTPS', 443)]
```

---

### Sorting Dictionaries

Convert keys or values to a list first:

```python
numbers = {'one': 1, 'two': 2, 'three': 3}
sorted_keys = sorted(numbers.keys())
print(sorted_keys)    # ['one', 'three', 'two']
```

---

💡 **Key Takeaway:** Day 7 covers sorting — `sorted()` creates a copy while `.sort()` modifies in place. Use the `key` parameter for custom sort logic and `reverse=True` for descending order.

---

# 📅 Python Day 8

## 🧱 Objects and Classes

### Object Review

In Python, every value is an object — an instance of a class:

| Class | Object Example |
|-------|---------------|
| `int` | `7` |
| `float` | `3.14` |
| `str` | `'hello'` |
| `bool` | `True` |
| `list` | `[1, 2, 3, 4]` |
| `tuple` | `(1, 2, 3, 4)` |
| `set` | `{1, 2, 3}` |
| `dict` | `{'a': 1}` |

### `isinstance()` Function

Returns `True` if an object is an instance of a specific type:

```python
x = '0.0'
if isinstance(x, int):
    print(f'{repr(x)} is an instance of an integer.')
else:
    print(f'{repr(x)} is not an instance of an integer.')

if isinstance(x, str):
    print(f'{repr(x)} is an instance of a string.')
```

---

### Object Properties (OOP Fundamentals)

- **Object attributes** — coded as Python names bound to values (data)
- **Object behaviors** — coded as Python methods (functions)

| Class | Methods (not exhaustive) |
|-------|-------------------------|
| `str` | `isdigit`, `upper`, `title` |
| `list` | `append`, `insert`, `sort` |
| `set` | `add`, `intersection`, `difference` |
| `dict` | `update`, `keys`, `items` |

---

## 🧱 Creating Custom Classes

### The `class` Keyword

```python
class Useless:
    pass

a = Useless()
print(type(a))    # <class '__main__.Useless'>
```

### A Class with Attributes and Methods

```python
class Pet:
    petType = 'dog'

    def speak(self):
        print(f'I am a {self.petType}.')
```

> 🧠 **Tip:** Every method must have `self` as its first parameter — it refers to the instance.

```python
a = Pet()
print(a.petType)       # dog
a.speak()              # I am a dog.
a.petType = 'cat'      # Change for this instance only
```

### Adding Arbitrary Attributes

```python
a.name = 'Kitty'       # Only exists on instance 'a'
Pet.name = 'unknown'   # Add to class — all new instances get it
```

---

### Magic Methods (`__init__` and `__str__`)

Magic methods (dunder methods) customize class behavior:

- `__init__` — Constructor: runs when an object is created
- `__str__` — String representation: called by `print()`

```python
class balloon:
    def __init__(self):
        self.altitude = 0

    def __str__(self):
        return f'Current altitude: {self.altitude}'

    def climb(self):
        self.altitude += 1

    def dive(self):
        if self.altitude > 0:
            self.altitude -= 1
        else:
            print('The balloon is at ground level.')

    def crashland(self):
        self.altitude = 0

    def setaltitude(self, newaltitude):
        if newaltitude >= 0:
            self.altitude = newaltitude

    def getaltitude(self):
        return self.altitude
```

```python
b = balloon()
print(b.getaltitude())      # 0
b.setaltitude(10000)
b.climb()
b.climb()
b.climb()
b.dive()
b.climb()
b.climb()
b.climb()
print(b)                    # Current altitude: 10005
b.crashland()
b.dive()                    # The balloon is at ground level.
print(b)                    # Current altitude: 0
```

---

### The `Dog` Class — More Magic Methods

```python
class Dog:
    def __init__(self, aName, level):
        self.dogName = aName
        if level < 0:
            self.goodDogLevel = 0
        elif level > 10:
            self.goodDogLevel = 10
        else:
            self.goodDogLevel = level

    def __del__(self):
        print(f'{self.dogName} says, "Goodbye!"')

    def __str__(self):
        return f'<Dog object named {self.dogName} with level {self.goodDogLevel}>'

    def __eq__(self, aDog):
        return self.goodDogLevel == aDog.goodDogLevel

    def __ne__(self, aDog):
        return self.goodDogLevel != aDog.goodDogLevel

    def __lt__(self, aDog):
        return self.goodDogLevel < aDog.goodDogLevel

    def __le__(self, aDog):
        return self.goodDogLevel <= aDog.goodDogLevel

    def __gt__(self, aDog):
        return self.goodDogLevel > aDog.goodDogLevel

    def __ge__(self, aDog):
        return self.goodDogLevel >= aDog.goodDogLevel

    def setName(self, aName):
        self.dogName = aName

    def setLevel(self, level):
        if level < 0:
            self.goodDogLevel = 0
        elif level > 10:
            self.goodDogLevel = 10
        else:
            self.goodDogLevel = level

    def query(self):
        print(f'The name of this dog is {self.dogName} and its level of goodness is {self.goodDogLevel}.')
```

```python
a = Dog('Lucky', 8)
b = Dog('Bailey', 8)
print(f'Are these dogs equal: {a == b}')      # True
a.setLevel(9)
print(f'Is first dog more good: {a > b}')     # True
del a    # Lucky says, "Goodbye!"
del b    # Bailey says, "Goodbye!"
```

---

### Inheritance

A class can inherit attributes and methods from another class:

```python
class myList(list):
    def cnt(self):
        return len(self)

aList = myList((1, 2))
aList.append(3)          # Inherited from list
print(aList.cnt())       # 3
```

**Shape hierarchy example:**

```python
from math import pi

class Shape:
    area = 0
    def printArea(self):
        shapeName = str(self.__class__.__name__).lower()
        print(f'The area of this {shapeName} shape is {self.area:.2f}.')

    def getArea(self):
        print('This method is a placeholder that should be overrided in a subclass.')

class Rectangle(Shape):
    def __init__(self, w, h):
        self.width = w
        self.height = h
        self.getArea()

    def getArea(self):
        self.area = self.width * self.height

class Square(Rectangle):
    def __init__(self, side):
        self.width = side
        self.height = side
        self.getArea()

class Circle(Shape):
    def __init__(self, r):
        self.radius = r
        self.getArea()

    def getArea(self):
        self.area = pi * self.radius ** 2
```

```python
R = Rectangle(5, 10)
R.printArea()        # The area of this rectangle shape is 50.00.

C = Circle(5)
C.printArea()        # The area of this circle shape is 78.54.

S = Square(5)
S.printArea()        # The area of this square shape is 25.00.
```

---

### Polymorphism

Multiple classes inherit from one parent but modify behavior differently:

```python
class Base:
    def behavior(self):
        print('Base behavior')

class A(Base):
    def behavior(self):
        print('A behavior')

class B(Base):
    def behavior(self):
        print('B behavior')

class C(Base):
    def behavior(self):
        Base.behavior(self)
        print('C behavior')
```

```python
l = [A(), B(), C()]
for i in l:
    i.behavior()
# A behavior
# B behavior
# Base behavior
# C behavior
```

---

### Military Example — Polymorphism & Inheritance

```python
class Soldier:
    def __init__(self, lname, fname, dodid, rank, etsdate):
        self.lname = lname
        self.fname = fname
        self.dodid = dodid
        self.etsdate = etsdate
        self.rank = rank

    def __str__(self):
        return f'{self.__class__.__name__}: {self.rank} {self.fname} {self.lname}'

    def armySong(self):
        print('March along, sing our song, with the Army of the free ...')

    def soldierCreed(self):
        print('I am an American Solider. I am a warrior ...')

    def setRank(self, rank):
        self.rank = rank

    def setEtsDate(self, etsdate):
        self.etsdate = etsdate

class NCO(Soldier):
    def ncoCreed(self):
        print('No one is more professional than I. I am a Non-Commissioned Officer ...')

class Warrant(Soldier):
    def warrantCreed(self):
        print('Willingly render loyal services to superiors, subordinates and peers ...')

class Officer(Soldier):
    def __init__(self, lname, fname, dodid, rank, etsdate, degree):
        self.degree = degree
        super().__init__(lname, fname, dodid, rank, etsdate)

    def admininsterOath(self):
        print('Raise your right hand and repeat after me ...')
```

```python
s = Soldier('Doe', 'James', '1234', 'SPC', '1-1-1')
n = NCO('Doe', 'Jane', '2345', 'SSG', '1-1-1')
w = Warrant('Doe', 'John', '3456', 'CW2', '1-1-1')
o = Officer('Doe', 'Jill', '4567', 'CPT', '1-1-1', 'Bachelors')

print(s)               # Soldier: SPC James Doe
print(n)               # NCO: SSG Jane Doe
n.ncoCreed()           # No one is more professional than I...
print(w)               # Warrant: CW2 John Doe
w.warrantCreed()       # Willingly render loyal services...
o.setRank('MAJ')
print(o)               # Officer: MAJ Jill Doe
o.admininsterOath()    # Raise your right hand...
```

> 🧠 **Tip:** Use `super().__init__()` in child classes to call the parent constructor without repeating code.

---

💡 **Key Takeaway:** Day 8 covers OOP — classes encapsulate data (attributes) and behavior (methods). Use `__init__` for construction, `__str__` for display, inheritance for code reuse, and polymorphism for flexible behavior.

---

# 📝 Python Exam Notes and Examples

## 🧪 Quiz — Day 1

**Question:** Place the acronym of the Python interpreter used in INTERACTIVE mode in the correct order.

**Answer:**
- Step 1: **Read**
- Step 2: **Evaluate**
- Step 3: **Print**
- Step 4: **Loop**

> The correct answer is **REPL** — Read → Evaluate → Print → Loop

---

## 🧪 Quiz — Day 2

**Question:** Given a `final_list` and `new_numbers`, complete the code to insert the missing digit, add all contents of `new_numbers` to `final_list`, print the count of the third number, and print the updated list.

```python
final_list = [0, 2, 4, 6, 8, 10]
new_numbers = [1, 3, 5, 7, 9]
```

**Answer:** The sequence goes up in increments of two — `6` was the missing digit. Use `.insert()`, `.extend()`, and `.count()`.

---

## 🧪 Quiz — Day 3

**Question:** Find all numbers divisible by 7 in a range of 0-100.

```python
lst = list(range(0, 101))
for num in lst:
    if num % 7 == 0:
        print(num)
```

**Question:** Write a function that prints "Let's start class!" if the user provides 17 students; "Too many students..." if higher; otherwise calculate how many are still needed.

```python
def check_students(count):
    if count == 17:
        print("Let's start class!")
    elif count > 17:
        print("Too many students...")
    else:
        needed = 17 - count
        print(f"Really? We are still waiting on {needed} students?!")
```

**Question:** Write a function that returns `True` only if the data type is a list AND it has something in it.

```python
def check_data(stuff):
    if isinstance(stuff, list) and len(stuff) > 0:
        return True
```

**Question:** Students have taken an exam twice with a passing score of 70. Return the final grade based on two scores. Both arguments must be `int` or `float`.

**Question:** Boolean evaluation answers:

| Expression | Result |
|-----------|--------|
| `False == False` | `True` |
| `True and True` | `True` |
| `(3 != 3) == False and False == False` | `True` |
| `3 == 3 and 3 == 4` | `False` |
| `False and False` | `False` |
| `"Kirk" == "Carter" or 1000 <= 1001` | `True` |

**Question:** Calculate the average from a list of grades, rounded to a whole number.

```python
def avg_grades(grades):
    return round(sum(grades) / len(grades))
```

**Question:** Turn a range into a list, print its length, then print odd numbers.

```python
data = range(3, 24)
data_list = list(data)
odds = [n for n in data_list if n % 2 != 0]
print(len(data_list))
print(len(odds), odds)
```

**Question:** Reverse any iterable using slicing.

```python
def reverse_iterable(data):
    return data[::-1]
```

---

## 🧪 Quiz — Day 4

**Question:** Harry Potter horcrux problem — use a `while` loop to remove random horcruxes until only Harry Potter remains.

**Question:** Given a list of integers, create a string from their character representations.

**Question:** Promote soldiers whose last names start with A-D and are designated "Eligible".

---

## 🧪 Quiz — Day 5

**Question:** True or False: If a file exists, write mode will NOT overwrite the file.

**Answer:** `False` — write mode (`w`) **will** overwrite the file.

**Question:** Which function reads the entire contents of a file from current cursor position?

**Answer:** `read()`

**Question:** Continuously read user strings and write each on its own line to a file.

```python
def gathering_thoughts(fname):
    with open(fname, 'w') as f:
        while True:
            line = input()
            if not line:
                break
            f.write(line + '\n')
```

**Question:** Copy contents from one file to another.

```python
def copy_paste(infile, outfile):
    with open(infile, "r") as f_in:
        content = f_in.read()
    with open(outfile, "w") as f_out:
        f_out.write(content)
```

**Question:** Read file contents into a variable and print.

```python
with open("Test.txt", "r") as file:
    contents = file.read()
print(contents)
```

**Question:** Read all usernames into a list.

```python
with open("Test.txt", "r") as file:
    usernames = file.readlines()
print(usernames)
```

**Question:** Write "Python is fun" to a file in append mode.

```python
with open("info.txt", 'a') as file:
    file.write("Python is fun")
```

---

## 🧪 Quiz — Day 6

**Question:** Add "CW2 Parsons" with key "Newest instructor" to the dictionary.

```python
instructors = {'instructor1': 'Coolguy', 'instructor2': 'Joshua', 'instructor3': 'Jonathan'}
instructors['Newest instructor'] = 'CW2 Parsons'
print(instructors)
```

**Question:** Which technique retrieves dictionary values without errors if the key doesn't exist?

**Answer:** `dictionary.get("key1")`

**Question:** Count how many 3's are in the tuple.

```python
tup = (1, 2, 3, 3, 4, 5, 6, 3, 7, 3, 8, 3)
print(tup.count(3))    # 5
```

**Question:** Print the type of 50.

```python
print(type(50))    # <class 'int'>
```

**Question:** Print the boolean value of 1.

```python
print(bool(1))    # True
```

---

## 🧪 Quiz — Day 7

**Question:** Complete args and kwargs code:

```python
def sumAll(*args, **kwargs):
    return sum(args) + sum(kwargs.values())

print(sumAll(1, 2, 3, 4, a=1, b=2, c=3))    # 16
```

**Question:** What does `**kwargs` do in a function definition?

**Answer:** Packs pairs of `keyword=value` into a dictionary.

**Question:** What does `*args` do in a function definition?

**Answer:** Packs positional arguments into a tuple.

**Question:** What does `*` do to a list when passed to a function?

**Answer:** It **unpacks** or expands the list into individual arguments.

**Question:** True or False: Positional arguments must come before keyword arguments.

**Answer:** `True`

**Question:** Print all positional arguments on separate lines, then keyword arguments in alphabetical order.

```python
def infinitearguments(*args, **kwargs):
    for arg in args:
        print(arg)
    for key in sorted(kwargs):
        print(f'{key}={kwargs[key]}')
```

**Question:** Read file lines, return sorted in case-insensitive ASCII order.

```python
def sort_ascii(filepath):
    with open(filepath, 'r') as file:
        lines = [line.strip() for line in file.readlines()]
        lines.sort(key=str.lower)
    return lines
```

**Question:** Read file lines, return sorted longest to shortest.

```python
def sort_length(filepath):
    with open(filepath, 'r') as file:
        lines = [line.rstrip('\n') for line in file if line.strip()]
    return sorted(lines, key=len, reverse=True)
```

---

## 🧪 Quiz — Day 8

**Question:** What is the purpose of `__init__`?

**Answer:** To initialize the attributes of a new object instance.

**Question:** What is the purpose of `__str__`?

**Answer:** To define a custom string representation of an object.

**Question:** What is the purpose of `if __name__ == "__main__":`?

**Answer:** To determine if a script is being run directly or imported as a module.

**Question:** What is the purpose of `self` in class methods?

**Answer:** To access instance variables and methods within the class.

**Question:** Create a `Car` class with year, make, model, color, trim, and transmission.

```python
class Car:
    def __init__(self, year, make, model, color, trim, transmission):
        self.year = year
        self.make = make
        self.model = model
        self.color = color
        self.trim = trim
        self.transmission = transmission

    def __str__(self):
        return f'{self.year} {self.make} {self.model}\n  Color: {self.color}\n  Trim: {self.trim}\n  Transmission: {self.transmission}'
```

**Question:** Create a `Chest` class that stores items, with `add`, `drop`, and `empty` methods.

```python
class Chest:
    def __init__(self, *items):
        self.items = list(items)

    def add(self, *new_items):
        self.items.extend(new_items)

    def drop(self, *items_to_remove):
        for item in items_to_remove:
            if item in self.items:
                self.items.remove(item)

    def empty(self):
        self.items.clear()
```

**Question:** Create a `ServiceMember` class with branch, name, rank, and MOS. Allow changing MOS and rank.

```python
class ServiceMember:
    def __init__(self, service, name, rank, mos):
        self.service = service
        self.name = name
        self.rank = rank
        self.mos = mos

    def change_mos(self, new_mos):
        self.mos = new_mos

    def change_rank(self, new_rank):
        self.rank = new_rank
```

---

## 🧪 Quiz — Day 9 (Practice Test)

**Question:** Calculate a grade curve from the highest score to 100.

```python
def curve_scores(grades):
    curve = 100 - max(grades)
    return [grade + curve for grade in grades]
```

**Question:** Dictionaries store values in **key** and **value** pairs. If you `pop` an item, it is extracted as a **tuple**.

**Question:** Read a log file of failed logins, count per user, and append results.

```python
def count_failed_logins(logfile, resultfile):
    with open(logfile, 'r') as f:
        lines = f.readlines()
    counts = {}
    for line in lines:
        user = line.split()[3]
        counts[user] = counts.get(user, 0) + 1
    with open(resultfile, 'a') as f:
        for user, count in counts.items():
            f.write(f'{user}: {count} failed logins\n')
```

**Question:** The function used to gather data from a user is `input()`.

**Question:** Select all mutables: **set**, **dictionary**, **list**, **variable**.

**Question:** What is the scope of `lst1` inside a function? **Answer:** Local.

**Question:** Select all ways to sort a tuple in descending order:
- `(1,2,3,4)[::-1]`
- `sorted((1,2,3,4), reverse=True)`

**Question:** Number of methods/attributes for a boolean object?

```python
len(dir(bool))    # 71
```

**Question:** Choose the correct index:

```python
list1 = [6, 3, 4, 7, 1, 2][3]     # 7
list1 = ["Good", "morning", "class"][0]    # Good
list1 = ["Jackson", "Jordan", "Tyson", "Phelps", "Bay", "Cera"][-1]  # Cera
```

**Question:** Convert a string number into an integer.

```python
def make_number(program_input):
    return int(program_input)
```

**Question:** Your Python file must have execute permissions and a shebang line to execute with only the filename. **Answer:** `True`

**Question:** Match container types:

| Syntax | Type |
|--------|------|
| `[1]` | `list` |
| `{1}` | `set` |
| `{'a': 1}` | `dict` |
| `(1,)` | `tuple` |

**Question:** Boolean evaluation:

| Expression | Result |
|-----------|--------|
| `1 == True` | `True` |
| `False or True == True` | `True` |
| `"True" == True` | `False` |
| `True and True == False and False` | `False` |
| `True or False == False` | `True` |

**Question:** Which is NOT a string method? **Answer:** `len()` (it's a built-in function, not a string method).

**Question:** Remove duplicates and return a sorted descending list.

```python
def no_dupes(given_lst):
    unique_set = set(given_lst)
    unique_list = list(unique_set)
    unique_list.sort(reverse=True)
    return unique_list
```

**Question:** Create an agent name from a full name for "Men in Black."

```python
def mib_name(name):
    return f"Agent {name.split()[1][0].upper()}"
```

**Question:** When binding a network socket with an IP and port, what data type must be used? **Answer:** `tuple`

---

## ✅ Summary

- **Day 1:** Python fundamentals — syntax, data types, variables, execution modes
- **Day 2:** Lists, tuples, strings, functions, scope (LEGB)
- **Day 3:** Operators (relational, logical, membership), conditionals, slicing, `range`, `sum`, `round`
- **Day 4:** `while` loops, `for` loops, `enumerate`, standard libraries (`math`, `random`)
- **Day 5:** File I/O — `open`, `read`, `write`, `seek`, `tell`, the `with` statement
- **Day 6:** Dictionaries, sets, `*args`, `**kwargs`, lambdas
- **Day 7:** Sorting with `sorted()` and `.sort()`, custom `key` functions, `ord`/`chr`
- **Day 8:** OOP — classes, `__init__`, `__str__`, magic methods, inheritance, polymorphism

---

[⬆️ Back to Module Index](../README.md) | [Next: 01 — Fundamentals & Data Types →](01_Fundamentals_02_Data_Types.md)
