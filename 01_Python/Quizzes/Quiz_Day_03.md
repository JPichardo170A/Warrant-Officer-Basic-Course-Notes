# 🧪 Python Quiz — Day 3

*Module 01 — Python | Exam Prep*

---

**Question:** Find all numbers divisible by 7 in a range of 0-100.

```python
lst = list(range(0, 101))
for num in lst:
    if num % 7 == 0:
        print(num)
```

**Question:** Write a function that prints "Let's start class!" if the user provides 17 students; "Too many students..." if higher; otherwise calculate how many are still needed.

```python
def check_students(count):
    if count == 17:
        print("Let's start class!")
    elif count > 17:
        print("Too many students...")
    else:
        needed = 17 - count
        print(f"Really? We are still waiting on {needed} students?!")
```

**Question:** Write a function that returns `True` only if the data type is a list AND it has something in it.

```python
def check_data(stuff):
    if isinstance(stuff, list) and len(stuff) > 0:
        return True
```

**Question:** Students have taken an exam twice with a passing score of 70. Return the final grade based on two scores. Both arguments must be `int` or `float`.

**Question:** Boolean evaluation answers:

| Expression | Result |
|-----------|--------|
| `False == False` | `True` |
| `True and True` | `True` |
| `(3 != 3) == False and False == False` | `True` |
| `3 == 3 and 3 == 4` | `False` |
| `False and False` | `False` |
| `"Kirk" == "Carter" or 1000 <= 1001` | `True` |

**Question:** Calculate the average from a list of grades, rounded to a whole number.

```python
def avg_grades(grades):
    return round(sum(grades) / len(grades))
```

**Question:** Turn a range into a list, print its length, then print odd numbers.

```python
data = range(3, 24)
data_list = list(data)
odds = [n for n in data_list if n % 2 != 0]
print(len(data_list))
print(len(odds), odds)
```

**Question:** Reverse any iterable using slicing.

```python
def reverse_iterable(data):
    return data[::-1]
```

---
---

[⬆️ Back to Quizzes Index](README.md) | [⬆️ Back to Module Index](../README.md)
