# 🧠 Key Terms in Python

Python is a powerful and versatile programming language with a rich ecosystem. Understanding key terms in Python is fundamental for both beginners and experienced developers. In this document, we’ll cover some of the most important Python concepts, keywords, and terminology.

---

## 🔑 Key Python Concepts

### 1. **Variables and Data Types**
   - **Variable**: A symbolic name for a value. In Python, variables are dynamically typed, meaning their type is determined at runtime.
   - **Data Types**: Defines the type of data a variable can hold. Common data types include:
     - `int`: Integer numbers (e.g., `5`, `-3`)
     - `float`: Floating-point numbers (e.g., `3.14`, `-0.001`)
     - `str`: String (e.g., `"Hello World"`)
     - `list`: Ordered, mutable collection of items (e.g., `[1, 2, 3]`)
     - `tuple`: Ordered, immutable collection of items (e.g., `(1, 2, 3)`)
     - `dict`: Dictionary (e.g., `{"name": "John", "age": 30}`)
     - `set`: Unordered collection of unique items (e.g., `{1, 2, 3}`)

### 2. **Control Flow**
   - **Conditional Statements**: Control the flow of execution based on conditions. Common structures include:
     - `if`, `elif`, and `else`
   - **Loops**: Repeatedly execute code blocks.
     - `for` loop: Iterates over a sequence (e.g., list, string)
     - `while` loop: Repeats as long as a condition is true

### 3. **Functions**
   - **Function**: A block of code that only runs when called. Functions can take arguments and return a result.
     - Defined using the `def` keyword.
     - Example:
       ```python
       def greet(name):
           return f"Hello, {name}!"
       ```
   - **Lambda Functions**: Small anonymous functions, defined using the `lambda` keyword.
     - Example:
       ```python
       add = lambda x, y: x + y
       ```

### 4. **Classes and Objects**
   - **Class**: A blueprint for creating objects (instances). Defines properties (attributes) and methods (functions).
   - **Object**: An instance of a class.
   - **Constructor (`__init__`)**: Special method to initialize an object.
     - Example:
       ```python
       class Person:
           def __init__(self, name, age):
               self.name = name
               self.age = age
       ```

### 5. **Exception Handling**
   - **try, except**: Used to handle errors or exceptions that occur during the execution of code.
     - Example:
       ```python
       try:
           result = 10 / 0
       except ZeroDivisionError:
           print("Cannot divide by zero!")
       ```

### 6. **Modules and Packages**
   - **Module**: A file containing Python definitions and statements.
   - **Package**: A collection of Python modules organized in directories.
     - Example:
       ```python
       import math
       print(math.sqrt(16))
       ```

### 7. **Generators**
   - **Generator**: A special type of iterator that produces items lazily (one at a time) using the `yield` keyword.
     - Example:
       ```python
       def count_up_to(max):
           count = 1
           while count <= max:
               yield count
               count += 1
       ```

---

## 🔍 Key Python Keywords & Definitions

| Term | Definition |
|------|------------|
| **def** | Used to define a function. |
| **lambda** | Used to create anonymous functions. |
| **class** | Used to define a class. |
| **self** | Refers to the current instance of a class. |
| **import** | Used to include external modules or packages into the current script. |
| **try** | Defines a block of code that may throw exceptions. |
| **except** | Defines the block of code that handles exceptions raised in the `try` block. |
| **yield** | Used in generators to produce a sequence of values lazily. |
| **global** | Declares a variable to be global, i.e., accessible across functions. |
| **None** | Represents the absence of a value or a null value. |
| **True/False** | Boolean values representing truth values. |
| **is** | Tests for object identity (whether two references point to the same object). |

---

## 🧑‍💻 Python Advanced Concepts

### 1. **Decorators**
   - **Decorator**: A function that modifies the behavior of another function or method. Decorators are used to add functionality to an existing function without changing its structure.
     - Example:
       ```python
       def decorator_function(original_function):
           def wrapper_function():
               print("Wrapper executed this before {}".format(original_function.__name__))
               return original_function()
           return wrapper_function

       @decorator_function
       def display():
           return "Display function executed"
       ```

### 2. **Context Managers**
   - **Context Manager**: Provides a way to allocate and release resources cleanly. Implemented using `with` statements.
     - Example:
       ```python
       with open('file.txt', 'r') as file:
           content = file.read()
       ```

### 3. **List Comprehension**
   - **List Comprehension**: A concise way to create lists. It’s an elegant alternative to using `for` loops to build lists.
     - Example:
       ```python
       squares = [x**2 for x in range(10)]
       ```

### 4. **Metaclasses**
   - **Metaclass**: A class of a class, used to control the behavior of classes. Metaclasses are advanced concepts used in object-oriented programming to modify class creation.
     - Example:
       ```python
       class Meta(type):
           def __new__(cls, name, bases, dct):
               dct['added_attribute'] = True
               return super().__new__(cls, name, bases, dct)

       class MyClass(metaclass=Meta):
           pass
       ```

### 5. **Async Programming**
   - **Async/Await**: A syntax used to write asynchronous code, allowing non-blocking operations such as network requests or I/O operations.
     - Example:
       ```python
       import asyncio

       async def fetch_data():
           await asyncio.sleep(2)
           return "Data fetched"

       asyncio.run(fetch_data())
       ```

---

## 🔐 Best Practices

1. **Use List Comprehensions**: To write cleaner and more efficient code when creating lists.
2. **Avoid Using `global`**: It can lead to bugs and unexpected behavior. Use function arguments and return values.
3. **Write Unit Tests**: Always write tests for your functions and methods.
4. **Follow PEP 8**: Adhere to Python's official style guide for clean, readable code.
5. **Use Generators for Large Data**: When working with large datasets, prefer generators over lists to conserve memory.

---

## 🔎 Common Interview Questions

- What is the difference between a list and a tuple in Python?
- How do you implement a decorator in Python?
- What is the purpose of the `self` keyword in a class?
- Explain the difference between `is` and `==` in Python.
- What is a generator and how does it differ from a regular function?
- How does Python handle memory management?

---

## 🔗 Extras

- [Python Official Documentation](https://docs.python.org/)
- [Python PEP 8 – Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)
- [Python List Comprehensions](https://realpython.com/list-comprehension-python/)
