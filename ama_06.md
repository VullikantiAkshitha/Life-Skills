

---

## 1. What is Django and Why is it Used?

**Django** is a high-level Python web framework that allows developers to create secure, scalable, and maintainable web applications quickly.  

### Key Features:
- **Rapid Development:** Pre-built components like authentication, admin panel, and ORM save time.  
- **Secure:** Protects against common security threats such as SQL injection, CSRF, and XSS.  
- **Scalable:** Handles large traffic and data efficiently.  
- **Versatile:** Used in e-commerce, social media, content management, and more.  

### Advantages:
- Reduces repetitive coding  
- Encourages clean architecture and separation of concerns  
- Supported by a large community and well-documented  

**Example of Django Use:**  
- Websites: Instagram, Pinterest, Mozilla  
- Web applications: Online learning platforms, E-commerce sites  

---

## 2. Difference Between Django Project and App

Django projects and apps provide **modularity and structure**.

| Feature | Project | App |
|---------|---------|-----|
| Definition | Full website with settings, configuration, and apps | A modular component handling a specific functionality |
| Example | `MyWebsite` | `Blog`, `Login`, `StudentManagement` |
| Reusability | Usually unique to the project | Can be reused in multiple projects |
| Purpose | Organize overall architecture | Perform a specific task independently |

**Project Structure Example:**  
```

myproject/
│
├── myproject/          # Project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
│
├── blog/               # App
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   └── templates/
│
└── manage.py

````

---

## 3. Models in Django

**Models** are Python classes that represent database tables. They define **fields (columns)**, **data types**, **relationships**, and **validations**.

### Features:
- Abstract SQL queries into Python code  
- Handle relationships: One-to-One, One-to-Many, Many-to-Many  
- Perform validations automatically  

### Example Model:
```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField(unique=True)
    marks = models.IntegerField()
    enrolled_date = models.DateField(auto_now_add=True)

    def __str__(self):
        return self.name
````

### Key Points:

* `models.Model` is the base class for all models
* `__str__` method defines readable representation
* Fields like `CharField`, `IntegerField`, `DateField` map to database column types

---

## 4. Views in Django

**Views** handle the logic of the application. They process requests, interact with models, and send responses to templates.

### Types of Views:

1. **Function-Based Views (FBV):** Simple Python functions
2. **Class-Based Views (CBV):** More structured, reusable, and extendable

### Function-Based View Example:

```python
from django.shortcuts import render
from .models import Student

def student_list(request):
    students = Student.objects.all()
    return render(request, 'students/list.html', {'students': students})
```

### Class-Based View Example:

```python
from django.views import View
from django.shortcuts import render
from .models import Student

class StudentListView(View):
    def get(self, request):
        students = Student.objects.all()
        return render(request, 'students/list.html', {'students': students})
```

### Key Points:

* Views bridge **models** and **templates**
* Contain business logic like fetching, updating, or deleting data

---

## 5. Templates in Django

**Templates** are HTML files that display dynamic content from views.

### Key Features:

* Separate design (HTML) from logic (Python)
* Reusable and maintainable
* Allow dynamic content using **template tags** and **filters**

### Example Template:

```html
<!-- students/list.html -->
<h1>Student List</h1>
<ul>
  {% for student in students %}
    <li>{{ student.name }} - {{ student.email }} - {{ student.marks }}</li>
  {% endfor %}
</ul>
```

### Template Tags:

* `{% for %}` loops
* `{% if %}` conditional statements
* `{{ variable }}` outputs dynamic data

---

## 6. `urls.py` in Django

**`urls.py`** maps URL patterns to views. It enables clean navigation and modular app structure.

### Example:

```python
# project-level urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('students/', include('students.urls')),  # Connects app URLs
]

# app-level urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.student_list, name='student_list'),
]
```

### Key Points:

* Each app can have its own `urls.py`
* Project `urls.py` connects all app URLs
* Naming URLs allows reverse URL resolution

---

## 7. `manage.py` in Django

**`manage.py`** is a command-line tool to manage Django projects.

### Common Commands:

| Command                            | Purpose                                  |
| ---------------------------------- | ---------------------------------------- |
| `python manage.py runserver`       | Start the development server             |
| `python manage.py makemigrations`  | Create migration files for model changes |
| `python manage.py migrate`         | Apply migrations to the database         |
| `python manage.py createsuperuser` | Create an admin user                     |
| `python manage.py shell`           | Open Django shell for testing            |

### Key Points:

* Simplifies development and maintenance
* Handles database, server, and administrative tasks

---

## 8. Django Admin Panel

**Admin Panel** is a pre-built interface to manage models and data.

### Features:

* Add, edit, delete records without writing code
* Secure access with authentication
* Customize which fields to display

### Example:

After creating a superuser:

```
http://127.0.0.1:8000/admin/
```

**Customizing Admin:**

```python
from django.contrib import admin
from .models import Student

class StudentAdmin(admin.ModelAdmin):
    list_display = ('name', 'email', 'marks', 'enrolled_date')
    search_fields = ('name', 'email')

admin.site.register(Student, StudentAdmin)
```

### Key Points:

* Saves time managing data
* Provides an organized view of database records

---

## Conclusion

Django is a robust framework that provides tools for **rapid web development**, **data management**, and **scalable applications**.
By understanding the following components, developers can build professional and maintainable web applications:

* Projects & Apps
* Models (Database)
* Views (Logic)
* Templates (Presentation)
* URL Routing
* `manage.py` (Project Management)
* Admin Panel (Data Management)

Django’s structure enforces **clean code**, **security**, and **reusability**, making it ideal for both small and large-scale web applications.

```

---


