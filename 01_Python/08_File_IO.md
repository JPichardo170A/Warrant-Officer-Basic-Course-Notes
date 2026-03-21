# 📁 File Input/Output

*Module 01 — Python | Day 5*

---

## 🎯 Learning Objectives

- Open files with `open()` in various modes (`r`, `w`, `a`, `x`)
- Read files with `read()`, `readline()`, and `readlines()`
- Write to files with `write()` and `writelines()`
- Use the `with` statement for automatic file closing
- Navigate files with `seek()` and `tell()`

---

# File Overview

To handle files in Python, there are three key things to know:

```open()```
```read()``` or ```write()```
```close()```

```python
# open file in write mode, and store it in a variable
file_obj = open("info.txt", "w")

# write to a file
file_obj.write("Line1 Hello\nLine2 World\nLine3 Another\nLine4 Final")

# close the file
file_obj.close()
```

## Opening and Closing Files
- Performing file input/output operations is, arguably, one of the most important features of a programming language.

- Fortunately, Python has language features that greatly facilitate this important task.

- Use the `open()` function to prepare a file for I/O operations.

### Specify:

- File name as string or path expression. The name/path may be absolute or relative.

- Remember, for Windows OS, the \\ is the path separator versus the / which is the path separator for Linux/Mac.

### File Modes
Mode options allow for the ability to read or write to a file. Some modes require two characters while others only require one. The list below shows all the available mode options:

|Keyword | Description |
| :----- | :-----------|
| r | reads from file, this is used by default | 
| w | writes to a file, will overwrite if file exists |
| a | appends to a file, will not overwrite |
| x | creates a file if it does not exist |
| b | allows for reading or writing to binary |
| t | text mde, can read or write |
| w+ or r+ | file must eist, can read and write |


### How to open and close a file in python 
#### To open a file, use the `open()` built-in function. Put either the file or the path in the parentheses, followed by the mode. Below are examples of opening files and storing them in a variable.

#### The `close()` method closes the file and may be explicitly coded as shown in the listing below.

```python
# Create a file object and opens file in write mode
file_obj = open("info2.txt", "w")
file_obj.close()

# Create a file object and open file in read mode
file_obj = open("info2.txt", "r")
file_obj.close()

# Create a file object and opens file in append mode
file_obj = open("info2.txt", "a")
file_obj.close()

# Create a file object and opens file in write binary mode
file_obj = open("info.dat", "wb")
file_obj.close()

# Create a file object and opens file in read binary mode
file_obj = open("info.dat", "rb")
file_obj.close()

# Create a file object and opens file in append binary mode
file_obj = open("info.dat", "ab")
file_obj.close()
```

## Reading Files 
To read one line at a time, open the file and use the ```read()``` method<br>
```read()``` returns a string of all the contents from file

```python
# open file in read mode, and store it in a variable
file_obj = open("info.txt", "r")

# reading from a file
file_content = file_obj.read()
print(file_content)

# close the file
file_obj.close()
```

```readline()``` reads one line of the text file at a time.

```python
# open file in read mode, and store it in a variable
file_obj = open("info.txt", "r")

# reading from a file
file_content = file_obj.readline()
print(file_content)

# close the file
file_obj.close()
```

`with` Keyword automatically closes file

```python
# files must be closed after using it
# the with statement ensures the file is closed without an explicit close()

with open('test.txt', 'r') as fp:
    pass
```

The ```readlines()``` method returns the whole text file in the form of a list!

```python
# Opening info.txt and reading the lines
with open("info.txt") as file_obj:
   file_content = file_obj.readlines()
   print(file_content)
```

- When using the readlines() method, it returns a list of strings from the file including the new line character. 
- There are other ways and methods to return a list of lines from a file without the new line character:

```python
# Opening info.txt and reading the lines without the new line character
with open("info.txt") as file_obj:
   file_content = file_obj.read()
   file_lines = file_content.splitlines()
   print(file_lines)
   # The splitlines() method splits a string into a list. The splitting is done at line breaks.
```

- Additionally, obtaining words from a file is a practice that is often done.
- In order to do this, use the _io.TextIOWrapper method of read() to return a string. From there, we use string.split() with a space as an argument to return a list of words.

