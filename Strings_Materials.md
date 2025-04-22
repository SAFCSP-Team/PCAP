# Strings Materials

## 1. Understand the machine representation of characters

1. Computers store characters as numbers. There is more than one possible way of encoding characters, like **ASCII** (used mainly to encode the Latin alphabet and some of its derivates) and **UNICODE** (able to encode virtually all alphabets being used by humans).

2. A number corresponding to a particular character is called a **codepoint**.

3. UNICODE uses different ways of encoding when it comes to storing the characters using files or computer memory: two of them are **UCS-4** and **UTF-8**, which is the most common as it wastes less memory space.

### **Encoding Standards**

#### **ASCII (American Standard Code for Information Interchange)**  
- A 7-bit encoding standard that represents **128 characters**, including:
  - English uppercase and lowercase letters (A-Z, a-z)
  - Digits (0-9)
  - Common symbols (e.g., `@`, `#`, `!`)
  - Control characters (e.g., newline, tab).
- ASCII forms the basis for many modern encodings and is a subset of Unicode.

#### **UNICODE**  
- A universal standard designed to represent characters from almost all writing systems worldwide.
- Unicode assigns a **unique numeric value** (called a **code point**) to every character, ensuring compatibility across languages.
- Code points are written as `U+` followed by a hexadecimal value (e.g., `U+0041` for 'A').

#### **UTF-8**  
- A **variable-length encoding** for Unicode:
  - Uses **1 to 4 bytes** per character.
  - Backward-compatible with ASCII (ASCII characters are represented as single bytes in UTF-8).
  - Widely used on the web and in modern systems due to its efficiency and compatibility.

#### **UCS-4 (Universal Character Set - 4 bytes)**  
- A **fixed-length encoding** for Unicode, where every character is represented by exactly **4 bytes**.
- This allows UCS-4 to represent all Unicode code points directly without the need for variable-length encodings.
- UCS-4 simplifies the processing of characters because every character has the same size in memory. However, it is less efficient in terms of memory usage compared to UTF-8.

