# 🔪 Slicing

*Module 01 — Python | Day 3*

---

## 🎯 Learning Objectives

- Slice lists, strings, and tuples with `[start:stop:step]`
- Use `len()`, `sum()`, `range()`, and `round()` built-in functions
- Understand exclusive stop values in slicing and `range()`
- Apply `enumerate()` for indexed iteration

---

# Slicing Iterable Objects

You have seen indexing that allows access to an individual item in a `list`/`tuple` or character in a `str`. There may be times you need to access more than one item or character at a time. Slicing gives you this ability.

Syntax:

`item_to_slice_from[start:stop:step]` Notice that these are colon `:` separated

The `start`:`stop`:`step` numbers are integers that represent the index values for the sequence being sliced from.

- NOTE: the `stop` value is EXCLUSIVE, which means it slices up to, but NOT including the index number provided.

Use slicing to print the first three items found in the following `list`:

```python
lst = ['zero',1, 'two', 3, 'four', 5]

print(lst[0:3])
```

Use slicing to print everything starting at index 5 and not including index 18 of a `str`:

```python
sentence = "This is an example sentence."
print(sentence[5:18])
```

Use slicing to print everything starting at index 5:

```python
sentence = "This is an example sentence."
print(sentence[5:])
```

Use slicing to print everything up to but not including index 18:

```python
sentence = "This is an example sentence."
print(sentence[:18])
```

Use slicing to print everything except the last character:

```python
sentence = "This is an example sentence."
print(sentence[:-1])
```

Use slicing to print the last 9 characters:

```python
sentence = "This is an example sentence."
print(sentence[-9:])
```

Use slicing to reverse a string or a list

```python
sentence = "This is an example sentence."
print(sentence[::-1])

lst = ['zero',1, 'two', 3, 'four', 5]
print(lst[::-1])
```

Use slicing to create a shallow copy of a list

```python
aList = [1, 2, 3, 4, 5]
print(aList[:])     # creates a shallow copy of the list

a = aList
print(a is aList)
a = aList[:]
print(a is aList)
```

# Length, Range, Sum, and Rounds Functions

## Length Function

The `len()` function returns the total number of items found inside of an iterable object.

More information about the `len()` function can be found at:
- [W3Schools](https://www.w3schools.com/python/ref_func_len.asp)
- [Python Docs](https://docs.python.org/3/library/functions.html#len)

Syntax:

`len(iterable_item)`

Examples using the `len()` function

```python
# len() - built-in funcction that returns the number of elements in a collection
aStr = 'hello'
print(len(aStr))

aList = [1, 2, 3, 4]
print(len(aList))

aTuple = (1, 2, 3, 4, 5, 6)
print(len(aTuple))

lst2 = [1,2,3,['a','b','c'],(9,'8',7)]
tup_len = len(lst2[-1])
print(tup_len)
```

Using `len()` in a math equation

|  **Scenario:** |
|---|
|given one `list` object, one `tuple` and one `str`, find the total number of items found in all of three objects.|

```python
lst1 = [1,2,3,4]
tup1 = ('hello', 'world')
str1 = 'Python was first released in 1991'
total = len(lst1) + len(tup1) + len(str1)
print(total)
```

## Range Function 

The `range()` function requires at least one `int` argument and returns a sequence of integers stored inside a literal `range` object type. It is important to note that the `range()` function does NOT return a `list` object type. 

More information about the `range()` function can be found at: 
- [W3Schools](https://www.w3schools.com/python/ref_func_range.asp)
- [Python Docs](https://docs.python.org/3/library/functions.html#func-range)

Syntax:

`range(start, stop, step)` Notice that these are comma `,` separated

- The `start` and `step` values are optional. They have a default value of 0 (for start) and 1 (for step).

- It is important to note that the `stop` value is EXCLUSIVE

- The `range()` function is helpful when you need a sequence of numbers

Creating a `range` object using only the `stop` value:
- Remember that it will default to a `start` value of 0 and a `step` of 1

```python
# range() - built-in function that creates a range object
# arguments are start, stop, step where only stop is mandatory; by default start is 0 and step is 1

print(range(10))
print(type(range(10)))

print(list(range(10)))          # ordered sequence from 0 to 9
print(list(range(1,10)))        # ordered sequence from 1 to 9
print(list(range(1,10,2)))      # ordered sequence of odd numbers from 1 to 9
print(list(range(10,-1,-1)))    # ordered sequence from 10 to 0
```

| **Scenario:** |
|----|
| Create `list` of indices for a `str` |

```python
myString = 'Hello World'
myStringIndices = list(range(len(myString)))
print(myStringIndices)
```

|  **Scenario:** |
|---|
|Create a `list` object of the `int` from 5 to 100|

```python
num_lst = list(range(5,101))
print(num_lst)
```

|  **Scenario:** |
|---|
|Create a `list` of the even `int` from 0 to 100|

```python
even_nums = list(range(0,101,2))
print(even_nums)
```

**Scenario:** |
|---|
|Create a `list` of the odd `int` from 0 to 100|

```python
odd_nums = list(range(1,101,2))
print(odd_nums)
```

|  **Scenario:** |
|---|
|`print` every fifth `int` in the range of `int` from 5 to 100 inclusively|

```python
nums = list(range(5,101,5))
print(nums)
```

|  **Scenario:** |
|---|
|Make a `list` of `int` from 50 to 0 inclusively|

```python
countdown = list(range(50,-1,-1))
print(countdown)
```

## Sum Function

The `sum()` function requires only ONE iterable item and returns either an `int` or `float` (depeneding on number types used in function)

More information on the `sum` function can be found at: 
- [W3Schools](https://www.w3schools.com/python/ref_func_sum.asp)
- [Python Docs](https://docs.python.org/3/library/functions.html#sum)

Syntax:

`sum(iterable_item)`

```python
# sum() - built-in Function that adds up all numbers in an iterable (every item must be a number)
aList = [1, 2, 3, 4]
print(sum(aList))

aTuple = (1.1, 2, 3.57)
print(sum(aTuple))
```

## Round Function

The `round()` function accepts up to two arguments and returns a `float` that is rounded to the level of precision (or number of decimal places) specified by the second argument, the *digits*. If the level of precision is 0, then `round()` returns an `int`.

[W3Schools](https://www.w3schools.com/python/ref_func_round.asp)
[Python Docs](https://docs.python.org/3/library/functions.html#round)


Consider PI: 
3.141592653589793238462643383279502884197

Depending on the project the level of precision of PI may need to vary

Use the `round()` function to round PI to varying levels of precision

```python
# round() - built-in function that rounds argument to nearest integer (up or down)
print(round(4.3))
print(round(4.6))
```

```python
pi = 3.141592653589793238462643383279502884197

default = round(pi)
print(default)

level_one = round(pi,1)
print(level_one)

level_four = round(pi,4)
print(level_four)
```

## Examples

Put these two functions together in practice.

|  **Scenario:** |
|---|
|Find the `sum` of all the `floats` in a `list` and then use the `round()` function to round the answer to 3 decimal places|

```python
nums = [1.48, 6.58793, 6.254789, 100.25741, 129.4587]

answer = sum(nums)
print(answer)

rounded = round(answer,3)
print(rounded)

rounded_again = round(sum(nums),3)
print(rounded_again)
```


---

[⬆️ Back to Module Index](../README.md)
