# 🐍 Python Fundamentals & Data Types

*Module 01 — Python | Day 1*

---

## 🎯 Learning Objectives

- Understand Python syntax, semantics, and grammar rules
- Identify and work with core data types: `int`, `float`, `bool`, `str`, `list`, `tuple`, `NoneType`
- Use `type()`, `print()`, `input()`, and conversion functions
- Declare variables using Python naming conventions
- Perform mathematical operations and augmented assignment
- Access Python’s built-in help system

---

# Basic Syntax And Semantics

Python's **syntax** refers to the set of rules and structures that dictate how code is written in the language. It includes conventions for defining variables, writing statements, and organizing code. Python uses a combination of English keywords and punctuation symbols to construct valid expressions and statements

## Errors:
When writing code, errors will arise quite often. These errors may cause the programs to crash, run forever or provide inaccurate results. These issues are usually caused by runtime, logic or syntax errors.

- **Runtime** - error occurs when a program runs instructions that the computer can’t execute.

```python
2/0
```

- **Syntax error** - occurs when an instruction does not follow the syntax rules of the programming language.

```python
print(4
```

## Semantics:
Python **semantics** defines how the code is executed and the behavior of various constructs. Semantics determines how expressions are evaluated, variables and objects are managed, control flow is handled, and how functions and classes are used. It also includes the rules for variable scope, function calls, object references, and how different data types behave.

Similar to the semantics of a sentence in english python semantics provide the meaning and interpretation of the programming language.

- **Semantics error** - are a type of logic error that are more subtle and occur when the code is grammatically correct but doesn't produce the intended results due to logical or functional mistakes. Semantic errors can be harder to detect and may lead to unexpected behavior in the program.

```python
pi = 3.14159
radius = 10
circumference = 3 * pi * radius
print(circumference)
```

## Case Sensitivity
Python is case sensitive meaning it considers uppercase and lowercase characters differently. Therefore, the following two variables are different. 
```python
# The “=” assigns the variable name the_Person to the string “Him”
the_Person = "Him"

# The “=” assigns the variable name the_person to the string “Her”
the_person = "Her"

```python
the_Person = "Him"
the_person = "Her"
print("the_Person: ", the_Person)
print("the_person: ", the_person)
```

# Python Grammar 

## White Space

In Python, **whitespace** refers to spaces, tabs, and newline characters that are used for formatting and structuring the code. White space assist with determining the structure and readability of Python programs. Unlike some other programming languages, Python uses whitespace for indentation and block delineation, which affects how code is executed.

- **Indentation**: Used to define blocks of code

- **Space in expressions**: Separates elements in a block of an expression

- **Blank lines**: used to separate blocks of code for better readability

## INDENTATIONS vs. TABS

Python uses **indentation** to define blocks of code, such as those inside loops, conditionals(if/else), functions, and classes. Python relies heavily on  whitespace to determine the control flow structure of an application. As control structures are introduced, we will revisit the indentation rules. Consistent and proper indentation is crucial for the program's functionality. When creating "White Space" using the space bar is preferred over “Tab”  indentation method.  Tabs should be used solely to remain consistent with code that is already indented with tabs.

## Comments

- **Comments** are used to explain and label Python code and will be ignored by the Python interpreter.  They are use to provide more information about the functionally of the code and ultimately to make Python code more human-readable.

- Comments assist with **collaboration and ease of use** allowing other users or developer edit your code.

- Comments can also be used to prevent execution when testing code. If you are troubleshooting your code, you can use comment blocks to organize the flow of execution so that you can identify run time errors or incorrect logic.

```python
# this is a comment and will not be executed
print('hello') # print() - built-in function that outputs to the screen

# This is a comment!!
# It is multilined
```

## Statements

- In Python, **statements** are sequence of instructions or commands that perform specific actions.
    
    - Examples of statements include variable assignments, conditional statements (if-else), loops (for, while), and function definitions.
    <br>

- All lines in a Python application must begin in the first column, unless the statement is in the body of a loop, conditional, function, or class definition.

## Line / Statement Terminator
- In python, the **statement terminator** is marked by the end of the line. In the example below, we can see that two separate statements are split by a newline.

```python
x = 5 + 5
print(x)
```

```python
length = 10; width = 5
area = length * width
print(area)
```

- We can extend the statement beyond the end of line by using the backslash character `\` [Backslash]

- When used in this fashion it is often referred to as the line continuation character.

- In the example below, we can continue with our statement on newlines without ending the statement.

```python
result = 500 * 2 + \
400 * 3

