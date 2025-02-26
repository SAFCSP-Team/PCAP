# Miscellaneous Materials
## 1. yield Keyword
Definition: The yield keyword is used to produce a value in a generator function.

Scope: Generator functions
Example:
```python
def infinite_sequence():
    num = 0
    while True:
        yield num
        num += 1
#call
gen = infinite_sequence()
print(next(gen))  # prints 0
print(next(gen))  # prints 1
print(next(gen))  # prints 2
print(next(gen))  # prints 3
``` 
Example2: 
```python
def fibonacci_generator(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b
#call
fib_gen = fibonacci_generator(5)
for num in fib_gen:
    print(num)
#output
# 0
# 1
# 1
# 2
# 3
```
## 2. Build complex lists using list comprehension
- **List comprehensions:** A concise way to create lists in Python, combining loops and conditional logic into a single line.
- **Syntax:** `[expression for item in iterable if condition]`
- **Nested comprehensions:** A concise way to create lists that contain other lists, often with multiple levels of nesting.
- **Syntax:**`[[expression for item in inner_list] for inner_list in outer_list]`

```python
# Basic list comprehension
squares = [x**2 for x in range(10)]
print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# List comprehension with if condition
even_squares = [x**2 for x in range(10) if x % 2 == 0]
print(even_squares)  # Output: [0, 4, 16, 36, 64]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
print(flattened)  # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## 3. Embed lambda functions into the code
- **Lambda functions:** Anonymous inline functions are defined using the `lambda` keyword and are typically used for short, simple operations.
- **Syntax:** `lambda arguments: expression`
- **Usage with `map()` and `filter()`:** Lambdas are often used with `map()` to apply a function to all items in an iterable and with `filter()` to filter items based on a condition.

### map() function:
- Purpose: `map()` function applies a given function to each item of an iterable (e.g., list, tuple, set) and returns a new iterator with the results.
- Parameters: `map()` 
    - function: The function that you want to apply to each item in the iterable.
    - Iterables: The iterable(s) that you want to process using the given function.
- Return Value: It returns a map object (an iterator).

### filter() function:
- Purpose: `filter()` function constructs a new iterable from elements of the given iterable for which a function returns true.
- Parameters:
    - function: The function that returns True or False based on a condition.
    - iterable: The iterable that you want to filter based on the condition specified by the function.
- Return Value: It returns a filter object (an iterator).

Example:
```python
## Regular function
def add(x, y):
return x + y

## Equivalent lambda function
add_lambda = lambda x, y: x + y

print(add(2, 3)) # Output: 5
print(add_lambda(2, 3)) # Output: 5

# a self-defined function that takes a lambda function as an argument.
def apply_function(func, value1,value2):
    return func(value1, value2)

# Use the self-defined function with the lambda function
result = apply_function(add_lambda,5,3)
print(result)  # Output: 8

# Using lambda with map()
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # Output: [1, 4, 9, 16, 25]

# Using lambda with filter()
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [2, 4]
```

## 4. Define and use closures
A closure is a nested function that remembers and has access to the variables of its enclosing scope, even after the enclosing scope has finished execution.

It is simply a technique that can store values even if the context in which they have been created does not exist anymore.

```python
def tag(tg):
    # variable defined outside the inner function
    tg2= tg[0]+'/'+tg[1:]

    # inner function
    def inner(str):
        return tg + str + tg2 

    return inner

# call the outer function
b_tag = tag("<b>")