```python
# Opening info.txt and create a list of words
with open("info.txt") as file_obj:
   file_content = file_obj.read()
   words = file_content.split(" ")
   print(words)

with open("info.txt") as file_obj:
   file_content = file_obj.read().replace('\n', ' ')
   words = file_content.split(" ")
   print(words)
```

file objects are iterable

```python
# we can also iterate through a file object to get one line on each iteration

with open('info.txt', 'r') as fp:
    for line in fp:
        print(line.strip('\n'))
```

## Writing Text to a File 

```write()``` - writes a single string to a file<br>
```writelines()``` - writes a list of strings to a file, does not add newlines

### .write Method

#### 'w' mode when opening file

```python
# write() - method for writing a string to a file; file must have been opened in a mode supporting write

# 'w' mode will create the file if it does not exist; if it exists it will truncate the file
data = [("California", 39937489, "Sacramento"),
       ("Texas", 29472295, "Austin"),
       ("Florida", 21992985, "Tallahassee")]

with open("info.txt", "w") as data_obj:
       for state, population, capital in data:
           data_obj.write(f'{state}, {population}, {capital}\n')
```

Note: If info.txt was already created, using 'w' mode will overwrite the file. Using 'a' will not overwrite the file, it will add the contents to the end of the file.

#### 'a' mode when opening file

```python
# 'a' mode will create the file if it does not exist; if it exists it will append to the end of the file

with open('info.txt', 'a') as fp:
    fp.write('Here is another line\n')

with open('info.txt', 'r') as fp:
    print(fp.read())
```

### .writelines Method

```python
# writelines() - method for writing a list to a file

data = [("California", 39937489, "Sacramento"),
       ("Texas", 29472295, "Austin"),
       ("Florida", 21992985, "Tallahassee")]

linesToWrite = []
for state, population, capital in data:
    linesToWrite.append(f'{state}, {population}, {capital}\n')

with open('info.txt', 'w') as fp:
    fp.writelines(linesToWrite)

with open('info.txt', 'r') as fp:
    print(fp.read())
```

## Seek and Tell 
- The file object methods ```seek()``` and ```tell()``` allow a program to navigate the read/write pointer in a file and to report on the current position of the read/write pointer.

- ```seek( pos )``` to position file at position pos for next I/O operation.

- For example, `seek(0)` positions the read/write pointer to the beginning of the file. The `seek()` method takes an optional second parameter called `whence` which is an integer specifying where to start seeking from, however it only properly works when opening in `rb` mode.

- The `tell()` method returns an integer specifying the current position within the file of the read/write pointer.

```python
# tell() - method that returns the current read/write position in the file
# seek() - method that moves read/write position to seek argument

with open('info.txt', 'r') as fp:
    print(fp.read(5))
    print(fp.tell())
    fp.seek(0)
    print(fp.read(11))
    print(fp.tell())
    fp.seek(0)
    print(fp.read())
    print(fp.tell())
```

### multi-mode

```python
# open a file in multi-mode
# 'r+' - reading and writing with no truncation (file must exist)
# 'w+' - reading and writing but file is truncated (file need not exist)
# 'a+' - reading and writing with no truncation (cursor is at end of the file)

with open('info.txt', 'r+') as fp:
    print(fp.tell())
    print(fp.read())

with open('info.txt', 'a+') as fp:
    print(fp.tell())
    print(fp.read())
```

### open two files with one with statement

```python
# copy one file to another using one with statatemnt

with open('info.txt', 'r') as inFile, open('copyInfo.txt', 'w') as outFile:
    contents = inFile.read()
    outFile.write(contents)

with open('copyInfo.txt', 'r') as fp:
    print(fp.read())
```

### continually write user input to file until user enters empty string

```python
# write user input to file until empty string

with open('userInput.txt', 'w') as fp:
    ui = input('Enter some characters or simply enter to quit: ')
    while ui:
        fp.write(ui + '\n')
        ui = input('Enter some characters or simply enter to quit: ')

with open('userInput.txt', 'r') as fp:
    print(fp.read())
```


---

[⬆️ Back to Module Index](../README.md)