#### **Escape Sequences**: 
Special character representations in strings, starting with a backslash (`\`).

Examples:

  - `\n` - Newline
  - `\t` - Tab
  - `\\` - Backslash
  - `\'` - Single quote
  - `\"` - Double quote
  - `\uXXXX` - Unicode code point (e.g., `\u00A9` represents).

Example:
```python
# ASCII and Unicode representation
print(ord('A'))  # Output: 65 (ASCII code point)
print(chr(65))   # Output: A (character from code point)

# Escape sequences
print("Hello\nWorld")  # Output: Hello (newline) World
print("Unicode: \u0555")  # Output: Unicode: Օ
```


## 2. Operate on strings

### Functions:
- **`len(string)`**
  - **Parameters**: A string object.
  - **Return Value**: An integer representing the total number of characters in the string.
    
- **`ord(char)`**  
  - **Parameters**: A single character (string of length 1).  
  - **Return Value**: The Unicode code point of the character as an integer.  

- **`chr(code)`**  
  - **Parameters**: An integer representing a Unicode code point.  
  - **Return Value**: The character corresponding to the code point.  

Example:
```python
word = 'by'
print(len(word))  # Output: 2

empty = ''
print(len(empty))  # Output: 0

i_am = 'I\'m'
print(len(i_am))  # Output: 3
# The backslash (\) used as an escape character is not included in the string's total length.


print(ord('a'))  # Output: 97
print(chr(97))   # Output: a
```

### Concatenating and Multiplying Strings:
- **Concatenation**: Use the `+` operator to combine strings.
  - **Parameters**: Two or more strings.  
  - **Return Value**: New string containing all the characters from its arguments.  
  
- **Multiplication**: Use the `*` operator to repeat strings.
  - **Parameters**: a string and an integer  
  - **Return Value**:  A new string created by the nth replication of the string.  

Example:
```python
print("Hello" + " World")  # Output: Hello World
print("Hi" * 3)            # Output: HiHiHi
```

```
Note: Shortcut variants of the above operators are also applicable for strings (+= and *=).
```

### Indexing, Slicing, and Immutability:
- **Indexing**: Access individual characters in a string by specifying their position (index) that can be accessed using square brackets (`[]`).
  - **Zero-Based Indexing**: The first character of a string is at index `0`, the second at index `1`, etc.
  - **Negative Indexing**: Use negative indices to access characters from the end of a string: `-1` for the last character, `-2` for the second-to-last, and so on.
- **Slicing**: Extract substrings using the syntax `string[start:end:step]`.
- **Immutability**: Strings in Python are **immutable**, meaning that once a string is created, it cannot be modified. 

Example:
```python
word = "Python"
# Indexing
print(word[0])       # Output: P
print(word[-3])      # Output: h
print(word[10])      # Raises IndexError: string index out of range

# Slicing
print(word[1:4])     # Output: yth
print(word[::-1])    # Output: nohtyP
print(word[3:])      # Output: hon
print(word[:3])      # Output: Pyt
print(word[3:-1])    # Output: ho
print(word[-3:4])    # Output: h
print(word[1::2])    # Output: yhn

# Immutability
word[0] = "J"  # Raises TypeError: 'str' object does not support item assignment
```

### Iterating Through Strings:
- **For Loop**: Iterate through each character in a string.

Example:
```python
for char in "Hello":
    print(char)
```
```
H
e
l
l
o
```

### Operators: `in` and `not in`
- **`in`**: Checks if a substring exists within a string.  
- **`not in`**: Checks if a substring does not exist within a string.  

**Parameters**: A substring and a string.  
**Return Value**: Boolean (`True` or `False`).  

Example:
```python
sentence = "Welcome to Python"
print("Welcome" in sentence)      # Output: True
print("Hi" in sentence)           # Output: False
print("welcome" not in sentence)  # Output: True
print("Python" not in sentence)   # Output: False
```


## 3. Employ built-in string methods

#### `min()`: 
- Returns the smallest (minimum) character in a string based on its Unicode value.
- Compares characters based on their Unicode values.
- Works on non-empty strings; calling it on an empty string raises a ValueError.

Example:
```python
print(min("Python"))  # Output: P
# Unicode value of 'P' is smaller than other characters
```

#### `max()`: 
- Returns the largest (maximum) character in a string based on its Unicode value.
- Compares characters based on their Unicode values.
- Works on non-empty strings; calling it on an empty string raises a ValueError.

Example:
```python
print(max("Python"))  # Output: y
# Unicode value of 'y' is the largest.
```

#### `index()`:
- **Parameters**:
  - substring: The character or substring to search for.
  - start (optional): The starting position for the search.
  - end (optional): The ending position for the search.
- **Return Value**: The index (integer) of the first occurrence of the substring.  

Example:
```python
string = "Python Programming language"
print(string.index("P"))            # Output: 0  (first 'P' is at index 0)
print(string.index("o"))            # Output: 4  (first 'o' is at index 4)
print(string.index("Programming"))  # Output: 7  (substring starts at index 7)
print(string.index("g",16,-1))      # Output: 17 (first 'g'  in the range from index 16 to the second-to-last character)

print(string.index("z"))  # ValueError: substring not found
```

#### `list()`: 
- Converts a string into a list of its characters.
- Each character in the string becomes an element in the list, including whitespace and special characters.

Example:
```python
char_list = list("Python")
print(char_list)  # Output: ['P', 'y', 't', 'h', 'o', 'n']

string = "123 456"
list_numbers = list(string)
print(list_numbers)  # Output: ['1', '2', '3', ' ', '4', '5', '6']
```

#### `count()`:
- **Parameters**:
  - substring: The character or substring to count.
  - start (optional): The starting position for the search.
  - end (optional): The ending position for the search.
- **Return Value**: Returns the number of occurrences of a specified substring or character in a string.

Example:
```python
string = "Python Programming language"
print(string.count("g"))
print(string.count("g",18,-1))
print(string.count("Programming"))
```

#### `isxxx()` Methods:
- **Parameters**: None. Operates on the string itself.  
- **Return Value**: Boolean (`True` or `False`).  

Examples:
- **`isalpha()`**: Returns True if all characters are alphabetic.
- **`isdigit()`**: Returns True if all characters are digits.
- **`islower()`**: Returns True if all alphabetic characters are lowercase.
- **`isupper()`**: Returns True if all alphabetic characters are uppercase.
- **`isalnum()`**: Returns True if all characters are alphanumeric (letters and digits).
- **`isspace()`**: Returns True if all characters are whitespace.
  
Example:
```python
print("Hello".isalpha())  # Output: True
print("123".isdigit())    # Output: True
print("hello".islower())  # Output: True
print("HELLO".isupper())  # Output: True
print("abc123".isalnum()) # Output: True
print("   ".isspace())    # Output: True
```

#### `join()`
- **Parameters**: An iterable of strings (e.g., a list, tuple, etc.).  
- **Return Value**: A single string concatenated with the specified delimiter.  
- All the list's elements will be joined into one string, and the string from which the method has been invoked is used as a separator, put between the strings.
Example:
```python
words = ["Python", "is", "fun"]
print(" ".join(words))  # Output: Python is fun
print(",".join(words))  # Output: Python,is,fun
```

#### `split()`
- **Parameters**: A delimiter string (optional). The default is whitespace.  
- **Return Value**: A list of substrings.
  ```
  Note : The method assumes that the substrings are delimited by whitespaces - the spaces don't take part in the operation, and aren't copied into the resulting list.
  ```
  
Example:
```python
sentence = "Python is fun"
print(sentence.split())  # Output: ['Python', 'is', 'fun']
print("Python , is fun".split(","))  # Output: ['Python ', ' is fun']
```

#### `center()`
- **Parameters**: Width (integer), optional fill character (string, default is space).  
- **Return Value**: A new string centered within the specified width.

Example:
```python
word = "Hello"
print(word.center(10))  # Output: "  Hello   "
print(word.center(10, '*'))  # Output: "**Hello***"
```

#### `find()` and `rfind()`
Is similar to index(), it looks for a substring and returns the index of first occurrence of this substring, but it doesn't generate an error for a non-existent substring it returns -1.
- **`find()`**:  
  - **Parameters**: Substring, optional start and end indices.  
  - **Return Value**: The index of the **first** occurrence of the substring, or `-1` if not found.  

- **`rfind()`**:  
  - **Parameters**: Substring, optional start and end indices.  
  - **Return Value**: The index of the **last** occurrence of the substring, or `-1` if not found.  

Example:
```python
sentence = "Python Programming language"
print(sentence.find("o"))    # Output: 4 (first occurrence)
print(sentence.rfind("o"))   # Output: 9 (last occurrence)
```

#### `startswith()` and `endswith()`
- **`startswith()`**:
  - checks if a given string starts with the specified substring or character.
  - **Parameters**: A prefix string (can also accept a tuple of prefixes).
  - **Return Value**: Boolean (True or False), indicating if the string starts with the specified prefix.

- **`endswith()`**:
  - checks if a given string ends with the specified substring or character.
  - **Parameters:** A suffix string (can also accept a tuple of suffixes).
  - **Return Value:** Boolean (True or False), indicating if the string ends with the specified suffix.

Example:

```python
filename = "main.py"
print(filename.startswith("m"))     # Output: True
print(filename.startswith("main"))  # Output: True
print(filename.endswith(".py"))     # Output: True
print(filename.endswith("y"))       # Output: True
```

#### `sorted()` and `sort()`
- **`sorted()`**:
   - The function takes one argument (iterable) and returns a new list filled with the sorted argument's elements. 
  - **Parameters**: Iterable.  
  - **Return Value**: A new sorted list.

- **`sort()`**:
  - The method affects the list itself - no new list is created. 
  - **Parameters**: None.  
  - **Return Value**: None (modifies the list in-place).  

Example:
```python
words = ["banana", "apple", "cherry"]
sorted_function = sorted(words) 

print(sorted_function)      # Output: ['apple', 'banana', 'cherry']
print(words)                # Output: ['banana', 'apple', 'cherry']

sort_function = words.sort()
print(sort_function)        # Output: None
print(words)                # Output: ['apple', 'banana', 'cherry']
```

#### String Manipulation Methods
**The original string (from which the method is invoked) is not changed in any way; the modified  string is returned as a result.**

- **`strip()`**: Removes leading and trailing whitespace from the string.
- **`lstrip()`**: Removes leading whitespace (from the left).
  - The one-parameter lstrip() method does the same as its parameterless version, but removes all characters listed in its argument (a string), not just whitespace:
- **`rstrip()`**: Removes trailing whitespace (from the right). Do nearly the same as lstrips, but affect the opposite side of the string.
- **`replace(old, new)`**: Returns a new string where all occurrences of old are replaced with new.
- **`lower()`**: Converts all characters in the string to lowercase.
- **`upper()`**: Converts all characters in the string to uppercase.
- **`capitalize()`**: Capitalizes the first character of the string, and all remaining letters in the string will be converted to lower-case.
- **`title()`**: Capitalizes the first character of each word in the string, turning all other ones to lower-case.
- **`swapcase()`**: Swaps case; converts lowercase to uppercase and vice versa.

Example:
```python
text = "  Hello World!  "
print(text.strip())                       # Output: "Hello World!"
print(text.lstrip())                      # Output: "Hello World!  "
print("www.cisco.com".lstrip("w."))       # Output: "cisco.com"
print(text.rstrip())                      # Output: "  Hello World!"
print(text.replace("World", "Python"))    # Output: "  Hello Python!  "
print("HELLO".lower())                    # Output: "hello"
print("hello".upper())                    # Output: "HELLO"
print("hello World".capitalize())         # Output: "Hello world"
print("hello world".title())              # Output: "Hello World"
print("Hello World".swapcase())           # Output: "hELLO wORLD"
```
### For more information and additional methods, [click here](https://docs.python.org/3.4/library/stdtypes.html#string-methods).

## 4. Comparing Strings
Two strings are equal when they consist of the same characters in the same order.

Key point for comparing strings:  
- Compare the lengths of the strings; the longer string is greater.
- The final relationship between strings is determined by comparing the first different character in both strings (keep ASCII/UNICODE code points in mind at all times).
- String comparison is always case-sensitive (upper-case letters are taken as smaller than lower-case).
- Even if a string contains digits only, it's still not a number.

Example:
```python
print("alpha" < "alphabet")    # Output: True
print("Ahmad" < "Ahlam")       # Output: False
print("beta" > "Beta")         # Output: True
print ("O" == " o ")           # Output: False
print (10 != "10")             # Output: True

string1 = "Apple"
string2 = "apple"
print(string1.lower() == string2.lower()) # Output: True
```