# call the inner function
print(b_tag("python"))
```

## 5. Basic Input/Output terminology & File handling

1. **I/O Modes**:
   - **Text Mode**: In text mode, data is read or written as a sequence of characters. Text mode handles end-of-line characters (like `\n`) in a platform-specific way.
   - **Binary Mode**: In binary mode, data is read or written as a sequence of bytes, which is more suitable for non-text data.

2. **Predefined Streams**:
   - **Standard Input (stdin)**: It is used for reading input from the user (e.g., using `input()` function).
   - **Standard Output (stdout)**: It is used for displaying output to the user (e.g., using `print()` function).
   - **Standard Error (stderr)**: It is used for displaying error messages or warnings separately from regular output.

3. **Handles vs. Streams**:
   - **Handles**: Handles are unique identifiers that represent an open file or I/O device. They are used to access files or devices for reading or writing data.
   - **Streams**: Streams are flows of data between a program and an I/O device or file. They provide a way to read or write data in a sequential manner.

4. **Text vs. Binary Modes**:
When working with text data, you typically use the text modes (rt, wt, at, r+t, w+t), and when dealing with binary data, you use the binary modes (rb, wb, ab, r+b, w+b).

- **Text Modes**:
   - **`rt` (Read Text Mode)**: Opens a file for reading in text mode. The file must exist.
   - **`wt` (Write Text Mode)**: Opens a file for writing in text mode. It truncates the file if it exists or creates a new file.
   - **`at` (Append Text Mode)**: Opens a file for appending in text mode. It creates a new file if it does not exist.
   - **`r+t` (Read/Write Text Mode)**: Opens a file for reading and writing in text mode. The file must exist.
   - **`w+t` (Write/Read Text Mode)**: Opens a file for reading and writing in text mode. It truncates the file if it exists or creates a new file.

- **Binary Modes**:
   - **`rb` (Read Binary Mode)**: Opens a file for reading in binary mode. The file must exist.
   - **`wb` (Write Binary Mode)**: Opens a file for writing in binary mode. It truncates the file if it exists or creates a new file.
   - **`ab` (Append Binary Mode)**: Opens a file for appending in binary mode. It creates a new file if it does not exist.
   - **`r+b` (Read/Write Binary Mode)**: Opens a file for reading and writing in binary mode. The file must exist.
   - **`w+b` (Write/Read Binary Mode)**: Opens a file for reading and writing in binary mode. It truncates the file if it exists or creates a new file.

```python
# Writing to a file in text mode
with open("example.txt", "wt") as file:
    file.write("Hello, World!")

# Reading from a file in text mode
with open("example.txt", "rt") as file:
    content = file.read()
    print(content)
```

## 5. Perform Input/Output operations
- **`open()` function:** Opens a file and returns a file object.
    - Parameters:
        - **`file`**: The name of the file to be opened. It can be a relative or absolute file path.
        - **`mode`**: A string specifying the file mode, such as `'r'` for read mode, `'w'` for write mode, etc.
        - **`encoding`** (optional): The encoding to be used for reading or writing text data. For example, `'utf-8'`.
        - **`errors`** (optional): Specifies how encoding and decoding errors are handled.
        - **`newline`** (optional): Controls how universal newlines mode works (only in text mode).
    - Return Value:
      - A file object, which represents the opened file.

- **`read()` method:** Reads the contents of a file. It allows you to retrieve the data stored in the file and process it in your program.
    - Parameters:
        - **`size`** (optional): The number of bytes to read from the file. If no size is specified, it reads the entire content of the file.
    - Return Value:
      - Returns a string (in text mode) or bytes object (in binary mode) containing the contents of the file.

Example:
```python
# Open a file in read mode
with open("example.txt", "r") as file:
    # Read the entire content of the file
    content = file.read()
    print(content)
```
- **`readline()` method:**
Reads a single line from a file, starting from the current file position. It allows you to read and process lines of text data one by one from a file.
  - Parameters:
    - **`size`** (optional): The number of bytes to read from the line. If no size is specified, it reads the whole line.
  - Return Value:
    - Returns a string containing the line of text read from the file, including the newline character at the end of the line. If the end of the file is reached, an empty string (`''`) is returned.

Example:
```python
# Open a file in read mode
with open("example.txt", "r") as file:
    # Read and print the first line
    line1 = file.readline()
    print(line1)

    # Read and print the second line
    line2 = file.readline()
    print(line2)
```

- **`readlines()` method:** Reads all lines from a file and return them as a list of strings.
  - Parameters:
    - **`size`** (optional): The maximum number of bytes to read from the file. If no size is specified, it reads the entire content of the file.
  - Return Value:
    - Returns a list of strings (in text mode) or bytes objects (in binary mode) containing the lines.

Example :
```python
# Open a file in read mode
with open("example.txt", "r") as file:
    # Read all lines from the file
    lines = file.readlines()
    
    # Print each line
    for line in lines:
        print(line)
