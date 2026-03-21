# 📋 Lists and Strings

*Module 01 — Python | Day 2*

---

## 🎯 Learning Objectives

- Access items using indexing and nested indexing
- Use list methods: `append`, `insert`, `remove`, `pop`, `extend`, `count`
- Work with string methods: `upper`, `lower`, `split`, `join`, `replace`, `strip`
- Find substrings with `find`, `index`, and `count`
- Validate strings with `is` methods (`isdigit`, `isalpha`, `isalnum`)
- Format strings with f-strings and `str.format()`

---

# Indexing through iterable items

## Access items in a list, tuple, or string using indexing
- Elements in a `list`, `tuple`, and `str` are accessed by their index positions.  		 
    - Index positions are **zero-based** when counting them.
- Elements can be retrieved by using the subscript operator `[]` and identifying the index number as an integer.

```python
# Indexing allows us to access individual items in an ordered collection (string, list, tuple)
# Python uses 0-based indexing: the first time is index 0, the second item is index 1, ...
# Python also allows negative indexing: the last item is index -1, the second to last time is index -2, ...

#          01234
aString = 'hello'
print(aString[0])
print(aString[4])
print(aString[-5])
print(aString[-1])
```

```python
#        0  1  2  3
aList = [5, 6, 7, 8]
#       -4 -3 -2 -1
print(aList[0])
print(aList[3])
print(aList[-4])
print(aList[-1])
```

```python
#          0      1       2       3
aTup = ('one', 'two', 'three', 'four')
#         -4     -3      -2      -1
print(aTup[0])
print(aTup[3])
print(aTup[-4])
print(aTup[-1])
```

What about a `list` inside of a `list`, or a `list` with multiple `str`?

In the following `list` of `str`, how do you access an individual letter?

```python
word_lst = ['cyber','is','so','much','fun']
#print the letter 'o' in the word 'so' found in the list
print(word_lst[2][1])
```

```python
lst = [[1,2,3],['4','5','6'],[7,'8',9]]
#print the integer 1
print(lst[0][0])
```

**What happens if you access an index that doesn't exist?**

Attempting to access an index number that exceeds the limits of your `list`/`tuple`/`str` will cause an error

```python
#index:  01234
strng = 'hello'
print(strng[5])
```

# Modifying, and methods of Lists and Tuples

## Modify items in a list using indexing

Lists are *mutable* and can be modified dynamically

```python
# Mutability
# list is an ordered sequence that is mutable

a = [1,2,3,4,5]
print(a)

# modify a list with item assignment
a[0] = 9
print(a)
```

- Many types are immutable meaning they cannot be changed
- Some obvious immutable types are int, float, and bool
- While str and tuple are ordered sequences, they are immutable

```python
# cannot modify a string with item assignment

aStr = 'hello'
print(aStr)
aStr[0] = 'z'
```

```python
# cannot modify a tuple with item assignment

aTup = (1, 2, 3, 4)
print(aTup)
aTup[0] = 5
```

## List Methods

The most commonly used methods are listed below, however, there are many more methods available. To learn more about other list methods you can visit both of the following resources:

- Using `help(list)` in your IDE

- [Python Docs - More on Lists](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)

