
# Technical Paper on Python Strings

## Introduction
Strings are one of the most important data types in Python.  
A string is a sequence of Unicode characters enclosed in single quotes `' '`, double quotes `" "`, or triple quotes `''' '''` / `""" """` for multi-line text.  
They are widely used for text processing, data storage, and manipulation.

---

## Creating Strings
```python
s1 = 'Hello'
s2 = "World"
s3 = '''This is
a multi-line
string'''
````

* Single quotes or double quotes can be used.
* Triple quotes are used for multi-line strings.

---

## Handling Quotes in Strings

Sometimes we need to use quotes inside strings. Python provides solutions:

1. **Escape Character (`\`)**

```python
print("Practice makes \"Perfect\"")
```

2. **Using Alternate Quotes**

```python
print('She said "Hello"')
```

---

## String Indexing and Slicing

Strings are **sequences**, meaning each character has an index.

```python
s = "Python"
print(s[0])     # P
print(s[-1])    # n
print(s[0:4])   # Pyth
```

* Indexing starts at **0**.
* Negative indices count from the end.
* Slicing allows extracting substrings.

---

## String Properties

* **Immutable** → Once created, string values cannot be changed.

```python
s = "Python"
# s[0] = 'J'  
```

* **Iterable** → Strings can be looped character by character.

```python
for ch in "Hi":
    print(ch)
```

---

## Common String Methods

Python provides built-in methods for easy text handling:

```python
text = "Hello World"

print(text.lower())     # hello world
print(text.upper())     # HELLO WORLD
print(text.title())     # Hello World
print(text.count("o"))  # 2
print(text.replace("World", "Python"))  # Hello Python
```

---

## Splitting and Joining

* `split()` breaks a string into a list.
* `join()` joins elements into a string.

```python
data = "a,b,c"
parts = data.split(",")     # ['a', 'b', 'c']
print("-".join(parts))      # a-b-c
```

---

## String Formatting

Python supports multiple ways of formatting strings.

1. **f-Strings (Python 3.6+)**

```python
name = "Akshitha"
age = 22
print(f"My name is {name}, age {age}")
```

2. **format() Method**

```python
print("My name is {}, age {}".format(name, age))
```

---

## Raw Strings

Sometimes we don’t want escape sequences (like `\n`) to be interpreted.
We can use raw strings with prefix `r`.

```python
path = r"C:\newfolder\file.txt"
print(path)
```

---

## Memory Representation and Interning

* Strings are **immutable**.
* If two strings have the same value, Python may store them at the same memory location (string interning).
* This improves efficiency.

```python
a = "hello"
b = "hello"
print(id(a), id(b))  # Same memory address
```

---

## Conclusion

* Strings in Python are powerful, immutable, and widely used.
* They support indexing, slicing, iteration, and many built-in methods.
* Features like string formatting, raw strings, and interning make them flexible for real-world applications.

---

## References

1. [Python Documentation – Strings](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
2. [W3Schools – Python Strings](https://www.w3schools.com/python/python_strings.asp)
3. [GeeksforGeeks – Python Strings](https://www.geeksforgeeks.org/python-strings/)
4. [Real Python – Python Strings](https://realpython.com/python-strings/)
