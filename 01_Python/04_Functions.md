# ⚙️ Functions

*Module 01 — Python | Day 2*

---

## 🎯 Learning Objectives

- Define and call functions with parameters
- Understand positional and keyword arguments
- Use the `return` statement to pass data back from functions
- Understand variable scope (LEGB rule)

---

# Function Definitions

## Defined Functions you are familiar with already

- `print()`
- `input()`


## Creating Functions 

- To define a unique new function, use the keyword `def` followed by a function name followed by a parenthesized list of parameters, if needed, followed by a colon.

- A function must be defined before it can be used (called). 

- A function in Python defines a block. As with other blocks in Python (if/elif/else statements, and while/for statements) the code must be indented by using all spaces or all tabs. 

- We create functions to group togther code that we are going to call multiple times - write the code once, execute it multiple times.

```python
def multiply(a,b):  # the parameters for this function are a and b
    print(a*b)      # this is the function body

def noParams():
    print('this function has no parameters')
```

## Calling Functions 

- A function call calls the function that is defined which will execute what is in the function. When a function is called, the arguments are the data passed into the method’s parameters.

- Arguments passed to Python functions may be of any type.

- It is the programmer’s responsibility to ensure that the type of data passed is appropriate for how the data is used in the function.

- Argument data is assigned to parameters.

- Python treats assigning arguments to parameters as assignment, meaning that Python does not copy the argument data into the parameters (recall that in Python, assignment never copies data).

- Positional parameters are bound to argument data by their position in the function definition.

```python
multiply(2,3)       # call the function with arguments; they must match up with the parameters
noParams()          # call a function that does not take any arguments
```

Neither `multiply` nor `noParams` have a `return` statement so they implicitly return `None`

```python
multRet = multiply(2,3)
noParamsRet = noParams()
print(multRet)
print(noParamsRet)
```

## Returning Data
- Functions often return values via the `return` statement.

- It is common to save returned values for later use BUT if it is not needed, the function call is equivalent to the returned value when used by the calling code.

### return Statement

```python
# user defined function with a return statement

def power(base, exp):
    return base ** exp

funcReturn  = power(2,10)
print(funcReturn)
```

#### `print` vs `return`

- The `print()` function will simply provide a copy of the function's results/output
- The `return` keyword will actually provide a value that can be assigned to a variable and used

```python
def meantToReturn(x):
    return x*2

def meantToPrint(x):
    print(x*2)

print(f'The return value is: {meantToReturn(10)}')
print(f'The return value is: {meantToPrint(10)}')
```

### pass Statement

```python
# pass statement - legal code that does nothing
# generally provided after a function definition that does not yet have a function body

def myFunction():       # legal function definition
    pass                # legal function body

myFunction()            # function call
```

# Name Scopes

- Functions provide a nested namespace (sometimes called a scope), which localizes the names they use, such that names inside the function won’t clash with those outside (in a module or other function). We usually say that functions define a local scope, and modules define a global scope. 

## The four Python scopes:
1. The ```local``` scope are names created inside a function.
2. The ```enclosed``` scope are names created in a function that encloses (contains) another function. This section includes some examples of names defined in the enclosed scope.
3. The ```global``` scope are names created inside a script outside of any/all functions.
4. The ```built-in``` scope are names that Python reserves for its own internal workings.

- When Python looks to resolve (use) a name, it examines the scopes 'inside-out'.

- Python looks at the most restrictive scope first and works its way outward to increasingly larger scopes.

- Pythonistas express this concept as the ```LEGB``` rule.

- Python looks first in local scope, followed by enclosed, followed by global, followed by builtin (LEGB).

- Each function contains its own scope; if a Python program has six functions that program contains six local scopes. The scope is activated when the function is called and disappears when the function terminates (either normally or abnormally).

- A function cannot change the value of data bound to a name outside its scope (without some extra work). If a Python function uses the name defined in global (or any enclosing) scope, Python creates a new name known only in the local scope and binds data to it.

```python
# Example of local scope
def func():
   within_function = "This is locally defined"
   print(within_function)

func()
```

```python
# Example of a Enclosed Scope
# Creating a function and defining num
def func_1():
   num = 20
   # Creating a function and printing num and num2
   def func_2():
       print(num)
       print(num2)
   func_2()   
num2 = 50
func_1()
```

- The name ```num2``` is defined (known) in the global scope. Functions may access names outside their scope provided the scope is an outer scope (E, G or B scopes).

```python
# Global Scope
# Declaring a global variable
global_var = "I am global"

# Creating a function and changing global_var
def func_1():
   global_var = "New global"
   print(global_var)

# Creating a function and printing global_var
def func_2():
   print(global_var)

func_1()
func_2()
```

```python
# demonstrate why it is not advised to use variable names that are also built-in function names
# this unfortunate result occurs because of local vs global scope
```

# Building Custom Functions - Examples

## Example 1

Python allows you to build your own custom function to accomplish tasks.

Starting with something simple, build a function that multiplies 2 and 4 and `return` the product

```python
def multiply():
    return 2 * 4
```

This function is hardcoded to ONLY multiply 2 and 4.

Make a new function modified to accept two arguments/parameters so that it can multiply ANY two numbers passed into the function.

```python
def multiply(num1, num2):
    return num1 * num2
```

## Example 2

Build a function called `username` that accepts two parameters/arguments. Those arguments will be a person's first name and last name. 

The function should `return` a formatted string that looks like the following:  `last.first`

```python
def username(first, last):
    return f"{last}.{first}"
```


---

[⬆️ Back to Module Index](../README.md)
