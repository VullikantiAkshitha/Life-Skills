
# Technical Paper

## 1. How to Create or Change a Branch (Git)

Branches in Git are used to work on different features or fixes independently.  

### Create a New Branch
```bash
git branch branch_name
````

### Switch to a Branch

```bash
git checkout branch_name
```

### Create and Switch in One Step

```bash
git checkout -b branch_name
```

### View All Branches

```bash
git branch
```

---

## 2. Joins in SQL and Their Types

**Joins** are used to combine rows from two or more tables based on related columns.

### Types of Joins:

1. **INNER JOIN** → Returns only matching rows between tables.
2. **LEFT JOIN (or LEFT OUTER JOIN)** → Returns all rows from the left table and matching rows from the right table.
3. **RIGHT JOIN (or RIGHT OUTER JOIN)** → Returns all rows from the right table and matching rows from the left table.
4. **FULL JOIN (or FULL OUTER JOIN)** → Returns all rows when there is a match in either table.
5. **CROSS JOIN** → Returns the Cartesian product of both tables (every row of first table joined with every row of second).
6. **SELF JOIN** → A table joined with itself.

---

## 3. What is a Function in Python?

A **function** in Python is a block of reusable code that performs a specific task. Functions help in organizing code, avoiding repetition, and improving readability.

### Syntax:

```python
def function_name(parameters):
    # block of code
    return result
```

### Example:

```python
def add(a, b):
    return a + b

print(add(3, 5))  # Output: 8
```

---

## 4. List Comprehension in Python

**List comprehension** provides a shorter and more readable way to create lists in Python.

### Syntax:

```python
[expression for item in iterable if condition]
```

### Example:

```python
numbers = [1, 2, 3, 4, 5]
squares = [x**2 for x in numbers]
print(squares)  # Output: [1, 4, 9, 16, 25]
```

With condition:

```python
even_numbers = [x for x in numbers if x % 2 == 0]
print(even_numbers)  # Output: [2, 4]
```

---

## 5. DROP vs DELETE in SQL

### DELETE:

* Removes rows from a table based on a condition.
* Can be rolled back (if inside a transaction).
* Syntax:

```sql
DELETE FROM table_name WHERE condition;
```

### DROP:

* Removes the **entire database object** (like table, view, or database).
* Cannot be rolled back once executed.
* Syntax:

```sql
DROP TABLE table_name;
```

**Key Difference**:

* **DELETE** → Removes **data** (rows).
* **DROP** → Removes the **structure** (table).

---

## 6. Inheritance in Object-Oriented Programming

**Inheritance** allows a class (child) to inherit properties and methods from another class (parent).

### Types of Inheritance:

1. **Single Inheritance** → One child class inherits from one parent class.
2. **Multiple Inheritance** → One child class inherits from multiple parent classes.
3. **Multilevel Inheritance** → A chain of inheritance (Parent → Child → Grandchild).
4. **Hierarchical Inheritance** → Multiple child classes inherit from a single parent class.
5. **Hybrid Inheritance** → A combination of two or more types of inheritance.

### Example in Python:

```python
class Parent:
    def greet(self):
        print("Hello from Parent")

class Child(Parent):  # Single Inheritance
    def greet_child(self):
        print("Hello from Child")

c = Child()
c.greet()        # Inherited method
c.greet_child()  # Child method
```

---

## 7. Abstract Method

An **abstract method** is a method declared in an abstract class but not implemented.
It forces subclasses to provide their own implementation.

### In Python:

* Defined using the `abc` module (`Abstract Base Class`).

### Example:

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass  # No implementation

class Circle(Shape):
    def __init__(self, r):
        self.r = r

    def area(self):
        return 3.14 * self.r * self.r

c = Circle(5)
print(c.area())  # Output: 78.5
```

---

# Conclusion

* Git branches help in parallel development.
* SQL joins connect data across tables.
* Functions in Python make code reusable.
* List comprehension simplifies list creation.
* `DELETE` removes data, `DROP` removes structure.
* Inheritance promotes reusability and hierarchy in OOP.
* Abstract methods enforce subclass implementation.

```

