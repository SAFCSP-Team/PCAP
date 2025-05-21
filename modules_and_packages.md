# Modules and Packages


## What is a Module? 
A **module** is a single Python file (.py) containing definitions and statements (such as functions, classes, variables, and constants) that can be imported and used in other Python files.

Each module has a unique name, and its contents can be accessed if you know the module's name.


## What is a Package?

A **package** is a way of organizing related Python modules into a directory hierarchy.

A package is simply a directory containing a special `__init__.py` file (which can be empty or contain initialization code), and one or more module files or sub-packages.

**Key facts:**
- Packages allow you to organize modules logically in subdirectories.
- Sub-packages are just packages within packages.
- Can be a directory sub-tree, or it can be packed inside a zip file.


## How to Use Modules and Packages

There are two perspectives:

1. **Module/Package User:** When you want to use an existing module or package (created by you or others).
2. **Module/Package Supplier:** When you want to create new modules or packages for your own use or for others.


## Importing Modules and Packages

To make a module usable, import it using the `import` keyword and the name of the module.

### Importing Single or Multiple Modules

```python
import math
import sys
# OR
import math, sys

print(math.sin(math.pi/2))
```
> [!NOTE]
>  The import must appear before the first use of any module entity.

### Importing Specific Entities

You can import specific functions, classes, or variables:

```python
from math import sin, pi

print(sin(pi/2))
```
Now, you can use `sin()` and `pi` directly without qualifying them with `math.`.

### Importing All Entities

Import everything from a module:

```python
from math import *
```

### Aliasing

You can import a module or entity under a different name:

```python
from math import pi as PI, sin as sine

print(sine(PI/2))
```
> [!NOTE]
> After successful execution of an aliased import, the original module name becomes inaccessible and must not be used.



## Namespaces

Every Python file (script or module) has its own **namespace**—a space where names are unique and don’t collide with names in other namespaces..

- When you import a module, its entities don’t enter your script’s namespace unless you use `from module import ...`.
- This allows you to have your own `sin`, `pi`, etc., without clashing with what’s in the math module.

**Example:**

```python
import math

def sin(x):
    # your version
    return 0.99999999 if 2 * x == pi else None

pi = 3.14

print(sin(pi/2))          # Calls your sin and pi 
print(math.sin(math.pi/2))  # Calls math's sin and pi 
```

_Output:_
```
0.99999999
1.0
```
## Nested Modules

A **nested module** refers to a module inside a package or a sub-package. Packages can contain sub-packages, creating a hierarchy or tree of modules.

**Example Structure:**
```
myproject/
    mypackage/
        __init__.py
        module1.py
        subpackage/
            __init__.py
            module2.py
```
**Usage:**
```python
import mypackage.module1
import mypackage.subpackage.module2
```
Or, to import a specific entity:
```python
from mypackage.subpackage.module2 import my_function
```
**Key Points:**
- The directory structure mirrors the dot-separated import path.
- Each directory must have an `__init__.py` file (can be empty) to be recognized as a package/sub-package.
- Nested modules and packages help organize complex applications.


## The `dir()` Function

The `dir()` function returns an alphabetically sorted list containing all the entities' names available in the module:

```python
import math
print(dir(math))
```
## The `sys.path` Variable

`sys` is a built-in Python module providing access to system-specific parameters and functions.  
`sys.path` is a list of directory names that constitute the interpreter’s search path for modules and packages.

- It is initialized from the environment variable `PYTHONPATH`, or a built-in default if `PYTHONPATH` is not set.
- You can modify `sys.path` at runtime.

**Example:**
```python
import sys
print(sys.path)
```

## Standard Library Modules

### The `math` Module

Provides access to mathematical functions and constants:
- `ceil(x)` – Returns the smallest integer ≥ x.
- `floor(x)` – Returns the largest integer ≤ x.
- `trunc(x)` – Returns the value of x truncated to an integer.
- `factorial(x)` – Returns the value of x!.
- `hypot(x, y)` – Returns the length of the hypotenuse of a right-angle triangle with the leg lengths equal to x and y. 
- `sqrt(x)` – Returns the square root.

