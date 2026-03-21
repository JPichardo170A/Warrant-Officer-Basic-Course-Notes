# 📥 Args, Kwargs & Lambdas

*Module 01 — Python | Day 6*

---

## 🎯 Learning Objectives

- Use positional, keyword, and default parameters
- Pack/unpack arguments with `*args` and `**kwargs`
- Write lambda functions for simple operations
- Understand argument ordering rules

---

# Args/Kwargs/Lambdas

## Revisit the Function

So far every function you have worked with has used a fixed number of positional arguments.

A helpful reminder on the breakdown of a function:

```python
def function_name(parameter1, parameter2):
    print(f'argument_1 is assigned to {parameter1}')
    print(f'argument_2 is assigned to {parameter2}')

function_name('this is argument_1', 'this is argument_2')
```

In the example above, `parameter1` and `parameter2` are positional parameters that 'pick up' the positional arguments in the order in which they were passed into the function.

A fixed number of parameters isn't always ideal. Using argument packing and unpacking can help our functions become more dynamic and accepting of more than just a fixed number of parameters.

## Default Parameters

### Optional Arguments 

- Optional arguments depend on default parameter values.

- When the optional argument is not included when calling the function, the function uses the default value coded in the function definition.


- Default arguments must follow non-default arguments.

- Python requires that default parameters must follow non-default (required) parameters as shown below:

```python
def func_1(para1 = "This is a string", para2):
   return (para1, para2)

print(func_1(para1, para2))
```

```python
def addAtLeastTwoNumbers(a, b, c=0, d=0):
    return a+b+c+d

print(addAtLeastTwoNumbers(1,2))
print(addAtLeastTwoNumbers(1,2,3))
print(addAtLeastTwoNumbers(1,2,3,4))
```

## Keyword Arguments 
- Keyword arguments are arguments that can be bound to data by their parameter name.

- Required parameters must have argument data bound to the parameters.

- Optional arguments need not have argument data bound to the parameters.

- For optional arguments, the bound data may not be argument data; bound data may come from the function definition.

- A keyword argument is coded with the name of the corresponding parameter. The argument is coded with the name, not the parameter.

```python
def func_1(para):
   return(para)

print(func_1(para=100))
print(func_1('This is a string!'))
```

!!! NOTE 
    The first call to func_1() uses a keyword argument; the second call does not.

- Python allows the use of both keyword arguments and non-keyword arguments.

- However, the non-keyword argument must be coded before the keyword argument.

```python
def func_1(para1, para2):
   return (para1, para2)

print(func_1(para1=100, para2 = "This is a string"))
print(func_1(para1 = 'This is a string!', para2 = [1,2,3]))
```

```python
def divide(a,b):
    return a/b

print(divide(2,4))
print(divide(a=2,b=4))
print(divide(b=4,a=2))

# Note the above three return the same result, but the below does not return the same result
print(divide(4,2))
```

## Arbitrary Arguments 

- Python allows for functions to treat a sequence parameter as a single argument or as a group of arguments corresponding to sequence elements.
- Code for a varying number of positional parameters of unknown number as follows:

### Positional Arguments

```python
def func(*arbitrary_args):
   print("Number of arguments passes: ", len(arbitrary_args))

func(1,2,3,4)
```

- The `*` operator in a function definition packs a variable number of positional arguments into one parameter as a tuple
- The `*` operator in a function call unpacks a collection into positional arguments

```python
def func(*arbitrary_args):
   print(arbitrary_args)

tup = (1,2,"string")
func(*tup)  # unpacking the tuple
```

```python
def addAtLeastTwoNumbers(a, b, c=0, d=0):
    return a+b+c+d

aList = [1,2]
bList = [1,2,3]
cList = [1,2,3,4]

print(addAtLeastTwoNumbers(*aList))
print(addAtLeastTwoNumbers(*bList))
print(addAtLeastTwoNumbers(*cList))
```

```python
def addAnyNumbersProvided(*args):
    total = 0
    for arg in args:
        total += arg
    return total


print(addAnyNumbersProvided())
print(addAnyNumbersProvided(1))
print(addAnyNumbersProvided(1,2))
print(addAnyNumbersProvided(1,2,3,4,5))
print(addAnyNumbersProvided(*list(range(1,11))))
```

### Keyword Arguments

- Python allows for function to treat a dictionary parameter as a single argument or as a group of arguments corresponding to `keyword`/`value` pairs.

- Code the function definition that accepts a varying number of keyword arguments as follows:

```python
def func(**dict_arg):
   print("The len of args: ", len(dict_arg))
   print("arguments: ", dict_arg)

func()
func(arg1 = "String", arg2 = [1,2,3])
func(arg1 = "String", arg2 = [1,2,3], arg3= (1,2,3))
```

- The `**` operator in a function definition packs a variable number of keyword arguments into one parameter as a dictionary
- The `**` operator in a function call unpacks a dictionary into keyword arguments

```python
def func(**dict_arg):
   print("The len of args: ", len(dict_arg))
   print("arguments: ", dict_arg)

kwarg_dict = {'arg1':['Value 1'], 'arg2':'Value 2', 'arg3': ['Value', 3]}
func(**kwarg_dict)  #unpacking the dictionary keyword and values into the function (just like the previous function call worked)
```

## Lambdas

- lambda is a Python keyword
- A lambda may contain only one statement
- Lambdas cannot contain certain Python statements
- In particular, the  `return`, `pass`, `assert`, `raise` statements may not be coded in a lambda
- Lambdas always `return` a value.
- More information on lambdas can be found at:
    - [W3schools](https://www.w3schools.com/python/python_lambda.asp)
    - [Python Docs](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions)

Lambda Syntax:

`func_name_as_var = lambda param : expression` 

- The expression will be filled in with the action to perform on param

Example:

```python
add_10 = lambda num : num + 10

print(f'lambda: {add_10(50)}')

#the above is the 'shorthand' version of the same thing listed below: 

def add_10(num):
    return num + 10

print(f'function: {add_10(50)}')
```

```python
def t(x):
    return x+1

z = t(1)
print(z)

y = lambda x: x+1
z = y(1)
print(z)

# t and y are functionally the same although t is a named function and y is a lambda function
print(t)
print(y)
```

**Lambda functions will prove valuable when we introduce sorting**


---

[⬆️ Back to Module Index](../README.md)
