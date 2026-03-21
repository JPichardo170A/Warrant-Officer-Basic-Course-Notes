# 🔁 Loops

*Module 01 — Python | Day 4*

---

## 🎯 Learning Objectives

- Use `while` loops for conditional repetition
- Use `for` loops to iterate over sequences
- Control loop flow with `break` and `continue`
- Apply `range(len())` and `enumerate()` for indexed loops
- Use nested for loops and tuple unpacking

---

# Loops

## While Loops

- The `while` statement causes Python to loop through a suite of statements if the test expression evaluates to `True`.

- The `while` statement uses the same evaluations for `True` and `False` as the `if` statement.

- Likewise, the same indentation rules are used for a `while` as they are for an `if`.

- Each time through the loop, if the condition in the `while` is `True`, then the body of the while loop is executed.

- When the condition is `False`, then the loop is complete and the first statement after the `while` loop is executed.

- While loops often require the use of a counter variable.

   - When this is the case, remember to increment the counter variable to prevent an infinite loop!

For more information on While loops:

[W3Schools](https://www.w3schools.com/python/python_while_loops.asp)
[Python Docs](https://docs.python.org/3/reference/compound_stmts.html#while)

!!! TIP
   Any time you need to do something **repeatedly** or **continously** or execute a task **until** a condition is met, think `while` loop

**Helpful Syntax note:**

**while** *condition to be met is True*:
   - take these actions
   - don't forget to incrememnt or update your 'control' variable




Use a `while` loop to print a given number provided in `counter` as long as it is less than or equal to 5:

```python
# Declaring a counter
counter = 1

# While the counter is less than or equal to 5 print counter
while counter <= 5:
    print(f'Loop iteration: {counter}')
    counter += 1  #update the counter to prevent infinite loop
```

|  **Scenario:** |
|---|
|Read a `str` from a user **until** an empty `str` is entered. Append the collected strings to a `list`|
|Remember, an empty `str` is just empty quotes:  `''`|

```python
user_input = input()
user_list = []

while user_input:
   user_list.append(user_input)
   user_input = input()
   print(user_input)
```

Why doesn't the print statement in the following block of code execute??

```python
condition  = False
while condition:
    print('This line will never display.')
```

`while` loops REQUIRE a `True` condition in order to execute the instructions inside

Which is why the following is the dangerous `while` loop:

**Do NOT execute this on your computer without being ready to terminate the code block or IDE**

```python
condition  = True
while condition:
    print('This line displays forever!')
```

When executing a `while True` loop, you must implement a `break` in the loop somewhere to prevent an infinite loop from happening.
## Break

- Any looping construct can have its control flow changed through a `break` statement within it.


- When a `break` is executed, control of the program jumps to the first statement beyond or outside the loop.


- A `break` is often used when searching through a collection for the occurrence of a particular item.

Using the `while True` loop, collect input from a user again **until** an empty `str` is collected. Append user input into a list.

```python
uiList = []

while True:
    ui = input('Enter some characters or simply enter to stop: ')
    if not ui:
        break
    uiList.append(ui)
    

print(uiList)
```

#### continue statement

```python
# the continue statement will immediately end the current iteration of the loop 
# and go to the next iteration (if the loop condition is still True)

# use a while loop to append only single digit odd numbers to a list

oddList = []
num = 0

while num < 10:
    num += 1
    if num % 2 == 0:
        continue
    oddList.append(num)

print(oddList)
```

#### break and continue together

```python
# use break and continue to add integers from user input, break on empty string
# however validate user only enters integers

userSum = 0

while True:
    ui = input('Enter an integer: ')
    if not ui:
        break
    if not ui.isdigit():
        print('That is not an integer, try again!')
        continue
    userSum += int(ui)
    print(f'Your running total is: {userSum}')

print(f'Thanks for using the calculator! The total is: {userSum}')
```

## For Loops

### Basic for loop
- The for loop in Python is used to iterate over the items of any sequence, such as a `str`, `list`, `tuple`, or any iterable object.

- The generic syntax of a `for` loop is: `for target in sequence:` suite

- Each item in the sequence is evaluated once and assigns the item to the target and then the suite is executed.

- The loop terminates after processing the last item in the sequence.

For more information about a for loop: 

[W3Schools](https://www.w3schools.com/python/python_for_loops.asp)

[Python Docs](https://docs.python.org/3/tutorial/controlflow.html#for-statements)

!!! TIP
   Any time you need to do something with **each** or **every** item in a `list` or `str` or any other iterable item, think `for` loop

**Helpful syntax note:**

**for** *every_item* **in** *iterable_item*:
   - take these actions (print, append *every_item* to a new `list`, make it uppercase, etc.)


Use a `for` loop to print each character separately found in the following variable: `strng`

```python
# for loop - used for definite iteration
# employs a loop variable and a loop sequence
# loop sequence values are assinged the loop variable one iteration at a time

strng = 'hello world'

#    loop var        loop sequence
for  each_letter in   strng:
   print(each_letter)
```

Use a `for` loop to print each item found in the `list` on a separate line

```python
lst = [1, 'two', 3, 'four']

for each_num in lst:
   print(each_num)
```

Take is a step further: 

|  **Scenario:** |
|---|
|Iterate over a list of strings. Calculate the total number of characters found in the `list` of `str`|

```python
str_lst = ['this', 'is', 'a', 'list', 'of', 'words']

total = 0
#   loop var      loop sequence
for  word     in    str_lst:
    total += len(word)

print(total)
```

It is also important to note that the `break` keyword can be used in a `for`` loop as well.

|  **Scenario:** |
|---|
|Iterate through a `list` of names. |
|When the name 'sally' is found, `break` the loop and print 'we found sally'|
|Any names encountered before 'sally' should print: '{name} is not sally'|

```python
names = ['bob', 'joe', 'sally', 'harold']

#   loop var          loop sequence
for each_name    in     names:
    if each_name == 'sally':
        print('we found sally!')
        break
    else:
        print(f'{each_name} is not sally')
```

#### break and continue in for loop

```python
# break and continue can also be used in a for loop

# multiply odd numbers from 1 to 99, but stop when product exceeds 1000000000 (one billion)
# don't use step for range to generate odd numbers

product = 1

for i in range(1,100):
    if i % 2 == 0:
        continue
    product *= i
    if product > 1000000000:
        break

print(f'The loop stopped when i was assigned {i} and the product was {product}.')
```

### for loops - extended

Sometimes a `list` or other iterable object may have another iterable object found at each index. Reference the `list` below that contains multiple `tuple` objects. Each `tuple` contains a state `str`, population `int` and the capital `str`. 

How can I access each one of these items individually while iterating over the `list`?

```python
data = [("California", 39937489, "Sacramento"),
       ("Texas", 29472295, "Austin"),
       ("Florida", 21992985, "Tallahassee")]

# the loop variable each_item will contain a tuple
for each_item in data:
    print(each_item)
```

```python
data = [("California", 39937489, "Sacramento"),
       ("Texas", 29472295, "Austin"),
       ("Florida", 21992985, "Tallahassee")]

# dynamic variable declaration unpacks the tuple into three loop variables: state, population, capital
for state, population, capital in data:
    print(f'the state of {state} has a population of {population} and its capital is {capital}')
```

## Using Range and Length Functions Together

### Isolating and Identifying Index Positions

#### range(len()) Functions working together
Using the `range()` and `len()` functions together is helpful when needing to iterate over a collection of items while also identifying which index position each item is in.

```python
lst = ['zero','one','two','three']
for index_num in range(len(lst)):
    print(index_num)
```

Use the dynamic counting created by using `range(len())` to access the items inside the `list`

```python
lst = ['zero','one','two','three']
for index_num in range(len(lst)):
    print(lst[index_num])
```

|  **Scenario:** |
|---|
|Create a queue message to let everyone in the customers list know what position they are in. Use the index number their name is found in to assign their position number|

```python
customers = ['Jim', 'Bob', 'Sue', 'Mary', 'Allen']
Queue_message = ''

for position in range(len(customers)):
    Queue_message += f'{customers[position]} is in position {position}\n'

print(Queue_message)
```

|  **Scenario:** |
|---|
|Given a `list` of names, print the names of people who are found at the even indexes. (Remember, zero counts as an even number in python)|

```python
customers = ['Jim', 'Bob', 'Sue', 'Mary', 'Allen']

for position in range(len(customers)):
    if position % 2 == 0:
        print(customers[position])
```

### enumerate() Function

The `enumerate()` accepts up to two arguments and is a function that returns an enumerate object that assigns numbers to each item found in an iterable object.

This built-in function is another way of accomplishing what the `range(len())` function can also do.

`enumerate()` can be given a *start* `int`; by default when no `int` is supplied the function begins numbering items at 0.

- [W3Schools](https://www.w3schools.com/python/ref_func_enumerate.asp)
- [Python Docs](https://docs.python.org/3/library/functions.html#enumerate)

Syntax:

`enumerate(iterable, start=0)`

```python
lst = ['zero','one','two','three']

print(enumerate(lst))
```

The `enumerate()` function is like the `range()` function that creats a range object that by itself is not abundantly helpful. However, combining it with a `list()` conversion function or using it inside a `for` loop leverages the usefulness of this built-in function.

```python
# start value starts at 0 by default
for num in enumerate(lst):
    print(num)
```

Notice the output each time is a `tuple` of information consisting of the numbered item and the item itself from `lst`

Change the *start* value:

```python
# changing the start value
for num in enumerate(lst, 1):
    print(num)
```

Using dynamic variable declaration in for loop with enumerate

```python
for idx, val in enumerate(lst):
    print(f'{val} is at position {idx} in lst')
```

## list comprehensions

```python
# list comprehension

#syntax --> [ valueExpression for controlVariable in iterator whereClause]

# list of squares of single digit integers

#          valueExpression          contolVariable             iterator
squares = [x*x               for     x                in      range(1,10)]
print(squares)
```

```python
# list of squares of single digit even integers

#          valueExpression          contolVariable             iterator         whereClause
evenSquares = [x*x               for     x                in      range(1,10)      if x % 2 == 0]
print(evenSquares)
```

```python
# list of uppercase letters
upperLetters = [chr(x) for x in range(65,91)]
print(upperLetters)

# list of lowercase letters
lowerLetters = [chr(x) for x in range(97, 123)]
print(lowerLetters)
```


---

[⬆️ Back to Module Index](../README.md)