- [W3Schools](https://www.w3schools.com/python/python_lists_methods.asp)


    - `append(item)` - Adds a new element to the end of the list, increasing the length by one.

    - `count(item)` - Returns the total number of times the item specified is found inside the list.

    - `extend(iterable)` - Adds each element from the iterable passed in as new elements to the end of the list, increasing the length by the number of items in the iterable.

    - `insert(index, item)` - Adds the specified item at the specified index position, shifting existing elements to make room for the new item, increasing the length by one.

    - `pop(index)` - Deletes the element at the specified index or the end of the list if no index is provided, decreasing the length by one.

    - `remove(value)` - Deletes the first instance of the specified value in the list, decreasing the length by one.

**Methods in action:**


Adding an item to the `list` (three ways):

### .append Method

```python
# append() method - add an item to the end of the list
aList = [1,2,3,4]
print(aList)
aList.append(5)
print(aList)
```

### .extend Method

```python
# extend Method - add one list onto the end of another list
aList = [1,2,3,4]
bList = [5,6,7,8]
aList.extend(bList)
print(aList)

# extend is functionally the same as concatenating one list to another
cList = [1,2,3,4]
dList = [5,6,7,8]
cList += dList
print(cList)
```

### .insert Method

```python
# insert Method - insert a value into a list at an index position
lst = [1,2,3]
lst.insert(0,'zero')
print(lst)
```

Removing items from a `list` (three ways):

### .remove Method

```python
# remove() method - removes first occurrence of item provided by argument; if item is not in list there will be an error
aList = [1,2,2,3]
aList.remove(2)
print(aList)
```

### del keyword

```python
lst = [1,2,3]
del lst[0]  #NOTE:  del is a keyword used to delete items from the list
print(lst)
```

### .pop Method

```python
# pop() Method - removes and returns item at index provided as argument (default is last item)
aList = [1,2,3,4]
a = aList.pop(0)
print(a)
print(aList)
b = aList.pop()
print(b)
print(aList)
```

### .count Method

```python
# count() method - returns the number of occurences of the argument in the list
aList = [1,4,4,3]
print(aList.count(1))
print(aList.count(4))
print(aList.count(5))
```

## Tuple Methods

Tuples are NOT mutable and cannot be dynamically changed using methods. Tuples do still have some helpful methods.

- `count(item)` - Returns the total number of times the item specified is found inside the tuple

- `index(item)` - Returns the index position of the item

### .count Method

```python
tup = (9,8,7,9,8,7)
tup.count(9)
nine_count = tup.count(9)
print(nine_count)
```

### .index Method

```python
tup = (1,2,3)
tup.index(2)  #NOTE: The returned index number can be saved into a variable if needed
where_is_2 = tup.index(2)
print(where_is_2)
```

## Make changes to a tuple

While tuples are great at maintaining the integrity of its contents, sometimes a change may need to be made. 

|  **Scenario:** |
|---|
|Joe Smith is being reassigned to Ft. Eisenhower, GA and his record needs to be updated|

```python
soldier_159 = ('Joe','Smith','88M','Ft. Drum, NY')
soldier_159 = list(soldier_159)  #converting to a list to access mutable properties
soldier_159[-1] = 'Ft. Eisenhower, GA'
soldier_159 = tuple(soldier_159)  #converting back to a tuple to 'lockdown' or deny mutability
print(soldier_159)
```

# String Methods
- Strings in Python are an *immutable* sequence of zero or more characters.


- Literal string values may be enclosed in single or double quotes and can span multiple lines in several ways.
    - This is achieved by using the line continuation character \ as the last character.

- Literal strings may also be prefixed with a letter r or R.
    - These are referred to as raw strings and use different rules for backslash escape sequences.

- Strings in Python are represented using a class named `str`.

- The `str` class has an abundance of methods defined within it.
    - Some of the methods return Boolean values such as `True` or `False`.
    - Some methods return a modified **copy** of the string.


- A full listing of the string methods can be found by using: 
    - `help(str)` from the Python interactive shell or your IDE.
    - [W3Schools](https://www.w3schools.com/python/python_strings_methods.asp)
    - [Python Docs](https://docs.python.org/3/library/stdtypes.html#string-methods)

## String Casing methods
- Python provides several methods that can be used to modify the casing of characters in a string.
- ```upper()``` returns a **copy** of the string with all cased characters converted to uppercase.
- ```lower()``` returns a **copy** of the string with all cased characters converted to lowercase letters.
- ```casefold()``` similar to lower(), is stronger, more aggressive, meaning that it will also convert unicode characters into lower case. This method will find more matches when comparing two strings and both are converted using the casefold() method
- ```title()``` returns a **copy** of the string with the first letter of each word in the string in upper case and the rest of the characters in lower case.
- ```capitalize()``` returns a **copy** of the string with the first letter in upper case and the rest of the characters in lower case.

```python
string = "python is fun"                                                        
print("String is now upper:", string.upper()) 
print("String is now lower", string.lower())
print("String is now casefold:", string.casefold())
print("String is now title:", string.title())  
print("String is now capitalized:", string.capitalize())
```

## Finding Substrings

- A variety of methods can be used to find instances of characters or strings within another string.


- `count(s)` will return the number of times the value passed to the method is found within the string.


- `index(s)` will return the index position of the first instance of the value passed to the method.


- `index()` will raise a `ValueError` exception if the value to find is not found within the string


- `find(s)` is similar to index but find will return a -1 when the sub-string is not found rather than raising an exception.


!!! Note "Note"
    that all these methods perform case sensitive searches.

```python
string = "python is fun"
                                
print(string.count("n"))
print(string.index("n")) 
print(string.find("n"))  
print(string.find('z'))
```

## Methods To Create Modified Copies of Strings

- Methods can be used to clean up data or to replace or remove unwanted characters.

**It is important to note that all of these methods will only return a modified *copy* of your string UNLESS you assign it to a variable**

- `strip()` will remove any leading and trailing whitespace from the string.


- `lstrip()` will remove any leading whitespace (whitespace on the left)


- `rstrip()` will remove any trailing whitespace (whitespace on the right)


- `replace(old, new)` replaces all instances of the first parameter with all instances of the second parameter.
	- An optional third parameter can be used to specify the number of times the replacement is to be made.

### .strip Method

```python
# strip() method - remove characters from left and right side of string; by default removes whitespace

aStr = '    characters     '
print(aStr)

print(aStr.strip())

# optional argument is all characters to be removed from left and right side of string
bStr = 'www.example.com'
print(bStr.strip('w.com'))
```

### .replace Method

```python
# replace() method - create a copy of the string where first character is replaced by second character

aStr = '192.168.68.101'
print(aStr.replace('.', '+'))

# aStr not modified
print(aStr)
```

## Splitting and Joining Strings Working With Lists

Strings are immutable objects which can make them difficult to easily alter. Let's look at some methods available to break apart strings, make some alterations if necessary, and then join them back together.

- `.split()` - Returns a `list` of the original string elements separated by index by the item specified; default value is whitespace
- It is important to note that the item provided to the `.split()` method will be removed completely from the string

### .split Method

```python
# split() method - split a string into a list based on a delimiter

aStr = 'This is a sentence'
print(aStr.split(' '))
print(aStr.split())     # by default the delimiter is the ' ' character

csvString = 'This,might,be,what,a,csv,file,looks,like'
print(csvString.split(','))

aMACaddress = '07:bb:21:3d:a9:29'
print(aMACaddress.split(':'))

anIPaddress = '192.168.68.101'
print(anIPaddress.split('.'))

full_name = 'Joe Smith'
fname = full_name.split()[0]
lname = full_name.split()[1]
print(fname)
print(lname)
```

### .join Method

```python
# join() method - constuct a string from a list where each list element is separated by the given string

# string are immutable, but given a string how could I 'make changes' to it?

myStr = 'line tree' # want to change it to 'pine tree'
print(myStr)

myStrList = list(myStr)
print(myStrList)

myStrList[0] = 'p'
print(myStrList)

myStr = ''.join(myStrList)
print(myStr)
```

```python
# Get the next IP address
anIPaddress = '192.168.68.101'
print(anIPaddress)

anIPaddressList = anIPaddress.split('.')
print(anIPaddressList)
anIPaddressList[-1] = str(int(anIPaddressList[-1])+1)
print(anIPaddressList)

anIPaddressReassembled = '.'.join(anIPaddressList)
print(anIPaddressReassembled)
```

```python
# 'jello' to 'hello'
strng = 'jello'
str_lst = list(strng)
print(str_lst)
new_str = ''.join(str_lst)
print(new_str)
```

# is METHODS for Strings

- Methods can be used to to validate if a string contains a certain set of characters
- When the method validates, it will return either True or False

### The methods are:
-  `isdigit()`: will return `True` if all characters are digits
-  `islower()`: will return `True` if all characters are lowercase
-  `isupper()`: will return `True` if all characters are uppercase
-  `isalnum()`: will return `True` if all characters are alphanumeric

```python
# some boolean string methods - returns True or False

aStr = 'word'
print(aStr.isalpha())
print(aStr.islower())
print(aStr.isupper())
print(aStr.isdigit())
```

# Escape Characters
| sequence | Character/Meaning |
| :------- | :---------------- |
| \newline | Ignored           |
| \\       | Bckslash          |
| \'       | Single Quote      |
| \"       | Double Quote      |
| \a       | ASCII Bell(Bel)   |
| \b       | Backspace         |
| \f       | form feed         | 
| \n       | newline/Line feed |
| \r       | Carriage Return   |
| \t       | Horizontal Tab    |
| \v       | Vertical Tab      |
| \ooo     | ASCII Character(octal value ooo) |
| \xhhh    | ASCII Character (Hex Value hhh)  |
| \uxxxx   | Unicode Character with 16-bit hex alue xxxx |
| \Uxxxxxxx | Unicode Character with 32-bit hex value xxxxxxx |

```python
single_quote = "This is a \'single quote\'" # The string will escape char for a single quote
print(single_quote)

new_line = "This: \n will produce a newline." # The string will produce a newline at the end of it
print(new_line)

tab = "This is a \t tab" # The string will add a tab
print(tab)

chess_piece = "\U0000265F" # Use unicode to create a chess piece
print(chess_piece)
```

```python
print("Strings are \'easy\' in Python")                     

print(r"Strings are \'easy\' in Python")                    

print("Strings are \x27easy\x27 in Python")                 

print('\U0000265A','\U0000265B','\U0000265C','\U0000265D','\U0000265E')
```

# String Formating

## f-string

- Python has several ways to format the output rather than just printing space separated values.


- The newest and easiest way to format a string for output in Python uses formatted string literals or f-strings.


- Beginning with Python 3.6, f-strings are available for output formatting.


- To use a formatted string literal, begin the `str` with f or F before the opening quotation mark.


- This can be used in front of single, double, or triple quotation marks.


- Inside the string, the programmer adds braces to hold values {  }

```python
coding_language = "Python"
print(f'{coding_language} is fun')
```

- A programmer can define and merge f-strings to create a multi-line f-string.


- Notice that the `{name}` placeholder, or field can be repeated. Python evaluates the fields in the braces as Python expressions and looks for variables to match.


- The order of the fields does not matter and as stated earlier, a field can contain any valid Python expression. It is important to include the f or F in front of each line.

```python
coding_language = "Python"
audience = "Students"

long_string = f"{coding_language} is fun. {audience} seem to enjoy learning {coding_language}"

print(long_string)
```

- When using f-strings the programmer can place curly braces in a literal string.


- The curly braces can contain a Python expression.


- Additionally, the programmer can specify additional formatting details for the result of the Python expression.


- A format specifier can be appended to the field after a colon : and inside the curly braces.


- Backslashes are not allowed within the formatting field and will cause a syntax error!


| Type |  Meaning |
| :----| :-------- |
| s  | String format. This is the default type for strings and may be omitted. |
| none | The same as 's'. |
| b  | Binary Format. The Number is display as base 2. |
| c  | Character. Converts the integer to a Unicode Character. |
| d  | Decimal Integer. This converts the number to base 10.   | 
| x or X | Hex format. Display the number in base 16. The case of the hex number will match the case of the specifier. |
| f | Fixed point number. Displays the number with a decimal point. Default precision is 6. |
| % | percentage. Multiplies the number by 100 and displays in fixed ('f') fromat with a percent sign. |

```python
PI = 3.14159
print(f"PI is now 2 decimal places: {PI:.2f}") #  this will show 2 digits after the decimal

PI = 3.14159
print(f"PI is now 4 decimal places: {PI:.4f}") #NOTE rounding took place in the string formatting

num = .5
print(f"num is now a percentage: {num:%}") 

print(f"num is now 2 decimal places: {num:.2%}")
```

## .format Method

- `format()` is a method to be used with `str`.

- Much like f-strings, the `str.format()` method uses curly braces in a template string to mark where the output should be replaced.

- The syntax is to create a string literal with fields marked with curly braces {} where the programmer wants the output to appear.

```python
# string methods (a method is a function that works on specific object types)
# format() method
name = 'Smilla'
pet = 'dog'
myString = 'I have a {} whose name is {}.'.format(pet, name)
print(myString)

pi = 3.14159
aStr = 'Pi rounded to four decimal places is {:.4f}.'.format(pi)
print(aStr)

# alternately can use f-strings
myString = f'I have a {pet} whose name is {name}.'
print(myString)

aStr = f'Pi rounded to four decimal places is {pi:.4f}.'
print(aStr)
```


---

[⬆️ Back to Module Index](../README.md)
