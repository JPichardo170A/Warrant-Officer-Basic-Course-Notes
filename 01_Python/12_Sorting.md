# 📊 Sorting

*Module 01 — Python | Day 7*

---

## 🎯 Learning Objectives

- Sort with `sorted()` (returns copy) and `.sort()` (in-place)
- Use `reverse=True` for descending order
- Apply custom `key` functions for sorting
- Understand ordinal sorting with `ord()` and `chr()`
- Sort dictionaries by keys or values

---

# Sorting Sequences

## Sorting Numerically vs. Alphabetically

- At a computer's most basic level everything, including words, are interpreted in ones and zeros. Sorting works much the same using the numerical value of an `int` and `float` or the ordinal value of a `str` character. 

- By default Python sorting methods sort from smallest to largest. This can be modified by adjusting the `reverse` parameter.

- Furthermore, a `key` can be assigned to tell Python what function to use to decide a unique sorting order. By default this parameter is `None` and sorts by numerical values of the items found in the sequence to be sorted.

More information can be found on Python sorting at the following links:

- [W3Schools](https://www.w3schools.com/python/ref_func_sorted.asp#gsc.tab=0)
- [PythonDocs](https://docs.python.org/3/library/functions.html#sorted)

## Two ways to perform sorting:

- `sorted(item, key, reverse)` - This function works  for `str`, `tuple`, `list`, and `dict` data types. It produces a COPY of the specified item sorted according to the key and reverse values given.

- `.sort(key, reverse)` -  This method ONLY works on `list` objects. It reaches into the memory location of where the `list` is stored and PERMANENTLY sorts the `list`

## Sorting a list

### Numerically sort a list of numbers

|  **Scenario:** | |
|---|---|
| *What to sort*| *How to sort it*|
| `num_lst` | smallest to largest|

```python
num_lst = [5,4,3,9,20,5,40,89,46]

num_lst_sorted = sorted(num_lst)
print(num_lst_sorted)
```

```python
import random
aList = random.sample(range(1,100), 10)
print(aList)

aListSorted = sorted(aList)
print(aListSorted)
print(aList)  # original list is unchanged
```

- Using the `reverse` parameter

|  **Scenario:** | |
|---|---|
| *What to sort*| *How to sort it*|
| `num_lst` | largest to smallest|

```python
num_lst = [5,4,3,9,20,5,40,89,46]

num_lst_lg_sm = sorted(num_lst,reverse=True)
print(num_lst_lg_sm)
```

```python
import random
aList = random.sample(range(1,100), 10)
print(aList)

# Can use the reverse keyword to sort in descending order
aListReverseSorted = sorted(aList, reverse=True)
print(aListReverseSorted)
print(aList)        # original list unchanged
```

#### .sort Method

```python
import random
aList = random.sample(range(1,100), 10)
print(aList)

# sort() method permantly changes the list
aList.sort()
print(aList)

aList.sort(reverse=True)
print(aList)
```

### Revisiting ord() and chr()

Remember that the ordinal value of any `str` can be found by using the `ord()` function and the character value of any `int` can be found using the `chr()` function.

```python
x = 'a'
x_ord = ord(x)
print(x_ord)

letter_num = 97
letter = chr(97)
print(letter)
```

### 'Alphabetically' sorting a list of characters

- The word 'Alphabetically' is purposely surrounded in quotations because of the discussion we just had about the `ord()` function. Each character corresponds to an `int` and it is by these `int` that the sorting is actually performed.

```python
characters = ['z', 'd', 'B', 'A', 'a', 'Z']

sorted_chars = sorted(characters)
print(sorted_chars)
```

- Let's get this sorted in actual alphabetical order.
    - We can provide a value to `key` to accomplish this

```python
characters = ['z', 'd', 'B', 'A', 'a', 'Z']

sorted_chars = sorted(characters,key=str.lower)
print(sorted_chars)
```

```python
cList = random.sample('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ', 20)
print(cList)

print(sorted(cList))
print(sorted(cList, key=str.lower))
```

- The `key` in the above example evaluates all of the characters as if they were lowercase. Alternatively, you could use `str.upper` and would still get the same result.

- Another example of sorting words into **reverse** alphabetical order:

```python
words = ['This', 'is', 'a', 'list', 'with', 'words']

sorted_words = sorted(words,key=str.upper,reverse=True)
print(sorted_words)
```

### Sorting items based on length

Another way to sort items could be from shortest to longest and vice versa. 

Sort the `list` of `words` seen above from the shortest to the longest word

```python
words = ['This', 'is', 'a', 'list', 'with', 'words']

short_long = sorted(words, key=len)
print(short_long)
```

## Sorting a str

- Sorting can be performed on a `str` which is no more than a sequence of characters

```python
strng = 'hello world'
sorted_strng = sorted(strng)
print(sorted_strng)
```

- Notice that even the instance of a whitespace has an ordinal value and is sorted accordingly in the `str`

- Also, it is important to note that a `list` data type was returned when utilizing the `sorted()` function

All of the same rules around character/ordinal value sorting still apply when sorting strings and in order to sort a string in actual alphabetical order, especially when capital letters are involved, you still need to enforce the use of the `key`

```python
strng = 'Hello World'
sorted_strng = sorted(strng)
print(sorted_strng)
```

**versus:**

```python
strng = 'Hello World'
sorted_strng = sorted(strng,key=str.lower)
print(sorted_strng)
```

## Making a unique key function by which to sort items

Because Python allows users to define their own unique functions, users can apply those functions to the `key` parameter of the `sorted()` function to perform unique sorting needs.

```python
ports_monitored = [('HTTPS', 443),('SSH', 22),('FTP-data', 20), ('HTTP', 80)]

sorted_ports = sorted(ports_monitored)
print(sorted_ports)   # by default it is going to sort the tuples inside the list based on the ordinal values of the characters found in index 0
```

In order to sort the `ports_monitored` by the actual port number found in each tuple we need to build a unique function that isolates the exact item we want to sort it by

```python
ports_monitored = [('HTTPS', 443),('SSH', 22),('FTP-data', 20), ('HTTP', 80)]

def find_port(tup):  #this function is designed to take in 1 item at a time and isolate whatever is found in the [1] index position
    return tup[1]

sorted_by_ports = sorted(ports_monitored,key=find_port)
print(sorted_by_ports)
```

While we can define a function like `find_port`, we will probably only use it once. So instead of defining a function that fills a space in memory, let's use a lamdba function:

```python
ports_monitored = [('HTTPS', 443),('SSH', 22),('FTP-data', 20), ('HTTP', 80)]

sorted_by_ports = sorted(ports_monitored,key=lambda x: x[1])
print(sorted_by_ports)
```

```python
bListOfTuples = list(zip(random.sample(range(1,100),10), random.sample('abcdefghijklmnopqrstuvwxyz',10)))
print((bListOfTuples))
print(sorted(bListOfTuples))
print(sorted(bListOfTuples, key=lambda aTup: aTup[1]))
```

## Sorting Dictionaries
- The only way to sort a `dictionary` is to convert the keys or values to a `list` and call the sort method to sort the `list`.

- A sorted list of the keys will be returned by default. You can specify the `items()` or `values()` if you wish to have them sorted as well.

Isolate the `key` in the `dictionary` found below and sort them

```python
numbers = {'one':1, 'two':2, 'three':3}
sorted_keys = sorted(numbers.keys())
print(sorted_keys)
```


---

[⬆️ Back to Module Index](../README.md)