```

- **`write()` method:** Writes a data to a file, allowing you to store information, text, or binary data in the file.
  - Parameters:
    - **`data`**: The data that you want to write to the file. The data can be in the form of a string (in text mode) or bytes (in binary mode).
  - Return Value:
    - Returns the number of bytes written to the file.

Example:
```python
# Open a file in write mode
with open("example.txt", "w") as file:
    # Write a string to the file
    file.write("Hello, World!")
```

- **`close()` method:** Closes a file.
  - Parameters:
    - The function does not take any parameters. It is simply called on a file object to close the file.
  - Return Value:
    - The function does not return a value.

Example:
```python
# Open a file in read mode
with open("example.txt", "r") as file:
# Read and print the first line
line1 = file.readline()
print(line1)
# Close the file
file.close()
```
```
Note: When the `with` statement is used, the file is automatically closed at the end of the block. 
```

#### IOErroe 
The IOError exception object, created when any file operations fails , contains a property named `errno`, which contains the completion code of the failed action.
```
Note: In Python 3, IOError is simply another name for OSError.
```
  - errno.EACCES : Permission denied

    The error occurs when you try, for example, to open a file with the read only attribute for writing.

  - errno.EBADF : Bad file number

    The error occurs when you try, for example, to operate with an unopened stream.

  - errno.EEXIST : File exists

    The error occurs when you try, for example, to rename a file with its previous name.

  - errno.EFBIG : File too large

     The error occurs when you try to create a file that is larger than the maximum allowed by the operating system.

  - errno.EISDIR : Is a directory

     The error occurs when you try to treat a directory name as the name of an ordinary file.

  - errno.EMFILE : Too many open files

     The error occurs when you try to simultaneously open more streams than acceptable for your operating system.

  - errno.ENOENT : No such file or directory

    The error occurs when you try to access a non-existent file/directory.

  - errno.ENOSPC : No space left on device

    The error occurs when there is no free space on the media.


#### bytearray
it's an array containing bytes, and not allowed to assign a value that doesn't come from the range 0 to 255 inclusive.
for example, to read a bitmap image and process it in any way, you need to create bytearray object.

- How to write a byte array for a binary file?
    - First, we initialize bytearray. 
    - Then, we create the file using the open() function whih mode containing the b flag.
    - the write() method takes its argument (bytearray) and sends it to the file.

```python
# Create a byte array
byte_array = bytearray([65, 66, 67, 68, 69])

# Open a binary file in write mode
with open("binary_file.bin", "wb") as file:
    # Write the byte array to the file
    file.write(byte_array)
```
- How to read bytes from a stream ? 
1. `readinto()` method :

Read bytes from a stream, such as a file object, directly into a pre-allocated buffer, such as a bytearray object. 
  - Parameters:
    - `buffer` : The bytearray object to read into.
  - Return Value:
    - The `readinto()` method returns the number of bytes read and stored in the buffer.

Example  
```python
# Open a file in binary read mode
with open("binary_file.bin", "rb") as file:
    # Create a bytearray to store the read bytes
    buffer = bytearray(10)  # Allocate a buffer of size 10

    # Read bytes into the buffer
    bytes_read = file.readinto(buffer)
```
2. `read()` method :

An alternative way of reading the contents of a binary file is offered by the method named read().

Invoked without arguments,  to read all the contents or with an argument, to specify the maximum number of bytes to be read into the memory, making them a part of a newly created object of the bytes class.

```
Note : don't use this kind of read if you're not sure that the file's contents will fit the available memory.
```

Example  
```python
# Open a file stream in binary read mode
with open("binary_file.bin", "rb") as file:
    # Read a specific number of bytes (e.g., 5 bytes)
    read_bytes = file.read(5)
    print("Bytes read:", read_bytes)

    # Read all bytes from the file
    all_bytes = file.read()
    print("All bytes read:", all_bytes)
```
