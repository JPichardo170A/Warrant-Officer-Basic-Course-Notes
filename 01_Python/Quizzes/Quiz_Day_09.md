# 🧪 Python Quiz — Day 9

*Module 01 — Python | Exam Prep*

---

**Question:** Calculate a grade curve from the highest score to 100.

```python
def curve_scores(grades):
    curve = 100 - max(grades)
    return [grade + curve for grade in grades]
```

**Question:** Dictionaries store values in **key** and **value** pairs. If you `pop` an item, it is extracted as a **tuple**.

**Question:** Read a log file of failed logins, count per user, and append results.

```python
def count_failed_logins(logfile, resultfile):
    with open(logfile, 'r') as f:
        lines = f.readlines()
    counts = {}
    for line in lines:
        user = line.split()[3]
        counts[user] = counts.get(user, 0) + 1
    with open(resultfile, 'a') as f:
        for user, count in counts.items():
            f.write(f'{user}: {count} failed logins\n')
```

**Question:** The function used to gather data from a user is `input()`.

**Question:** Select all mutables: **set**, **dictionary**, **list**, **variable**.

**Question:** What is the scope of `lst1` inside a function? **Answer:** Local.

**Question:** Select all ways to sort a tuple in descending order:
- `(1,2,3,4)[::-1]`
- `sorted((1,2,3,4), reverse=True)`

**Question:** Number of methods/attributes for a boolean object?

```python
len(dir(bool))    # 71
```

**Question:** Choose the correct index:

```python
list1 = [6, 3, 4, 7, 1, 2][3]     # 7
list1 = ["Good", "morning", "class"][0]    # Good
list1 = ["Jackson", "Jordan", "Tyson", "Phelps", "Bay", "Cera"][-1]  # Cera
```

**Question:** Convert a string number into an integer.

```python
def make_number(program_input):
    return int(program_input)
```

**Question:** Your Python file must have execute permissions and a shebang line to execute with only the filename. **Answer:** `True`

**Question:** Match container types:

| Syntax | Type |
|--------|------|
| `[1]` | `list` |
| `{1}` | `set` |
| `{'a': 1}` | `dict` |
| `(1,)` | `tuple` |

**Question:** Boolean evaluation:

| Expression | Result |
|-----------|--------|
| `1 == True` | `True` |
| `False or True == True` | `True` |
| `"True" == True` | `False` |
| `True and True == False and False` | `False` |
| `True or False == False` | `True` |

**Question:** Which is NOT a string method? **Answer:** `len()` (it's a built-in function, not a string method).

**Question:** Remove duplicates and return a sorted descending list.

```python
def no_dupes(given_lst):
    unique_set = set(given_lst)
    unique_list = list(unique_set)
    unique_list.sort(reverse=True)
    return unique_list
```

**Question:** Create an agent name from a full name for "Men in Black."

```python
def mib_name(name):
    return f"Agent {name.split()[1][0].upper()}"
```

**Question:** When binding a network socket with an IP and port, what data type must be used? **Answer:** `tuple`

---
---

[⬆️ Back to Quizzes Index](README.md) | [⬆️ Back to Module Index](../README.md)