print(result)
```

# Help in Python

## Python Documentation
There are various ways in which a Python programmer can get help from the Python documentation. A good starting point is one of the 

following URLs:
<br>
[Python Docs - Latest Version](https://docs.python.org/3/)
<br>
[Python Docs - By Version](https://www.python.org/doc/versions/)

!!! Note
     run ```py python3 --version``` to find the current version of python on your machine


## Built-in Help
In addition to the online Python documentation, the interactive Python shell can provide additional help. Typing ``help()`` at the Python shell prompt will start the Python help utility. For example:

```python
# using the dir and help functions
help(str)
```

```python
dir(str)
```

```python
help(str.title)
```

# Introducing the `print()` function

The `print()` function is intuitively named and provides a copy of the items placed inside the parentheses.

We will use this function randomly throughout this course to view our data.

The `print()` function is a great way to test your code and make sure it is correctly executing the commands and the logic you provide in your future code blocks.

Some examples of using `print()`. We will discuss this function in more depth later, just become comfortable with using it for now.

Next we will begin discussing what each of the items are that are found inside the following `print()` examples.

```python
print('hello world')


print(5)


print( 1 + 2)
#NOTE: the print function here accounted for the math being performed inside the parenthesis
```

# Primitive Data Types and the `type()` function

- In programming, data type is an attribute of data which tells the compiler or interpreter how the programmer intends to use the data.

- Python has many data types. Each of these types behave differently and have different attributes.

### type Function

```python
# type() - built-in function that returns the type of the value that is the argument
print(type(1))
print(type(1.1))
print(type('1'))
print(type(True))
print(type([1]))
print(type((1,1)))
```

## Integers - A Numeric Data type

- A number is referred to as an Integer.

- In Python, integers are defined as type `int`.

- Numbers 1,2,3 and 4…​ etc are integers. An integer is any whole number with no decimal or fractional value.

- Python3 does not limit the maximum value of an integer, it is unbounded. Unbounded is a mathematical term for functions and values that have no maximum value.

- The size of the integer is limited to the size of the registers/memory allocated to the integer within the operating system.

More complex information about `int` objects can be found at:
- [W3Schools](https://www.w3schools.com/go/go_integer_data_type.php)
- [Python Docs](https://docs.python.org/3.10/reference/lexical_analysis.html#integer-literals)

```python
# int - whole numbers
print(type(1))
print(type(2))
print(type(-100))
```

## Floating Point - Another Numeric Data type

- Numbers with a decimal are defined as type float.

- A floating point number precision is dependent on the system architecture.

- Precision refers to the accuracy at which small numbers can be measured. The greater the precision the more decimal places can be represented by a value.

More complex information about `float` objects can be found at:
- [W3Schools](https://www.w3schools.com/go/go_float_data_type.php)
- [Python Docs](https://docs.python.org/3.10/reference/lexical_analysis.html#floating-point-literals)

```python
# float - floating point numbers a.k.a. decimal point numbers
print(type(1.5))
print(type(3.14159))
print(type(1.0))
```

**What can python do with numbers?**

### Numerical or Mathmatical Operations with Integers and Floats

| Operation |               Result              |
| --------- | ----------------------------------|
| x + y     | Sum of x and y                    |
| x - y     | difference of X and Y             |
| x * y     | Product of X and Y                |
| x / y     | Quotient of x and Y               |
| x // y    | Floored (integer) Quotient of X and Y   |
| x % y     | Modulus: The remainder of x / y   |
| x ** y    | x raised to the y power           |
| -x        | x negated                         |
| +x        | x unchanged                       |
| abs(x)    | Absolute Value(or magnitude of x) |

```python
# mathematical operators
a = 8
b = 3
print(a + b)    # addition
print(a - b)    # subtraction
print(a * b)    # multiplication
print(a / b)    # division
print(4 / 2)    # division always results in a float
print(a // b)   # integer division
print(a % b)    # modulo division
print(a ** b)   # exponentation
```

## Boolean

- The bool data type is named after Boolean values. In short, a bool data type at its most base level can hold only the values 0 or 1.


- This can be thought of as a way to express True [1] or False [0]. For example, the bool value of 0 represents False.
- Any value of a variable other than 0 or the empty version of other data types will result to True in Bool

More complex information about `bool` can be found at:
- [W3Schools](https://www.w3schools.com/go/go_boolean_data_type.php)
- [Python Docs](https://docs.python.org/3.10/c-api/bool.html)

- Python supplies keywords to express True and False, these are unsurprisingly, True and False.
  - The case is important.
  - Both must start with a capital letter.
  - Also make note that there are no quotation marks around True or False.

```python
# bool - boolean: only two possible values are True and False
print(type(True))
print(type(False))
```

## String

- A string is a sequence of characters (upper and lowercase alphabetical characters, numbers, or special characters) surrounded by quotation marks.

- A string may also be referred to as a string literal.

- A literal is a basic value.

- This is raw data that cannot be changed once initialized.	
  - Also referred to as *immutable*
  - Immutable means that the object, a string in this case, cannot be changed once created.

- Python will recognize this data type as `str` for string.

- A Python expert would describe strings as an “immutable sequence of zero or more characters.”
  - This means that an empty string is a valid objet type

More complex information about `str` can be found at:
[W3Schools](https://www.w3schools.com/go/go_string_data_type.php)
[Python Docs](https://docs.python.org/3.10/tutorial/introduction.html#strings)

```python
# str - string: ordered sequence of characters
print(type('hello'))
print(type('1'))
print(type('1.1'))

# It is important to note that an empty string is also a valid `str` data type. 
print(type('')) 
# the empty string evaluates to False
print(bool(''))
```

### Literal Strings

- Literal string values may be enclosed in single ‘ ‘ or double quotes “ “.


- Since strings are a sequence of characters, the built-in `len` function can be used to determine the number of characters the string contains.


- Literal strings can span multiple lines in several ways.


- Using the line continuation character \ as the last character.


- Literal strings may also be prefixed with a letter r or R.


- These are referred to as raw strings and use different rules for backslash escape sequences.

- If a programmer needs a special character in a string, the programmer may need to use an escape sequence.


### Triple Quoted Strings

- Python supports the use of triple quotes (single or double) for defining a long (or short) string.

```python
# strings denoted in three ways: single quote, double quote, triple quotes
print('This string is formed by single quotes.')
print("This string is formed by double quotes, which is neat don't you think?")
print('''He shouted, "This string is formed by triple quotes, ma'am!"''')
```

```python
# triple quote strings can extend to multiple lines
# these are sometimes used to make multi-line comments
print('''one
two
three
four''')

'''
This
is
a
multi-line
comment
'''
```

### Various Excape Character Meanings

| Sequence | Character/Meaning |
| ------- | ---------------- |
| \        | Line Continuation |
| \\       | Backslash         |
| \'       | single Quote      |
| \"       | Double Quote      |
| \a       | ASCII Bell(BEL)   |
| \b       | Backspace         |
| \f       | Form Feed         |
| \n       | Line feed         |
| \r       | Carriage Return   |
| \t       | Horizontal Tab    |
| \v       | Vertical Tab      |
| \ooo     | ASCII Character (octal value ooo)|
| \xhhh    | ASCII Character (hex value hhh) |
| \uxxxx   | Unicode Character with 16-bit hex value xxxx |
| \Uxxxxxxxx| Unicode Character with 32-bit hex value xxxxxxxx |

```python
# more on strings - escape character (backslash)
print('This string is formed by single quotes, but includes a contraction, wouldn\'t you agree?')
print('This string includes a new line.\nThis sentence is on the next line!')
print('Part 1\n\tSection A\n\t\ti. bullet 1\n\t\tii. bullet 2')
print('Happy Face Emoji:', '\u263A' ) # 16-bits
print('Pensive Face Emoji:', '\U0001F614' ) # 32-bits
```

## List 

Python provides a `list` object, which is a sequence type that can hold a variety of objects.

List objects can be described as:

- An ordered collection of zero or more elements. - Similar to an array in other languages.
  - List objects support efficient element access using integer indices (slice notation).
- Dynamic in that items can be added and removed. This is also referred to as being mutable.
- We will explore more later on the usefulness of an empty list and how to add items to it
- Lists can hold many different data types, and use commas to separate each item in the list

```python
# list - mutable ordered sequence of values, formed by straight brackets
print([])
print(list([]))
print(type([1, 2, 3]))
print(type([1, 1.0, '1']))
print(type([]))
# the empty list evaluates to False
print(bool([]))
```

## Tuple

Tuples are similar to lists in that they can hold multiple items of varying data types separated by commas; however, they are NOT dynamic/mutable, they are immutable. This means that tuples CANNOT be changed once they are set.

More on `tuple` can be found at: 
- [W3Schools](https://www.w3schools.com/python/python_tuples.asp)
- [Python Docs](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)
- There is not much usefulness to creating an empty `tuple` since it cannot be altered, but it is still possible

There are more ways than one to create a `tuple`:

```python
#surrounding a collection of objects in parentheses:
print(type((1,2,3,4)))
print(type(('one','two','three','four')))
print(type((1, "string", 3.0, True)))
# the empty tuple evaluates to False
print(bool(tuple()))
```

!!! NOTE
  In order to create a `tuple` with just one item, you must add a comma after the item, otherwise Python can interpret the the parentheses as mathmatical operators implementing order of operations

```python
print(type(('one')))
print(type(('one',)))
```

## None Type 

- Another data type in Python is the NoneType which can be represented by using the None keyword.

- None is similar to null in other languages. In Python, None means nothing and will evaluate to False in a conditional statement.

- None is often used to check the result of some action or to ensure a variable has a value and is not nothing

```python
print(type(None))
```

## Why knowing your type is important

- Because python is a strongly typed langage, some data types work well together and some produce errors when you try to make them work together

```python
# + operator works with numbers
print(1 + 2.5)
```

```python
# + operator works with strings
print('hello' + 'world')

# + operator works with lists
print([1,2,3] + [4])
```

```python
# + operator does not work with numbers and strings
print(1 + 'hello world')
```

```python
# * operator works with strings and integers
print('hello world' * 3)

# * operator works with list and integers
print([1,2,3] * 3)
```

# Python Keywords

- Python keywords are reserved words within the language.

- In algebra class students learn to name values with names like x, y, and 𝛑 (pi).

- Likewise, a programmer can assign names to values in Python as well, however it would be wise to avoid any Python keyword.

- These words cannot be used as the names of variables or functions.

- They are listed here for reference.

|               |               |              |                 |                 |
| ------------  | ------------- | ------------ | ----------------| ----------------|
| ```False```   | ```class```   | ```finally```| ```is```        |  ```return```   |
| ```None```    | ```continue```| ```for```    | ```lambda```    |  ```try```      |
| ```True```    | ```def```     | ```from```   |  ```nonlocal``` |  ```while```    |
| ```and```     | ```del```     | ```global``` |  ```not```      | ```with```      |
| ```as```      | ```elif```    | ```if```     |  ```or```       |  ```yield```    |
| ```assert```  | ```else```    | ```import``` | ```pass```      |  ```break```    |
| ```except```  | ```in```      | ```raise```  |                 |                 |

```python
#This table can be generated by executing:
help('keywords')
```

# Dealing With Variables 
## Naming Conventions

- A Python identifier is a name that is used to identify any of the following:  
    - Variables, Functions/Methods, Classes, or Modules

- Often Python programming documentation will use the term name to describe an identifier. An identifier must start with:
    - A letter of the alphabet or the underline _ character.

- This can be followed by any number of letters, digits and/or the _ character.

- Identifier names cannot consist of any other characters:
    - Variable names and function names typically begin with a lowercase letter, while class names typically start with an uppercase letter.

- As discussed in the previous section, keywords cannot be used as variable names. Python will allow you to use built-in function names as variable names, but it is highly recommended that you do not do this.

- Use the assignment operator `=` to store a value in a variable

- Remember that Python is a case-sensitive language. 
    - This means `mynumber`, `MyNumber`, and `Mynumber` are three different variables.

```python
mynumber = 1
MyNumber = 2
Mynumber = 3
```

- Some Python programmers might prefer another option, `my_number`.
- The use of underscores between multi-word names is called snake_case.
- Capitalizing the first letter of each word with no spaces between is called CamelCase.
- There are many different naming styles within the language.

### variable naming rules

```python
# Variable naming rules
# Variable names are case-sensitive
a = 4
A = 5
print(a)
print(A)
```

```python
# Variable naming rules continued
# Must start with an underscore or a letter
# May contain underscores, letters, and numbers
# Cannot contain special characters or spaces
a = 4
_a = 4
a123 = 4
my_variable = 4
print(a, _a, a123, my_variable)
```

```python
# Variable naming rules continued
# Cannot use Python reserved words
```

```python
# Variable naming rules continued
# Should not use Python built-in functions
```

```python
# Variables do not have types themselves, but rather it is the value that has the type
a = 4
print(type(a))
a = 'hello'
print(type(a))
```

## Dyanmic Variable Declaration
### What if We wanted to declare more then one variable at a time? 
- The following program emphasizes the dynamic type system of Python.

- In a dynamically typed language, a variable is simply a value bound to a name.

- The value of what is being referenced by the variable has a type like int or float or str, but the variable itself has no type.

- Python uses pass by object reference. Other languages also have pass by value and pass by reference

```python
s,x,y = 'hello', 10, 5.0
tab = " \t"
							                #output: 
print(s, tab, type(s), tab, id(s))			#hello	<class 'str'>       	139954674414256
print(x, tab, type(x), tab, id(x))			#10   	<class 'int'>       	9764672
print(y, tab, type(y), tab, id(y))			#5.0  	<class 'float'>     	139954674401328
```

- Reminder: The built-in `type()` function returns the data type of the object that is referenced by a particular variable.

- Notice that the type of the reference is bound dynamically as the program is executed.

- The built-in `id()` function returns a unique identifier of an object that is referenced by a particular variable.
    - This is the address of a particular place in the computer’s memory.
    - It’s not vital to know this address in normal Python programming but it can illustrate how Python stores and accesses data in memory. There is only a single int object 10 being created as seen below. The memory location of both x and y are the same and they are both assigned the integer 10. Two variables point back to the same memory location for the integer object 10 that was created.

```python
s,x,y = 'hello', 10, 5.0
tab = " \t"
							                #output: 
print(s, tab, type(s), tab, id(s))			#hello	<class 'str'>       	139954674414256
print(x, tab, type(x), tab, id(x))			#10   	<class 'int'>       	9764672
print(y, tab, type(y), tab, id(y))			#5.0  	<class 'float'>     	139954674401328
y = 10
print(y, tab, type(y), tab, id(y))			#10    <class 'int'> 		9764672
```

#### Augmented assignment Operators with math

Augmented assingment is when we want to perform a operation and capture the result of that operation inside our variable.

we can do so using the below operations. 

| Operation |               Result                            |
| --------- | ------------------------------------------------|
| x += y     | Sum of x and y assigned to x                   |
| x -= y     | difference of X and Y assigned to x            |
| x *= y     | Product of X and Y assigned to x               |
| x /= y     | Quotient of x and Y assigned to x              |
| x //= y    | Floored Quotient of X and Y  assigned to x     |
| x %= y     | Remainder of x / y  assigned to x              |
| x **= y        | x to the power of y assigned to x          |

```python
# mathematical operators and assignment examples
a = a + 1
a += 1
print(a)

a = a - 1
a -= 1
print(a)

a = a * 3
a *= 3
print(a)

a = a / 3
a /= 3
print(a)
```

# Data Conversion Functions

## Built-in Conversion Functions

- Often times, a programmer may need to treat a string as a numeric type or a number as a string within your code.
- Python provides several functions that allow these types of conversions to be performed.

Some of the more common built-in conversion functions are:

|               |           |            |
| ------------  | ---------- | ---------- |
| `int()`  | `str()` | `float()` |
| `list()` | `tuple()` | `bool()` |

A more complete listing of Python built-in functions can be found at:

- [W3Schools](https://www.w3schools.com/python/python_ref_functions.asp)
- [Python Docs](https://docs.python.org/3/library/functions.html)

```python
# While tuple is an ordered sequence, it is immutable
# cannot modify a tuple with item assjupyignment

aTup = (1,2,3,4,5)
print(aTup)
aTup[0] = 9
```

### int Function

```python
# type conversion - convert a value from one type to another
# int() - attempt to convert to int type
print(int(1))     # int to int
print(int(True))  # bool to int
print(int(3.1))   # float to int
print(int('3'))   # str to  int
```

```python
# int() will not always succeed
print(int('3.1'))
```

### float Function

```python
# float() - attempt to convert to float type
print(float(3.1))   # float to float
print(float(1))     # int to float
print(float(True))  # bool to float
print(float('3.3')) # str to float
```

```python
# float() will not always succeed
print(float('three.four'))
```

### str Function

```python
# str() - convert to string type
print(str('hello'))     # str to str
print(str(1))           # int to str
print(str(1.1))         # float to str
print(str(True))        # bool to str
print(str([1, 2, 3]))   # list to str
print(str((1, 2, 3)))   # tuple to str
```

### list Function

```python
# list() -  attempt to convert to list type
print(list([1, 2, 3]))  # list to list
print(list('hello'))    # str to list
print(list((1, 2, 3)))  # tuple to list
```

```python
# list() will not succeed if value is not iterable
print(list(3.1))
```

### tuple Function

```python
# tuple() - attempt to convert to tuple type
print(tuple((1, 2, 3))) # tuple to tuple
print(tuple('hello'))   # str to tuple
print(tuple([1, 2, 3])) # list to tuple
```

```python
# tuple() will not succeed if value is not iterable
print(tuple(3.1))
```

### bool Function

```python
# bool() - convert to bool type
print(bool(True))       # bool to bool
print(bool(1))          # int to bool
print(bool(0.0))        # float to bool
print(bool('hello'))    # str to bool
print(bool([]))         # list to bool
print(bool((1, 2, 3)))  # tuple to bool
```

```python
# Why might I want to change a value from one type to another?
```

# Print and Input functions

## Printing on an Intermediate Level

So far you have used `print()` to get standard output. This function has a few modifiers we have not discussed.

`print(*objects, sep=' ', end='\n')`  NOTE: all of these modifiers are optional and do have default values which are provided in this statement

- `*objects` indicates that you can pass multiple objects into a print function separated by commas

!!! NOTE
    There are other modifiers available to the print statement that we will not discuss in this course

```python
# more on print() function
# print() takes a variable number of arguments

# by default the comma will generate a space in the output
print('hello', 'world') 

# can change this with 'sep' keyword argument
print('hello', 'world', sep='+')

# by default print() adds a newline; can change this with the 'end' keyword argument
print('hello world', end=' ')
print('hello world')
```

## How to prompt a user for input

Gathering input from a user is necessary at times. The `input()` is great at collecting this.

HINT: If you encounter a challenge that tells you to '**read** a string from a user' or something similar, think of `input()`

- `input()` - Initiates a prompt to the user and then returns a `str` of the user's data.
    - NOTE: You can place an *optional* prompt inside the parenthesis

It is also important to note that any input collected must be assigned to a variable if you would like to save it or manipulate it in any way.

```python
# input() function -  used to get input from the user via the keyboard
# optional argument is the prompt: this is a message outputed to the screen

a = input('Enter something for me: ')
print(a)
```

```python
# input() always returns a string

a = input('Enter an integer: ')
print(a)
print(type(a))
```

```python
# If we want to do math, then we must convert the user input
a = input('Enter the first integer: ')
b=  input('Enter the second integer: ')
add = int(a) + int(b)
print('The sum of the two integers is', add)
prod = int(a) * int(b)
print('The product of the two integers is', prod)
```


---

[⬆️ Back to Module Index](../README.md)
