# 🐛 Debugging

*Module 01 — Python | Day 7*

---

## 🎯 Learning Objectives

- Use `try`/`except` blocks for error handling
- Access error information from exceptions
- Use `else` and `finally` in exception handling
- Handle multiple exception types
- Raise custom exceptions with `raise`

---

# Debugging
## Try and Except

- try: test code

- except: handles an error

- else: continues when no error

- finally: continues to execute without caring about the try and except

```python
try:						               
  x = 1/0
except:
   print("Cannot divide by zero")	
else:
   print(x)
finally:
   print("this is a finally block!")
```

### try / except

```python
# Error handling with try/except

try:
    5/0
except:
    print('there was an error')

print('this line will execute')
```

### Access the error information

```python
# More error handling - access the error

try:
    5/0
except Exception as err:
    print(f'Error: {err}')

print('this line will execute')
```

### else block of try/except

```python
# More error handling - the else block

try:
    5/1
except Exception as err:
    print(f'Error: {err}')
else:
    print('There was no error')
```

### finally block of try/except

```python
# More error handling - the finally block

a = 5
b = 1

try:
    a/b
except Exception as err:
    print(f'Error: {err}')
else:
    print('There was no error')
finally:
    print('This line will always execute')
```

### demo

```python
import random

def func1(a,b):
    try:
        print(a/b)
    except Exception as err:
        print(f'{err} in {func1.__name__}')

def func2(b):
    try:
        print(int(b))
    except Exception as err:
        print(f'{err} in {func2.__name__}')


func1(random.randint(1,10),random.randint(0,2))
func2(''.join(list(random.sample('1234567890ab',3))))
```

## Raising and Assertions

### Raising Exceptions
- When code executes and the code is not valid, it will raise an error. 
- When programming, programmers have the ability to raise an error in their code.
- This is a good way to debug functions when there are errors being produced in the function.
- The output of a raised exception is an error message.
- To Raise Exception, use the raise keyword, followed by the Exception() function, followed by a string in the Exception() 
- ``` raise Exception(“Error Message”) ```

```python
def fun(num):							 
   if num < -1:
       raise Exception("Number needs to be above 0")	
   else:
       print("Number is not negative")				

fun(-5)
```

### Assertions: 
- Are a sanity check that make sure your program is not doing something wrong.

- Use assert keyword, a condition, and a string 
	
- ``` assert <condition>, “string” ```

```python
num = -5
assert num == -5, "Number needs to be -5"

num = 5
assert num == -5, "Number needs to be -5"
```

## Logging

- Logging helps programmers understand what is happening in their code and what the code is doing. Typically, a programmer will use the print() function to test certain aspects of their program. Using the logging module can prevent having multiple print statements in their program.

- To enable logging, use import logging to import the logging module

- ``` basicConfig() ``` function is needed. This allows one to specify the details of the logs

```python
import logging

logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s - %(levelname)s - %(message)s')
```

- **Level** allows one to define the level of logging they desire

- **format** allows one to define what format they want the log to look like


### Levels of logging
- Debug: logging.debug(); used for details about code. 

- Info: logging.info(); used for events that are general.

- Warning: logging.warning(): used to show a problem. This is the default level. Will write to stdout.

- error: logging.error(): used to show errors. Will write to stdout.

- critical: logging.critical(): used to show fatal errors. Will write to stdout.

```python
import logging

logging.debug('debug')
logging.info('info')
logging.warning('warning')      
logging.error('error')          
logging.critical('critical')
```

```python
import logging

# ‘level=logging.<level>’ can be changed to the level of logging you want to capture.
#  the ‘basicConfig’ function can only be run ONCE! This is typically run in the beginning.
logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s - %(levelname)s - %(message)s')

logging.debug("About to enter function")
def fun():
   for i in range(1,11):
       logging.debug(f"i is: {i}")
fun()
logging.debug("End of function")
```

### Logging to a File

```python
# try this is a script instead of jupyter notebook

import logging

logging.basicConfig(filename="logs.txt", filemode='w', format=' %(asctime)s - %(levelname)s - %(message)s')

logging.warning("About to enter function")
def fun():
   for i in range(1,11):
       logging.warning(f"i is: {i}")


fun()
logging.warning("End of function")
```


---

[⬆️ Back to Module Index](../README.md)
