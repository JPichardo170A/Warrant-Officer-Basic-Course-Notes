# 🧮 Conditional Expressions

*Module 01 — Python | Day 3*

---

## 🎯 Learning Objectives

- Use relational operators (`<`, `>`, `==`, `!=`, `is`)
- Apply logical operators (`and`, `or`, `not`)
- Use membership operators (`in`, `not in`)
- Write `if`, `elif`, and `else` conditional blocks
- Avoid common logic errors in conditional chains

---

# RELATIONAL VS. LOGICAL VS. MEMBERSHIP OPERATORS

- The relational, logical, and membership operators yield results of either `True` or `False`.

- `True`: Any non-zero / non-empty value.

- `False`: 0, Empty sets, dictionaries, tuples, or lists, empty strings, none.


## Relational / Comparison Operators

| Operator | Meaning |
| :------- | :------ |
| <        | Strictly Less than |
| <=       | Less than or Equal |
| >        | Strictly Greater Than |
| >=       | Greater than or Equal |
| ==       | Equal                 |
| !=       | Not Equal             | 
| is       | Object identity       |
| is not   | Negated Object identity |
| in       | Collection Membership |
| not in   | Negated Collection Membership |

```python
# bool revisited
print(type(True))
print(type(False))
```

```python
# relational / comparison operators
a = 4
b = 3
print(a == b)   # equality
print(a < b)    # less than
print(a > b)    # greater than
print(a != b)   # not equal
print(a <= b)   # less than or equal
print(a >= b)   # greater than or equal
```

```python
# collection membership
print('e' in 'hello')
print('f' in 'hello')
print(1 in [1, 2, 3, 4])
print(5 in [1, 2, 3, 4])

print('e' not in 'hello')
print('f' not in 'hello')
print(1 not in [1, 2, 3, 4])
print(5 not in [1, 2, 3, 4])
```

```python
# object id match
a = 4
b = 3
print(id(a))
print(id(b))

print(a is a)
print(a is b)

print(a is not a)
print(a is not b)

c = 4
print(id(a))
print(id(c))

print(a is c)

print(a is not c)
```

## Logical Operators

| Operator | Unary or Binary | The Result is True When... |
| :------- | :-------------- | :--------------------------|
| not      | unary           | Operand is False           |
| and      | binary          | Both Operands Must be True |
| or       | binary          | Only one Operand needs to be True |

### `and` Truth Table
| X  AND | Y    | Evaluates To:  |
| :----- | :--- | :------------- |
| True   | True | True           |
| True   | False| False          |
| False  | True | False          |
| False  | False| False          |

```python
# and logical operator
print(True and True)
print(True and False)
print(False and True)
print(False and False)

timeInRank = True
enoughPromotionPoints = False

elligibleForPromotion  = timeInRank and enoughPromotionPoints

print(f'SGT Smith elligble for promotion: {elligibleForPromotion}')
```

### `or` Truth Table
| X  OR  | Y    | Evaluates To:  |
| :----- | :--- | :------------- |
| True   | True | True           |
| True   | False| True           |
| False  | True | True           |
| False  | False| False          |

```python
# or logical operator
print(True or True)
print(True or False)
print(False or True)
print(False or False)

ballThrownToFirstBeforeRunner = True
runnerTaggedByBallBeforeFirst = False

runnerIsOut = ballThrownToFirstBeforeRunner or runnerTaggedByBallBeforeFirst

print(f'The batter is out: {runnerIsOut}')
```

### `not` Truth Table
| X | NOT X Evaluates To: |
|---|---------------------|
| True | False |
| False | True |

```python
# not logical operator
print(not(True))
print(not(False))

minesPresent = False

safeToProceed = not(minesPresent)

print(f'The platoon may proceed through the obstacle: {safeToProceed}')
```

### Operator Order of Precedence

| Order | Operator | Comments |
|-------|----------|----------|
| 1 | () | |
| 2 | ** | right to left |
| 3 | *,/,//,% | left to right |
| 4 | +,- | left to right | 
| 5 | ==,!=,<=,>=,<,>,is,is not, in, not in | left to right |
| 6 | not | left to right |
| 7 | and | left to right |
| 8 | or | left to right |

