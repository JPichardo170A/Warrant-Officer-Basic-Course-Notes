# 🧪 Python Quiz — Day 5

*Module 01 — Python | Exam Prep*

---

**Question:** True or False: If a file exists, write mode will NOT overwrite the file.

**Answer:** `False` — write mode (`w`) **will** overwrite the file.

**Question:** Which function reads the entire contents of a file from current cursor position?

**Answer:** `read()`

**Question:** Continuously read user strings and write each on its own line to a file.

```python
def gathering_thoughts(fname):
    with open(fname, 'w') as f:
        while True:
            line = input()
            if not line:
                break
            f.write(line + '\n')
```

**Question:** Copy contents from one file to another.

```python
def copy_paste(infile, outfile):
    with open(infile, "r") as f_in:
        content = f_in.read()
    with open(outfile, "w") as f_out:
        f_out.write(content)
```

**Question:** Read file contents into a variable and print.

```python
with open("Test.txt", "r") as file:
    contents = file.read()
print(contents)
```

**Question:** Read all usernames into a list.

```python
with open("Test.txt", "r") as file:
    usernames = file.readlines()
print(usernames)
```

**Question:** Write "Python is fun" to a file in append mode.

```python
with open("info.txt", 'a') as file:
    file.write("Python is fun")
```

---
---

[⬆️ Back to Quizzes Index](README.md) | [⬆️ Back to Module Index](../README.md)
