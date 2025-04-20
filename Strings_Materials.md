# Strings Materials

## 1. Understand the machine representation of characters

- **Encoding Standards**: Encoding standards define how characters are represented in memory as sequences of bytes.
  - **ASCII**: A 7-bit encoding standard representing 128 characters, including English letters, digits, and symbols.
  - **UNICODE**: A universal character encoding standard supporting characters from almost all writing systems.
  - **UTF-8**: A variable-length encoding for Unicode that uses 1-4 bytes per character. It is backward-compatible with ASCII.
  - **Code Points**: Numeric values assigned to each character in the Unicode standard (e.g., 'A' has code point `U+0041`).
  - **Escape Sequences**: Special character representations in strings, starting with a backslash (`\`). Examples:
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
- **`ord(char)`**  
  - **Parameters**: A single character (string of length 1).  
  - **Return Value**: The Unicode code point of the character as an integer.  

- **`chr(code)`**  
  - **Parameters**: An integer representing a Unicode code point.  
  - **Return Value**: The character corresponding to the code point.  

Example:
```python
print(ord('a'))  # Output: 97
print(chr(97))   # Output: a
```

### Indexing, Slicing, and Immutability:
- **Indexing**: Access individual characters using their position.
- **Slicing**: Extract substrings using the syntax `string[start:end:step]`.
- **Immutability**: Strings cannot be modified after creation.

Example:
```python
word = "Python"
print(word[0])       # Output: P
print(word[-1])      # Output: n
print(word[1:4])     # Output: yth
print(word[::-1])    # Output: nohtyP
```

### Iterating Through Strings:
- **For Loop**: Iterate through each character in a string.

Example:
```python
for char in "Hello":
    print(char)
```

### Concatenating and Multiplying Strings:
- **Concatenation**: Use the `+` operator to combine strings.
- **Multiplication**: Use the `*` operator to repeat strings.

Example:
```python
print("Hello" + " World")  # Output: Hello World
print("Hi" * 3)           # Output: HiHiHi
```

### Comparing Strings:
- **Parameters**: Two strings (or one string and one number).  
- **Return Value**: Boolean (`True` or `False`) based on lexicographical comparison or equality.  

Example:
```python
print("apple" < "banana")  # Output: True (lexicographical order)
print("123" == 123)        # Output: False (string vs number)
```

### Operators: `in` and `not in`
- **`in`**: Checks if a substring exists within a string.  
- **`not in`**: Checks if a substring does not exist within a string.  

**Parameters**: A substring and a string.  
**Return Value**: Boolean (`True` or `False`).  

Example:
```python
sentence = "The quick brown fox"
print("quick" in sentence)   # Output: True
print("slow" not in sentence)  # Output: True
```



## 3. Employ built-in string methods

### `isxxx()` Methods:
- **Parameters**: None. Operates on the string itself.  
- **Return Value**: Boolean (`True` or `False`).  

Examples:
- `.isalpha()`: Returns `True` if all characters are alphabetic.
- `.isdigit()`: Returns `True` if all characters are digits.
- `.islower()`: Returns `True` if all alphabetic characters are lowercase.

Example:
```python
print("Hello".isalpha())  # Output: True
print("123".isdigit())    # Output: True
print("hello".islower())  # Output: True
```



### `.join()`
- **Parameters**: An iterable of strings (e.g., a list, tuple, etc.).  
- **Return Value**: A single string concatenated with the specified delimiter.  

Example:
```python
words = ["Python", "is", "fun"]
print(" ".join(words))  # Output: Python is fun
```



### `.split()`
- **Parameters**: A delimiter string (optional). Default is whitespace.  
- **Return Value**: A list of substrings.  

Example:
```python
sentence = "Python is fun"
print(sentence.split())  # Output: ['Python', 'is', 'fun']
```



### `.sort()` and `sorted()`
- **`.sort()`**:  
  - **Parameters**: Optional `key` (function) and `reverse` (Boolean).  
  - **Return Value**: None (modifies the list in-place).  

- **`sorted()`**:  
  - **Parameters**: Iterable, optional `key` (function) and `reverse` (Boolean).  
  - **Return Value**: A new sorted list.  

Example:
```python
words = ["banana", "apple", "cherry"]
words.sort()
print(words)  # Output: ['apple', 'banana', 'cherry']

numbers = [3, 1, 2]
print(sorted(numbers))  # Output: [1, 2, 3]
```


### `.index()`
- **Parameters**: Substring, optional start and end indices.  
- **Return Value**: The index (integer) of the first occurrence of the substring.  
- **Raises**: `ValueError` if the substring is not found.  

Example:
```python
sentence = "The quick brown fox"
print(sentence.index("quick"))  # Output: 4
```


### `.find()` and `.rfind()`
- **`.find()`**:  
  - **Parameters**: Substring, optional start and end indices.  
  - **Return Value**: The index of the first occurrence of the substring, or `-1` if not found.  

- **`.rfind()`**:  
  - **Parameters**: Substring, optional start and end indices.  
  - **Return Value**: The index of the last occurrence of the substring, or `-1` if not found.  

Example:
```python
sentence = "The quick brown fox jumps over the lazy dog"
print(sentence.find("o"))    # Output: 12 (first occurrence)
print(sentence.rfind("o"))   # Output: 42 (last occurrence)
```

