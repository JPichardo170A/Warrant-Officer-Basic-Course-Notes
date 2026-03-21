# 📖 Dictionaries & Sets

*Module 01 — Python | Day 6*

---

## 🎯 Learning Objectives

- Create and manipulate dictionaries with `key:value` pairs
- Access, add, update, and remove dictionary entries
- Loop through dictionaries using `.keys()`, `.values()`, `.items()`
- Work with sets: `add`, `remove`, `union`, `intersection`, `difference`
- Use `in` and `not in` for membership testing

---

# Dictionaries
- A `dict()` (dictionary) is a collection of entries.
    - Since Python 3.7, dictionaries maintain their order of entry, but the collection is not ordered
 
- Each entry contains a `key:value` pair.
   - Think of Webster's dictionary. The word is the `key` and the definition is the `value`

- Dictionaries maintain their order of insertion - Last In, First Out (LIFO). 
 
- Dictionary keys have to be both unique and hashable. In other words a `key` can NOT be duplicated

More on dictionaries can be found at: 

- [W3Schools](https://www.w3schools.com/python/python_dictionaries.asp)
- [Python Docs](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)

## Creating Dictionaries 

- Two ways to create a dictionary, using `dict()` or `{}`

```python
# Creating an empty dictionary
dictionary = dict()
dictionary2 = {}
print(type(dictionary))
print(type(dictionary2))
```

```python
# Example 1 (using {}):
names = {"key_1": "Bill", "key_2":"Jill", "key_3":"Gill"}
numbers = {1:1, 2:2, 3:3}
```

```python
# Example 2 (using dict()):
also_names = dict(key_1 = "Bill", key_2 = "Jill", key_3 = "Gill")
also_numbers = dict(one = 1, two = 2, three = 3)  # NOTE: using this process will NOT allow you to assign integers as keys
```

## Acessing Items In A Dicionary 

- The `key` is the primary means of access when using a dictionary

***Consider this:*** Would you open Webster's dictionary looking for a specific definition (`value`) in order to find the word (`key`) that it is assigned to? Or, would you look up a specific word (`key`) to find the definition (`value`) it is assigned to?

Access the names dictionary and print the name 'Bill'

```python
names = {'key_1': 'Bill', 'key_2': 'Jill', 'key_3': 'Gill'}

print(names['key_1'])
```

Now access the dictionary and save the name 'Jill' to the variable: `name_2`

```python
name_2 = names['key_2']
print(name_2)
```

- Dictionaries also have a `.get()` method that can be used to retrieve the value for a given key.
 
   - ` dict_name.get(key, default) `
 
   - If a value for default is not provided, the `None` object will be returned.

#### .get Method

```python
print(names.get('key_1'))

#access a key that does not exist
print(names.get('key_10'))

#provide a unique 'error message' to the .get()
print(names.get('key_10','Key does not exist'))
```

## Finding Keys/Values
- The `in` and `not in` operators can be used to determine if a specific `key` or `value` exists in the `dictionary`.
 
- Both operators will return a `True` or `False` value.
 
- When used with the entire `dictionary`, the operators search for the `value` in the `keys` of the `dictionary`.
 
- The view returned by the values method can be used to search for a `value` in the values of the dictionary.

```python
numbers = {'one':1, 'two':2, 'three':3}

# Using in and not in
print("one" in numbers)	
#output:  True			
print("one" not in numbers)
```

## Adding and Updating Key:Value Pairs
- Dictionaries are designed as a data structure that provide fast look-ups into the structure by key. Sub-script notation can be used to add new key/value pairs and to modify existing values for a given key.
 
- `dict_name[key]` will retrieve the value associated to the given key.
 
- If the key does not exist, a `KeyError` exception is raised

- `dict_name[key] = value` will either add a new `key`:`value` pair, or modify the `value` associated to the given `key`.
 
Using the `names` dictionary, add two more keys and names

```python
names['key_4'] = 'Phil'
print(names)
names['key_5'] = 'Will'
print(names)
```

Update the `value` of `key_1` to be the name 'Hill'

```python
names['key_1'] = 'Hill'
print(names)
```

## Removing Key Values/Pairs
- Removing elements from a dictionary can be done by using the `del` keyword and through the `pop()`, `popitem()` methods.

- `del dict_name[key]` removes the specified key/value pair from the dictionary, the key/value pair is not returned.
 
- `del dict_name` deletes the entire dictionary.
 
- The general syntax for the `pop()` method is as follows: `value_variable = dict_name.pop(key, default)`
 
   - `Key` represents the actual key of the key/value pair to attempt to remove.
 
   - `Default` represents an optional value to return if key does not exist. If left blank and the key does not exist in the dictionary a `KeyError` will be raised.
 
- The general syntax for the `popitem()` method is as follows. `a_tuple = dict_name.popitem()`
 
   - The `popitem()` method takes NO arguments. It simply removes and returns the last `key`/`value` pair as a `tuple`, but raises a `KeyError` if obj is empty.
 
- A tuple is an immutable collection of ordered elements.
 
Use the names and numbers dictionaries to practice using the `del` keyword and `.pop()` and `.popitem()` methods.

- Pop key_1 off of names

```python
names = {'key_1': 'Bill', 'key_2': 'Jill', 'key_3': 'Gill', 'key_4': 'Phil', 'key_5': 'Will'}
numbers = {1:1, 2:2, 3:3}

remove_key_1 = names.pop("key_1",None)	#You can use the None obj						
print(names)
```

- Pop something that does not exist

```python
remove_key_10 = names.pop('key_10', 'Key does not exist') #You can use a unique 'error message'
print(remove_key_10)
```

- Use `popitem()` to remove the last `key:value` pair in the dictionary until nothing exists in the dictionary

```python
remove_3 = numbers.popitem()
print(numbers)	

remove_2 = numbers.popitem()
print(numbers)	

remove_1 = numbers.popitem()
print(numbers)	

remove_0 = numbers.popitem()
```

## Dictionary Methods - Continued

- When there is a need to work with all `key/value` pairs in a dictionary, the following methods are useful.
 
- The `.keys()` method returns a view of the dictionary keys.
 
- The `.values()` method returns a view of the dictionary values.
 
- The `.items()` method returns a view of the dictionary items.
 
- Each item in the view returned by `.items()` is a 2 item `tuple` consisting of a `key` and a `value`.
 
- Each of the views can also be converted to a `list` or a `tuple` by passing the view to a `list()` or `tuple()` constructor.

<br>

Create a new `dictionary` that uses state abbreviations as the `key` and the full name as the `value`.

### .keys()

```python
romanNumerals = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
print(romanNumerals.keys())

# .keys() returns a dict_keys object
print(type(romanNumerals.keys()))

# convert dict_keys object to a list
print(list(romanNumerals.keys()))
print(type(list(romanNumerals.keys())))
```

### .values()

```python
# values() - method that returns a dict_values object
print(type(romanNumerals.values()))

print(romanNumerals.values())
```

### .items()

```python
# items() - method that returns a dict_items object (each value is a tuple of the form (key, value))
print(type(romanNumerals.items()))

print(romanNumerals.items())
```

Reminder that none of the three above objects are lists; to use as a list you must convert them to a list

```python
print(type(romanNumerals.keys()))
print(type(list(romanNumerals.keys())))

print(type((romanNumerals.values())))
print(type(list(romanNumerals.values())))

print(type(romanNumerals.items()))
print(type(list(romanNumerals.items())))
```

## Looping/Iterating Through A Dictionary

Use the `romanNumerals` dictionary to practice iterating over dictionaries.

```python
for each_thing in romanNumerals:
    print(each_thing)
```

**NOTICE** that the `key` is returned. It can be helpful to change `each_thing` to the word `key`. `key` is not a reserved keyword for Python and it will not interfere with any dictionary operations.  Also note that iterating over a dictionary is functionally equivalent to iterating over a `.keys()` object.

```python
for key in romanNumerals.keys():
    print(key)
```

Loop over the dictionary and print only the value

```python
for value in romanNumerals.values():
    print(value)
```

Loop over the dictionary and print the key, value pair together

```python
for item in romanNumerals.items():
    print(item)
```

**NOTICE** this output is a `tuple` consisting of the `key` and `value`

There are many different ways to accomplish the same outcome. The following examples show how many different ways you can loop over a dictionary and print the following `str`: 'The roman numeral {roman numeral} has the decimal value: {decimal value}.'

- Using only the `key`

```python
for key in romanNumerals:
    print(f'The roman numeral {key} has the decimal value {romanNumerals[key]}.')
```

- Using the pairs of items

```python
for item in romanNumerals.items():
    print(f'The roman numeral {item[0]} has the decimal value {item[1]}.')
```

- Use `.items()` again, but with dynamic variable declaration

```python
for key, value in romanNumerals.items():
    print(f'The romman numeral {key} has the decimal value {value}.')
```

# Sets

## About Sets

- Sets are not ordered, do not allow for duplicates, and all items must be immutable. 
- To create a set use `set() `
- ` s = set() `
- Sets also allow for different data types.

More on sets can be found at: 

- [W3Schools](https://www.w3schools.com/python/python_sets.asp)
- [Python Docs](https://docs.python.org/3/tutorial/datastructures.html#sets)

```python
# creating an empty set
aSet = {} # Can't do it this way!
print(type(aSet))

aSet = set()
print(type(aSet))

s = {1, 2, 3, False, "String"}
print(s)

#turning a tuple into a set
s_two = set((1, 2, 3, False, "String"))
print(s_two)
```

## Adding items to a set
- `set_name.add()` - Requires only 1 argument and adds the item into the `set` in no particular order

```python
s = {1, 2, 3, False, "String"}

s.add(10)
print(s)

s.add(50)
print(s)
```

Add an item to the set that already exists. Will it create a duplicate or an error???

```python
s.add(50)
print(s)
```

No errors are raised and a `set` doesn't allow duplicates, it simply executes the line of code and continues on to the next line of your code.

## Removing items from a set

- `set_name.remove()` Requires only 1 argument and removes the item if found in the `set`. If it is not found a `KeyError` will be returned.

```python
s = {False, 1, 2, 3, 50, 10, 'String'}
s.remove(2)
print(s)
```

- `set_name.discard()` Requires only 1 argument and removes the item if found in the `set`, but will not cause an error if the item is not in the set.

```python
s = {False, 1, 2, 3, 50, 10, 'String'}
s.discard(2)
print(s)
s.discard(2)
print(s)
```

## Set Methods - Continued

- `set_name_1.difference(set_name_2)` - Accepts multiple arguments and returns what is found in set_name_1 that is *not* found in any of the sets provided in the arguments

- `set_name_1.intersection(set_name_2)` - Accepts multiple arguments and returns what is found in ALL of the sets provided.

- `set_name_1.union(set_name_2)` - Accepts multiple arguments and returns a compiled set of ALL items found in all of the sets provided.

|  **Scenario:** |
|---|
| The following are `set` objects contain collections of information that the Brigade security office uses to track A and B Company's soldiers and their clearance level.|

```python
A_company = {'Nelson', 'Scott', 'Miller', 'King', 'Walker', 'Green', 'Jones', 'Hall', 'Campbell'}
B_company = {'Smith', 'Holly', 'Taylor', 'Martin', 'Jackson', 'Lewis', 'Lee', 'Moore'}
secret_clearance = {'Smith', 'Taylor', 'Lewis', 'Lee', 'Moore', 'Miller', 'Walker', 'Green', 'Jones', 'Hall', 'Campbell'}
ts_clearance = {'Taylor', 'Lee', 'Moore', 'Walker', 'Green', 'Campbell'}
```

### .union()
Print a `set` containing ALL the names of people found in A Co and B Co, regardless of their clearance level

```python
# union() method returns the union of set object and set object argument
all_soldiers = A_company.union(B_company)
print(all_soldiers)
```

### .difference()
Who in B Co does NOT have a TS clearance?

```python
# difference() method returns elements in set object that are not in set object argument(s)
B_TS_uncleared = B_company.difference(ts_clearance)
print(B_TS_uncleared)
```

Who in A Co has NO clerance?

```python
# difference() method can take more than one argument
A_uncleared = A_company.difference(secret_clearance,ts_clearance)
print(A_uncleared)
```

### .intersection()
Who in A Co at least has a SECRET clearnace?

```python
# intersection() method returns those elements that are in both the set object and set object argument
A_secret = A_company.intersection(secret_clearance)
print(A_secret)
```

### Combining methods - That's crazy?!
Who in A Co **ONLY** has a SECRET clearance?

```python
A_secret_only = A_company.intersection(secret_clearance).difference(ts_clearance)
print(A_secret_only)
```


---

[⬆️ Back to Module Index](../README.md)
