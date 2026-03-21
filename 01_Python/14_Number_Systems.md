# 🔢 Number Systems

*Module 01 — Python | Day 7*

---

## 🎯 Learning Objectives

- Understand decimal (base 10), binary (base 2), octal (base 8), and hexadecimal (base 16)
- Convert between number systems with `bin()`, `oct()`, `hex()`, `int()`
- Use binary, octal, and hex literals in Python
- Apply bitwise operators

---

# Number Systems

## 4 types of number systems

### Integer - Decimal - Base 10
| 1000 | 100 | 10 | 1 |
|------|-----|----|---|
| 10**3 | 10**2 | 10**1 | 10**0 |

- Integers are any combination of base 10 whole numbers: 0-9

- Python easily interprets these numbers as `int` data types without any additional code needed. 

Use the number 16 to convert into each of the remaining number systems

### Binary - Base 2
| 8 | 4 | 2 | 1 |
|------|-----|----|---|
| 2**3 | 2**2 | 2**1 | 2**0 |

- Binary numbers are any combination of base 2 whole numbers: 0-1

- Python provides a built-in function that performs the conversion of `int` into a binary `str`

Convert the `int` 16 into a binary `str`:

```python
binary_16 = bin(16)
print(binary_16)

print(bin(1))
print(bin(2))
print(bin(6))
print(bin(9))
```

It is important to note that the `bin()` conversion function results in a `str` data type

```python
print(type(binary_16))
```

#### Binary literal in Python

- Python allows you to directly type `0b10000` and understands that this is a literal binary number

- While Python can interpret this binary literal, it is represented in output as an `int`
    - Which is why if you `print(0b10000)` the output will be 16
    - Also, if you `print(type(0b10000))` the output is `<class 'int'>`

```python
print(0b10000)
print(type(0b10000))
```

#### Convert binary string to integer

- Convert the binary `str` stored in `binary_16` back into an `int`
- The `int` conversion function has a parameter `base` that accepts an `int` indicating what base rules the `str` being converted needs to follow

In this case we are starting with a binary `str` and binary follows Base 2 rules

```python
binary_16 = bin(16)

int_16 = int(binary_16, base=2)
print(int_16)

print(int('0b1',2))
print(int('0b10',2))
print(int('0b110',2))
print(int('0b1001',2))
```

### Octal - Base 8
| 512 | 64 | 8 | 1 |
|------|-----|----|---|
| 8**3 | 8**2 | 8**1 | 8**0 |

- Octal numbers are represented using a grouping of Base 8 integers 0-8

- Python provides a built-in function that performs the conversion of `int` into an octal `str`

Convert the `int` 16 into an octal `str`:

```python
oct_16 = oct(16)
print(oct_16)

print(oct(1))
print(oct(2))
print(oct(11))
print(oct(19))
```

#### Octal literal in Python

- Python allows you to directly type `0o20` and understands that this is a literal octal number

- While Python can interpret this octal literal, it is represented in output as an `int`
    - Which is why if you `print(0o20)` the output will be 16
    - Also, if you `print(type(0o20))` the output is `<class 'int'>`

```python
print(0o20)
print(type(0o20))
```

#### Convert octal string to integer

- Convert the octal `str` stored in `oct_16` back into an `int`
- The `int` conversion function has a parameter `base` that accepts an `int` indicating what base rules the `str` being converted needs to follow

In this case we are starting with an octal `str` and octal follows Base 8 rules

```python
oct_16 = oct(16)

int_16 = int(oct_16, base=8)
print(int_16)

print(int('0o1',8))
print(int('0o2',8))
print(int('0o13', 8))
print(int('0o23',8))
```

### Hexadecimal - Base 16
| 4096 | 256 | 16 | 1 |
|------|-----|----|---|
| 16**3 | 16**2 | 16**1 | 16**0 |

- Hexadecimal numbers are represented using a grouping of Base 16 integers 0-9 and characters A-F 

- Python provides a built-in function that performs the conversion of `int` into a hexadecimal `str`

Convert the `int` 16 into a hexadecimal `str`:

```python
hex_16 = hex(16)
print(hex_16)

print(hex(1))
print(hex(2))
print(hex(34))
print(hex(89))
```

#### Hexadecimal literal in Python

- Python allows you to directly type `0x10` and understands that this is a literal binary number

- While Python can interpret this hexadecimal literal, it is represented in output as an `int`
    - Which is why if you `print(0x10)` the output will be 16
    - Also, if you `print(type(0x10))` the output is `<class 'int'>`

```python
print(0x10)
print(type(0x10))
```

#### Convert hexadecimal string to integer

- Convert the hexadecimal `str` stored in `hex_16` back into an `int`
- The `int` conversion function has a parameter `base` that accepts an `int` indicating what base rules the `str` being converted needs to follow

In this case we are starting with a hexadecimal `str` and hexadecimal follows Base 16 rules

```python
hex_16 = hex(16)

int_16 = int(hex_16, base=16)
print(int_16)

print(int('0x1',16))
print(int('0x2',16))
print(int('0x22', 16))
print(int('0x59',16))
```

## Converting from non-int number system to another non-int

- Python will not allow you to convert a Binary, Octal, or Hexadecimal `str` into any number system OTHER THAN an `int`

- All of these numbers systems must 'pass through' an `int` conversion before being able to be converted

Examples:
___

|  **Scenario:** |
|---|
|Given a Binary `str` convert it into an Octal and then Hexadecimal `str`|

- Observe the error when attempting to convert directly from Binary to Octal:

```python
bin_str = '0b111110100'

oct_str = oct(bin_str)
```

This is where the Binary `str` must 'pass through' an `int` data type first:

```python
bin_str = '0b111110100'

bin_str_int = int(bin_str,base=2)

oct_str = oct(bin_str_int)
print(oct_str)
```

This concept is simply repeated to convert the Octal `str` into a Hexadecimal `str`:

```python
oct_str = '0o14615'

oct_str_int = int(oct_str,base=8)

hex_str = hex(oct_str_int)
print(hex_str)
```


---

[⬆️ Back to Module Index](../README.md)
