# Python Cheat Sheet

A beginner-friendly reference to Python 3, with clear explanations, syntax, practical examples and common mistakes.

## Contents

- [Getting started](#getting-started)
  - [What is Python?](#what-is-python)
  - [What can Python do?](#what-can-python-do)
  - [Why Python?](#why-python)
  - [Python syntax compared with other languages](#python-syntax-compared-with-other-languages)
  - [Interpreted vs compiled languages](#interpreted-vs-compiled-languages)
  - [Installing Python](#installing-python)
  - [Python quick start: Hello, World!](#python-quick-start-hello-world)
  - [The Python interactive interpreter (REPL)](#the-python-interactive-interpreter-repl)
  - [Comments, statements and output](#comments-statements-and-output)
- [Variables and scope](#variables-and-scope)
- [Built-in data types](#built-in-data-types)
- [Numbers and conversion](#numbers-and-conversion)
- [Strings](#strings)
- [Booleans](#booleans)
- [Operators](#operators)
- [Collections](#collections)
- [Lists](#lists)
- [Tuples](#tuples)
- [Sets and frozensets](#sets-and-frozensets)
- [Dictionaries](#dictionaries)
- [References](#references)

## Getting started

### What is Python?

Python is a general-purpose programming language created by Guido van Rossum and first released in 1991. It is designed to make programs easy to read and write.

### What can Python do?

- **Web development:** create server-side applications and APIs.
- **Software development:** build applications, tools and prototypes.
- **Automation and system scripting:** automate repetitive tasks and workflows.
- **Database and file management:** connect to databases and read, create or modify files.
- **Mathematics and data science:** analyse large datasets and perform scientific calculations.
- **Artificial intelligence:** develop machine learning and AI applications.

Python is suitable for both rapid prototyping and production software.

### Why Python?

- Runs on Linux, Windows, macOS and devices such as Raspberry Pi.
- Uses readable syntax that often resembles English.
- Often requires less code than languages such as C for the same task.
- Allows developers to run scripts without a separate manual compilation step.
- Supports procedural, object-oriented and functional programming styles.
- Has a large standard library and a wide ecosystem of third-party packages.

### Python syntax compared with other languages

Python uses newlines to separate most statements and indentation to group statements into blocks. Languages such as C commonly use semicolons to terminate statements and curly braces to define blocks.

Python:

```python
if True:
    print("Inside the block")
print("Outside the block")
```

C (inside a function):

```c
if (1) {
    printf("Inside the block\n");
}
printf("Outside the block\n");
```

In Python, indentation is required, not merely decorative. Use four spaces per indentation level (PEP 8). A colon introduces blocks such as those belonging to `if`, loops, functions and classes. Indentation defines blocks; not every block creates a separate variable scope.

### Interpreted vs compiled languages

Python is commonly described as an **interpreted language**. A program is written in a `.py` file and run using the Python interpreter. There is usually no separate manual compilation step.

C is commonly described as a **compiled language**. A compiler such as GCC translates C source code into an executable program before it is run.

| Python | C |
|---|---|
| Source file: `hello.py` | Source file: `hello.c` |
| Run: `python3 hello.py` | Compile: `gcc hello.c -o hello` |
| Interpreter executes the program | Run the executable: `./hello` (Linux/macOS) |

**Good to know:** CPython, the standard Python implementation, also compiles source code internally into bytecode before executing it. The practical difference for a beginner is that Python normally handles this automatically.

### Installing Python

Python 3 is the version to use for new projects. Download Python from [python.org](https://www.python.org/downloads/) if needed. On Linux, the distribution's package manager is also an option.

Check whether Python is installed by entering a command in a terminal (not inside the Python interpreter):

```bash
# Linux and macOS
python3 --version
```

```powershell
# Windows (depending on installation)
py --version
python --version
```

The commands `python`, `python3` and `py` depend on the operating system and installation. Use the one that reports a Python 3 version.

Python files can be written in any plain-text editor. Editors and integrated development environments (IDEs), such as Visual Studio Code, PyCharm and Thonny, provide features for editing, running and debugging programs.

### Python quick start: Hello, World!

1. Open a text editor.
2. Create a file called `hello.py`.
3. Write the following code and save the file:

```python
print("Hello, World!")
```

4. Open a terminal and navigate to the folder containing `hello.py`.
5. Run the file with the appropriate command for your system:

```bash
# Linux and macOS
python3 hello.py
```

```powershell
# Windows (use whichever command is available)
py hello.py
# or
python hello.py
```

Output:

```text
Hello, World!
```

`print()` is a built-in function that displays values on the screen. Text written directly in code must be enclosed in quotes to form a string literal.

### The Python interactive interpreter (REPL)

For short experiments, start Python without specifying a file:

```bash
python3
```

On Windows, use `py` or `python` if appropriate. The `>>>` prompt indicates that the interpreter is ready for Python code.

```pycon
>>> print("Hello, World!")
Hello, World!
>>> 2 + 3
5
>>> exit()
```

The REPL (Read-Evaluate-Print Loop) executes commands interactively. Use `exit()` to leave it. On Linux/macOS, Ctrl+D also exits; on Windows, use Ctrl+Z followed by Enter.

### Comments, statements and output

Comments begin with `#` and continue to the end of the line. Statements normally execute in order unless control flow changes that order.

```python
# This is a comment
print("Hello, World!")
print('Python is fun!')
print(42)
print("Python", 3, sep=" - ")  # Python - 3
print("Hello", end=" ")
print("developer")  # Hello developer (same line)
```

By default, `print()` separates arguments with a space and ends with a newline. Use `sep` and `end` to customise these behaviours.

## Variables and scope

Assignment binds a name to an object; the name can later refer to an object of a different type. Python identifiers are case-sensitive, cannot begin with a digit or be reserved keywords, and can contain underscores and valid Unicode identifier characters.

```python
course_name = "Python"
lesson_number = 10
print(type(lesson_number))  # <class 'int'>
lesson_number = "ten"
first, second = "Git", "Python"
a = b = 0
language, version = ("Python", 3)
```

Prefer `snake_case` for variables/functions, `PascalCase` for classes and `UPPER_CASE` for constants by convention. `camelCase` is valid but not the usual Python convention. Avoid names such as `list` or `str` that shadow built-ins.

A function can read module-level names. Assignment inside a function normally creates a local binding. `global` explicitly targets the module-level binding.

```python
status = "learning"


def show_status():
    status = "practising"
    print(status)


show_status()  # practising
print(status)  # learning


def update_status():
    global status
    status = "ready"


update_status()
print(status)  # ready
```

Prefer passing arguments and returning values when possible instead of modifying globals.

## Built-in data types

| Category | Type | Example |
|---|---|---|
| Text | `str` | `"Python"` |
| Numeric | `int`, `float`, `complex` | `42`, `2.5`, `2+3j` |
| Sequence | `list`, `tuple`, `range` | `[1, 2]`, `(1, 2)`, `range(3)` |
| Mapping | `dict` | `{"level": 1}` |
| Set | `set`, `frozenset` | `{1, 2}`, `frozenset([1, 2])` |
| Boolean | `bool` | `True`, `False` |
| Binary | `bytes`, `bytearray`, `memoryview` | `b"abc"`, `bytearray(3)`, `memoryview(b"abc")` |
| Absence | `NoneType` | `None` |

Use `type(value)` to inspect the exact type and `isinstance(value, cls)` to test type membership (including subclasses).

## Numbers and conversion

```python
whole = 42
fraction = 3.75
imaginary = 2 + 4j
print(float(whole))  # 42.0
print(int(fraction))  # 3
print(int(-3.75))  # -3 (truncates toward zero)
print(complex(whole))  # (42+0j)
print(str(whole))  # '42' as a string
print(int("42"))  # 42
```

Not all conversions are valid: `int("hello")` raises `ValueError`; `int(2+4j)` raises `TypeError`.

```python
import random

print(random.randrange(1, 10))  # integer from 1 through 9
```

## Strings

Strings are immutable sequences of Unicode code points. Python has no separate character type: indexing returns a string of length one.

```python
text = "Python developer"
print(text[0])       # P
print(text[-1])      # r
print(text[0:6])     # Python
print(text[:6])      # Python
print(text[7:])      # developer
print(text[-9:-1])   # develope
print(text[::-1])    # repoleved nohtyP
print(len(text))     # 16
print("Python" in text)  # True
print("java" not in text)  # True
```

Slices follow `sequence[start:stop:step]`; the stop index is excluded. Single and double quotes are interchangeable; triple quotes allow literal newlines.

```python
message = "It's Python"
paragraph = """First line
Second line"""
name = "Python"
price = 12.5
print(f"{name}: {price:.2f} EUR")  # Python: 12.50 EUR
print("{}: {:.2f} EUR".format(name, price))
print("Lesson " + str(10))
```

Escape sequences: `\n` newline, `\t` tab, `\r` carriage return, `\b` backspace, `\f` form feed, `\\` backslash, `\'` single quote, `\"` double quote, `\ooo` octal, `\xhh` hexadecimal.

### String methods

Methods do not mutate the original string. They may return strings, numbers, booleans, lists, tuples or bytes.

| Method(s) | Purpose |
|---|---|
| `capitalize`, `title` | Capitalize first character or words |
| `upper`, `lower`, `casefold`, `swapcase` | Change letter case; casefold supports caseless matching |
| `strip`, `lstrip`, `rstrip` | Remove whitespace (or specified characters) from edges |
| `center`, `ljust`, `rjust`, `zfill` | Pad to a specified width |
| `count` | Count non-overlapping substring matches |
| `find`, `rfind` | First/last match index, or `-1` |
| `index`, `rindex` | First/last match index; raise `ValueError` if absent |
| `startswith`, `endswith` | Test prefix/suffix |
| `replace` | Substitute substrings |
| `split`, `rsplit`, `splitlines` | Produce lists of substrings |
| `partition`, `rpartition` | Split at first/last separator into three parts |
| `join` | Combine iterable strings using a separator |
| `format`, `format_map` | Substitute formatted values |
| `encode` | Encode text into bytes |
| `expandtabs` | Expand tabs into spaces |
| `maketrans`, `translate` | Build/use a character translation mapping |
| `isalnum`, `isalpha`, `isascii` | Test character categories |
| `isdecimal`, `isdigit`, `isnumeric` | Test increasingly broad numeric character categories |
| `isidentifier`, `isprintable`, `isspace` | Test identifier form, printable characters, whitespace |
| `islower`, `isupper`, `istitle` | Test letter case patterns |

```python
raw = "  Git,Python  "
print(raw.strip().split(","))  # ['Git', 'Python']
print(" / ".join(["Git", "Python"]))  # Git / Python
print("Python".find("z"))  # -1
print("007".isdigit())  # True
```

## Booleans

`bool(value)` tests truthiness. Zero, empty containers, empty strings, `None` and `False` are falsy. Most other objects are truthy. Custom classes can implement `__bool__` or `__len__` to control truthiness.

```python
print(bool([]))  # False
print(bool("False"))  # True: non-empty string
print(bool(0))  # False
print(isinstance(42, int))  # True


def is_ready():
    return True


if is_ready():
    print("Ready")
else:
    print("Not ready")
```

## Operators

### Arithmetic

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `7 + 2` → `9` |
| `-` | Subtraction | `7 - 2` → `5` |
| `*` | Multiplication | `7 * 2` → `14` |
| `/` | True division | `7 / 2` → `3.5` |
| `//` | Floor division | `7 // 2` → `3` |
| `%` | Modulo | `7 % 2` → `1` |
| `**` | Exponentiation | `7 ** 2` → `49` |

Floor division rounds the quotient down toward negative infinity. For built-in `int` and `float` operands, it returns an integer if both are integers and a float if either is a float.

```python
print(10 // 3)       # 3
print(10.0 // 3)     # 3.0
print(-10 // 3)      # -4
print(int(-10 / 3))  # -3 (different from floor division)
```

### Assignment

`=` binds a name. Augmented assignment operators include `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`, `&=`, `|=`, `^=`, `<<=`, `>>=`. Augmented assignment can mutate an existing object, depending on its type.

The assignment expression `:=` (Python 3.8+) assigns and returns a value within an expression.

```python
count = 2
count += 3
if (size := len("Python")) > 4:
    print(size)  # 6
```

### Comparison, logic, identity and membership

| Category | Operators |
|---|---|
| Comparison | `==`, `!=`, `<`, `<=`, `>`, `>=` |
| Logical | `and`, `or`, `not` |
| Identity | `is`, `is not` |
| Membership | `in`, `not in` |

```python
x = [1, 2]
y = [1, 2]
print(x == y)  # True: equal values
print(x is y)  # False: distinct objects
print(2 in x)  # True
print("" or "default")  # default
print(3 and 7)  # 7
print(not 0)  # True
```

`and` and `or` short-circuit and return one operand; `not` returns a Boolean. Use `is None` to check for `None`, not `is` to compare numeric or string values.

A conditional expression selects one of two values:

```python
day = 6
label = "weekend" if day > 5 else "weekday"
```

### Bitwise operators

For integers, `&` is AND, `|` OR, `^` XOR, `~` complement, `<<` left shift, and `>>` right shift.

```python
print(6 & 3)  # 2
print(6 | 3)  # 7
print(6 ^ 3)  # 5
print(~6)     # -7
print(6 << 2) # 24
print(6 >> 1) # 3
```

Python integers have arbitrary precision: left shifts do not discard high bits. Right shifting by n is equivalent to floor division by `2 ** n`.

### Operator precedence

Parentheses explicitly group expressions. A simplified order (high to low) is: exponentiation, unary signs, multiplication/division/modulo, addition/subtraction, shifts, bitwise AND/XOR/OR, comparisons/identity/membership, `not`, `and`, `or`, conditional expression, assignment expression. Some syntax (including calls and indexing) binds more tightly than arithmetic.

```python
print(2 + 3 * 4)    # 14
print((2 + 3) * 4)  # 20
print(2 ** 3 ** 2)  # 512: exponentiation groups right to left
print(-2 ** 2)      # -4
print(1 < 2 < 3)    # True: chained comparison
```

## Collections

| Type | Ordered | Mutable | Duplicates |
|---|---|---|---|
| `list` | Yes | Yes | Yes |
| `tuple` | Yes | No | Yes |
| `set` | No guaranteed order | Yes | No |
| `frozenset` | No guaranteed order | No | No |
| `dict` | Insertion order (Python 3.7+) | Yes | Unique keys; repeated values allowed |

## Lists

```python
skills = ["Git", "Python", "Linux"]
print(skills[0])  # Git
print(skills[-1])  # Linux
print(skills[1:])  # ['Python', 'Linux']
print(len(skills))  # 3
skills[0] = "GitHub"
skills[1:2] = ["Python", "SQL"]
skills.insert(0, "Terminal")
skills.append("Testing")
skills.extend(["HTML", "CSS"])
skills.remove("HTML")
last = skills.pop()
del skills[0]
```

| Method | Purpose |
|---|---|
| `append(x)` | Add one object at the end |
| `extend(iterable)` | Append each item from an iterable |
| `insert(i, x)` | Insert before index i |
| `remove(x)` | Remove first equal item; error if absent |
| `pop(i=-1)` | Remove and return an item |
| `clear()` | Remove all items |
| `index(x)` | First matching index; error if absent |
| `count(x)` | Count matches |
| `copy()` | Shallow copy |
| `sort()` | Sort in place |
| `reverse()` | Reverse in place |

### Iteration and comprehensions

```python
skills = ["Git", "Python", "Linux"]
for skill in skills:
    print(skill)
for i in range(len(skills)):
    print(i, skills[i])
for i, skill in enumerate(skills):
    print(i, skill)
i = 0
while i < len(skills):
    print(skills[i])
    i += 1

lengths = [len(skill) for skill in skills]
filtered = [skill for skill in skills if len(skill) > 3]
print(lengths)   # [3, 6, 5]
print(filtered)  # ['Python', 'Linux']
```

Use ordinary loops for side effects such as printing. Comprehensions build collections.

### Sorting, copying and joining

```python
names = ["python", "Git", "Linux"]
print(sorted(names, key=str.lower))  # ['Git', 'Linux', 'python']
names.sort(key=str.lower, reverse=True)
names.reverse()
values = [12, 3, 8]
print(sorted(values, key=lambda n: abs(n - 10)))  # [12, 8, 3]
copy1 = names.copy()
copy2 = list(names)
copy3 = names[:]
combined = [1, 2] + [3, 4]
```

`sort()` mutates the list and returns `None`; `sorted()` returns a new list. Assignment is not copying. Shallow copies share nested objects.

```python
original = [[1], [2]]
alias = original
shallow = original.copy()
shallow[0].append(3)
print(original)  # [[1, 3], [2]]
```

## Tuples

Tuples are immutable sequences: their element references cannot be replaced, though referenced mutable objects can still change.

```python
point = (3, 4)
x, y = point
single = (42,)
not_tuple = (42)
print(type(single))  # <class 'tuple'>
print(point[-1])  # 4
print(point[:1])  # (3,)
print(3 in point)  # True
new_point = point + (5,)
print(new_point * 2)  # (3, 4, 5, 3, 4, 5)
first, *remaining = new_point
print(remaining)  # [4, 5]
print((1, 2, 1).count(1))  # 2
print(point.index(4))  # 1
```

Use `tuple(iterable)` to construct a tuple. Converting to a list, editing, and converting back creates a new tuple rather than modifying the original. Tuples support the same iteration patterns as lists.

## Sets and frozensets

Sets hold unique hashable elements. They are mutable but do not support indexing or slicing. Use `set()` for an empty set: `{}` creates a dictionary.

```python
skills = {"Git", "Python", "Git"}
skills.add("Linux")
skills.update(["SQL", "Python"])
skills.discard("Java")  # no error if missing
skills.remove("SQL")   # raises KeyError if missing
print("Python" in skills)  # True
for skill in sorted(skills):
    print(skill)
```

`pop()` removes an arbitrary element; `clear()` empties the set; `copy()` makes a shallow copy. Never depend on set iteration order.

| Operation | Method | Operator |
|---|---|---|
| Union | `a.union(b)` | `a \| b` |
| Intersection | `a.intersection(b)` | `a & b` |
| Difference | `a.difference(b)` | `a - b` |
| Symmetric difference | `a.symmetric_difference(b)` | `a ^ b` |
| Subset | `a.issubset(b)` | `a <= b` |
| Superset | `a.issuperset(b)` | `a >= b` |
| Disjoint | `a.isdisjoint(b)` | — |

```python
a = {1, 2, 3}
b = {2, 3, 4}
assert a | b == {1, 2, 3, 4}
assert a & b == {2, 3}
assert a - b == {1}
assert a ^ b == {1, 4}
```

Methods such as `union()` accept other iterables, whereas the corresponding set operators generally require set-like operands. In-place variants include `update`, `intersection_update`, `difference_update`, `symmetric_difference_update`.

A `frozenset` is immutable and hashable. It supports non-mutating set operations but not `add`, `remove` or update methods.

```python
fixed = frozenset([1, 2, 2])
assert fixed == frozenset({1, 2})
assert fixed.union([3]) == frozenset({1, 2, 3})
```

## Dictionaries

Dictionaries map unique hashable keys to values and preserve insertion order. Updating an existing key changes its value without moving its position.

```python
course = {"name": "Python", "lesson": 10}
print(course["name"])  # Python
print(course.get("status", "unknown"))  # unknown
course["lesson"] = 11
course.update({"status": "learning"})
print("name" in course)  # True: checks keys
```

| Method | Purpose |
|---|---|
| `get(key, default)` | Retrieve value or fallback |
| `keys()`, `values()`, `items()` | Dynamic views of keys, values and pairs |
| `update(mapping)` | Add or overwrite entries |
| `setdefault(key, default)` | Retrieve value or insert default |
| `pop(key)` | Remove key and return value |
| `popitem()` | Remove and return last inserted pair (3.7+) |
| `clear()` | Empty dictionary |
| `copy()` | Shallow copy |
| `fromkeys(iterable, value)` | Construct mapping with shared default value |

```python
course = {"name": "Python", "lesson": 11, "status": "learning"}
for key, value in course.items():
    print(key, value)
backup = course.copy()
removed = course.pop("status")
del course["lesson"]
```

### Nested dictionaries

```python
projects = {
    "portfolio": {"language": "Python", "completed": False},
    "calculator": {"language": "Python", "completed": True},
}
print(projects["portfolio"]["language"])  # Python
for project, details in projects.items():
    for key, value in details.items():
        print(project, key, value)
```

