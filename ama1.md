

## 1. What is HTML?

**Answer:**  
HTML (HyperText Markup Language) is the standard language used to create and structure webpages. It defines the structure of a webpage using elements (tags) such as `<html>`, `<head>`, `<body>`, `<p>`, `<h1>`, and `<div>`.

**Example:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Page</title>
</head>
<body>
    <h1>Hello World</h1>
    <p>This is a paragraph.</p>
</body>
</html>
````

---

## 2. How do you handle exceptions in Python?

**Answer:**
Exceptions are runtime errors. Python handles them using `try`, `except`, `else`, and `finally` blocks.

**Example:**

```python
try:
    num = int(input("Enter a number: "))
    print(10 / num)
except ValueError:
    print("Invalid input! Enter a number.")
except ZeroDivisionError:
    print("Cannot divide by zero.")
else:
    print("Division successful!")
finally:
    print("Program finished.")
```

---

## 3. Why is it suggested to use `venv` for Python projects?

**Answer:**
`venv` (Virtual Environment) creates isolated environments for each Python project.

**Benefits:**

* Keeps project dependencies separate
* Prevents package version conflicts
* Makes deployment and sharing easier

**Commands:**

```bash
# Create a virtual environment
python -m venv myenv

# Activate (Linux/Mac)
source myenv/bin/activate

# Activate (Windows)
myenv\Scripts\activate

# Deactivate environment
deactivate
```

---

## 4. What is Git?

**Answer:**
Git is a distributed version control system used to track changes in code and collaborate with multiple developers.

**Common Git Commands:**

```bash
git init           # Initialize a repository
git clone <url>    # Clone a repository
git status         # Check repository status
git add <file>     # Stage changes
git commit -m "msg" # Commit changes
git push           # Push changes to remote
git pull           # Pull latest changes
```

---

## 5. How to create and change directory in CLI?

**Answer:**

* **Create directory:**

```bash
mkdir folder_name
```

* **Change directory:**

```bash
cd folder_name
```

* **Other useful commands:**

```bash
pwd   # Show current directory
ls    # List files/folders
cd .. # Move to parent directory
```

---

## 6. How to give permission to a file?

**Answer:**
In Linux/Mac, file permissions are managed using `chmod`. Permissions define who can **read (r), write (w), or execute (x)** a file.

**Example:**

```bash
chmod 644 file.txt   # Owner: read/write, Others: read
chmod 755 script.sh  # Owner: read/write/execute, Others: read/execute
```

**Check permissions:**

```bash
ls -l file.txt
```

Output:

```
-rw-r--r-- 1 user user 0 Sep 13 12:00 file.txt
```

* `rw-` → owner can read/write
* `r--` → others can read

---

