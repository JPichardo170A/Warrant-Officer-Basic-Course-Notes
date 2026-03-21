# 🧪 Python Quiz — Day 7

*Module 01 — Python | Exam Prep*

---

**Question:** Complete args and kwargs code:

```python
def sumAll(*args, **kwargs):
    return sum(args) + sum(kwargs.values())

print(sumAll(1, 2, 3, 4, a=1, b=2, c=3))    # 16
```

**Question:** What does `**kwargs` do in a function definition?

**Answer:** Packs pairs of `keyword=value` into a dictionary.

**Question:** What does `*args` do in a function definition?

**Answer:** Packs positional arguments into a tuple.

**Question:** What does `*` do to a list when passed to a function?

**Answer:** It **unpacks** or expands the list into individual arguments.

**Question:** True or False: Positional arguments must come before keyword arguments.

**Answer:** `True`

**Question:** Print all positional arguments on separate lines, then keyword arguments in alphabetical order.

```python
def infinitearguments(*args, **kwargs):
    for arg in args:
        print(arg)
    for key in sorted(kwargs):
        print(f'{key}={kwargs[key]}')
```

**Question:** Read file lines, return sorted in case-insensitive ASCII order.

```python
def sort_ascii(filepath):
    with open(filepath, 'r') as file:
        lines = [line.strip() for line in file.readlines()]
        lines.sort(key=str.lower)
    return lines
```

**Question:** Read file lines, return sorted longest to shortest.

```python
def sort_length(filepath):
    with open(filepath, 'r') as file:
        lines = [line.rstrip('\n') for line in file if line.strip()]
    return sorted(lines, key=len, reverse=True)
```

---
---

[⬆️ Back to Quizzes Index](README.md) | [⬆️ Back to Module Index](../README.md)