```python
from math import sqrt, floor, ceil, trunc 

x = 1.4
y = 2.6

print(sqrt(x), sqrt(y))
print(floor(x), floor(y))
print(floor(-x), floor(-y))
print(ceil(x), ceil(y))
print(ceil(-x), ceil(-y))
print(trunc(x), trunc(y))
print(trunc(-x), trunc(-y))
```

### The `random` Module

For generating pseudo-random numbers.

- `random()` – Returns a float in the range [0.0, 1.0) - in other words: (0.0 <= x < 1.0).
- `seed()` – Sets the initial seed for the generator.
  - `seed()` – sets the seed with the current time.
  - `seed(int_value)` – sets the seed with the integer value.
- `choice(sequence)` – Randomly selects an element.
- `sample(sequence, k)` – Returns a random sample (list) of size `k`, where `k` is less than the `sequence` length.

> [!important]
> - A **seed** is an initial value for a pseudo-random number generator.
> - If you set the same seed, you'll get the same sequence of random numbers.

```python
from random import random, seed, choice, sample

seed(0)
print([random() for i in range(5)])

my_list = [1,2,3,4,5,6,7,8,9,10]
print(choice(my_list))
print(sample(my_list, 5))
```
Running the code above multiple times will get the same output because the seed is consistently set to the same value, producing the same generated values.


### The `platform` Module

Retrieves information about the underlying platform (OS, hardware, Python version).
- `platform(aliased = False, terse = False)` – Returns a string describing the platform, e.g., OS and hardware info.
  - `aliased`: If True, may show alternate names for the underlying platform components.
  - `terse`: If True, returns a shorter, more concise string if possible.
- `machine()` – Returns the machine type (e.g., processor architecture).
- `processor()` – Returns the actual processor name, if available.
- `system()` – Returns the OS name.
- `version()` – Returns the OS version.
- `python_implementation()` – Returns which Python implementation is running (except CPython).
- `python_version_tuple()` – Returns the Python version as a (major, minor, patch) tuple.

```python
from platform import platform, machine, processor, system, version, python_implementation, python_version_tuple

print(platform())
print(platform(True))
print(platform(False, True))
print(machine())
print(processor())
print(system())
print(version())
print(python_implementation())
print(python_version_tuple())
```



## Creating and Using User-defined Modules and Packages

Python is not just about using built-in modules; you can create your own!
- **Why?** Reuse code, organize large projects, and share functionality with others.
- **How?** Write code in separate files (modules) and directories (packages).

### The `__pycache__` Directory

- When you import a module, Python compiles it to bytecode (.pyc), which is stored in the `__pycache__` directory. 
  - The file name matches the module's name, along with the Python implementation that created it and its version number. 
- This speeds up subsequent imports.
- Example:
    ```
    mymodule.py
    __pycache__/
        mymodule.cpython-xy.pyc
    ```

### The `__name__` Variable

- Every module has a built-in `__name__` variable.
- When a file is run directly, `__name__ == "__main__"`.
- When imported, `__name__` is the module’s name.

**Typical usage:**
```python
# mymodule.py
def hello():
    print("Hello from mymodule!")

if __name__ == "__main__":
    hello()  # Only runs when executed directly, not when imported
```

### The `__init__.py` File
- A file with a unique name inside the directory indicates it as a Python package.
- The file's content is executed when any module in the package is imported. If you do not require any special initializations, you can leave the file empty.

### Searching for Modules/Packages (using `sys.path`)

- When you import, Python searches directories in `sys.path` in order.
- You can append/prepend directories to `sys.path` at runtime if needed:
    ```python
    import sys
    sys.path.append('/my/custom/path')
    ```

### Nested Packages vs. Directory Trees

- **Nested Packages:** Packages within packages, forming a tree structure.
- **Directory Trees:** The physical representation of your project's organization.

**Example:**
```
project/
    main.py
    mypackage/
        __init__.py
        module1.py
        subpackage/
            __init__.py
            module2.py
```
- To import `module2` from `main.py`:  
  ```python
  from mypackage.subpackage import module2
  ```

## Further Reading

- [Python Modules Documentation](https://docs.python.org/3/tutorial/modules.html)
- [Standard Python Modules]( https://docs.python.org/3/py-modindex.html.)
