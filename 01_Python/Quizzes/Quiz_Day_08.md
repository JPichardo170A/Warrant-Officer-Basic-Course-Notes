# 🧪 Python Quiz — Day 8

*Module 01 — Python | Exam Prep*

---

**Question:** What is the purpose of `__init__`?

**Answer:** To initialize the attributes of a new object instance.

**Question:** What is the purpose of `__str__`?

**Answer:** To define a custom string representation of an object.

**Question:** What is the purpose of `if __name__ == "__main__":`?

**Answer:** To determine if a script is being run directly or imported as a module.

**Question:** What is the purpose of `self` in class methods?

**Answer:** To access instance variables and methods within the class.

**Question:** Create a `Car` class with year, make, model, color, trim, and transmission.

```python
class Car:
    def __init__(self, year, make, model, color, trim, transmission):
        self.year = year
        self.make = make
        self.model = model
        self.color = color
        self.trim = trim
        self.transmission = transmission

    def __str__(self):
        return f'{self.year} {self.make} {self.model}\n  Color: {self.color}\n  Trim: {self.trim}\n  Transmission: {self.transmission}'
```

**Question:** Create a `Chest` class that stores items, with `add`, `drop`, and `empty` methods.

```python
class Chest:
    def __init__(self, *items):
        self.items = list(items)

    def add(self, *new_items):
        self.items.extend(new_items)

    def drop(self, *items_to_remove):
        for item in items_to_remove:
            if item in self.items:
                self.items.remove(item)

    def empty(self):
        self.items.clear()
```

**Question:** Create a `ServiceMember` class with branch, name, rank, and MOS. Allow changing MOS and rank.

```python
class ServiceMember:
    def __init__(self, service, name, rank, mos):
        self.service = service
        self.name = name
        self.rank = rank
        self.mos = mos

    def change_mos(self, new_mos):
        self.mos = new_mos

    def change_rank(self, new_rank):
        self.rank = new_rank
```

---
---

[⬆️ Back to Quizzes Index](README.md) | [⬆️ Back to Module Index](../README.md)