# Identify Pythonic Code Blocks

- Python provides a robust set of keywords and related items that control the flow of execution within an application.

- In this section, we will explore the various conditional execution options that Python provides.

- In addition, we will look at the various operators used by Python in control flow constructs.

- Python mandates the use of indenting within a compound statement. The first line of the compound statement is referred to as the header.

- All other statements within the compound statement are referred to as the suite or body and must be indented the same number of columns to be part of the same suite.

- The suite ends with the first statement that is “indented” to the column of the header.

- One such type of compound statement is a control structure.

- Suites must be indented the same amount of white space from the starting column of the header.

- If tabs are used in the source code, a single tab is not equal to the number of spaces used in a tab.

- It is recommended that spaces be used over tabs.

# Conditionals a.k.a Branching a.k.a Selection Statements

## if

- The fundamental decision making control structure in many programming languages is the `if` statement.
- Code inside an `if` suite is only executed if a given condition is `True`.
- The following examples demonstrate proper indenting when using the `if` statement and its variants.
- Also, notice the required use of the colon `:` to end the header portion of the `if` statement.

```python
number = 25

if number <= 25:
   print("number is smaller or equal to 25")
```

```python
lst = [1,2,3,4,5]

if 5 in lst:
    print('5 is found in lst')
```

```python
if 50 in lst:
    print('50 found in lst')
```

```python
condition = True

if condition:
    print('this line will display if the condition is True.')

print('this line always displays')
```

```python
ui = input('Enter an integer: ')
if ui.isdigit():
    print(f'The integer you entered is {int(ui)}')
```

## else

- An `else` statement is useful when zero specified conditions are met.

```python
lst = [1,2,3,4,5]

if 50 in lst:
    print('50 found in lst')
else:
   print('50 was not found')
```

```python
condition =  True

if condition:
    print('this line will display if the condition is True.')
else:
    print('this line will display if the condition is False.')

print('this line always displays.')
```

```python
ui = input('Enter an integer: ')
if ui.isdigit():
    print(f'The integer you entered is {int(ui)}')
else:
    print(f'{ui} is not an integer!')
```

## elif

- When writing an `if` statement, there can be zero or more `elif` blocks, and the `else` block is optional.
- The keyword `elif` can be used to prevent the testing of multiple `if` statements when only one of the `if` statements can ever be `True` at a time.
- It can also sometimes prevent the need for nesting `if` statements inside of an `else`.
- `elif` gives the opportunity to have multiple conditional checks.
- When one conditional check results in `True`, the `True` part of the suite is executed and the rest of the `elif` statements are skipped.

```python
number = 25

if number <= 25:
   print("number is smaller or equal to 25")		

elif number == 50:
   print("number is 50")

elif number <= 75:
   print("number is less than or equal to 75")

else:
   print("number is greater than 75")
```

```python
# correct logic

grade = 100

if grade >= 90:
    print('You got an A')
elif grade >= 80:
    print('You got a B')
elif grade >= 70:
    print('You got a C')
elif grade >= 60:
    print('You got a D')
else:
    print('You failed.')
```

```python
# bad logic - need to go from most specific to least specific

grade = 100

if grade >= 60:
    print('You got an D')
elif grade >= 70:
    print('You got a C')
elif grade >= 80:
    print('You got a B')
elif grade >= 90:
    print('You got a A')
else:
    print('You failed.')
```

```python
# correct logic, but unnecessary conditions used given if-elif-else construct

grade = 100

if grade >= 90:
    print('You got an A')
elif grade >= 80 and grade < 90:
    print('You got a B')
elif grade >= 70 and grade < 80:
    print('You got a C')
elif grade >= 60 and grade < 70:
    print('You got a D')
else:
    print('You failed.')
```

#### determine if user input integer is odd or even

```python
# odd or even?

number = int(input('Enter a number: '))

if number % 2 == 0:
    print(f'{number} is even.')
else:
    print(f'{number} is odd.')
```


---

[⬆️ Back to Module Index](../README.md)
