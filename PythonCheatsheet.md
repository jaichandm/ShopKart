
Conversation with Gemini
give python cheet sheet

A quick-reference Python cheat sheet covering core syntax, data structures, and common idioms.

Basics & Types
Python
# Basic assignments & types
x = 42              # int
pi = 3.14159        # float
name = "Alex"       # str
active = True       # bool (True or False)
empty = None        # NoneType

# Type conversion
int("10")           # 10
float(5)            # 5.0
str(100)            # '100'
type(x)             # <class 'int'>

# String formatting (f-strings)
msg = f"User {name} has score: {pi:.2f}"  # 'User Alex has score: 3.14'
Data Structures
Python
# List (mutable, ordered)
nums = [1, 2, 3]
nums.append(4)          # [1, 2, 3, 4]
nums.extend([5, 6])     # [1, 2, 3, 4, 5, 6]
item = nums.pop()       # removes and returns 6
nums[0:2]               # slicing: [1, 2]
nums[::-1]              # reversed: [5, 4, 3, 2, 1]

# Tuple (immutable, ordered)
point = (10, 20)
x, y = point            # unpacking: x=10, y=20

# Dictionary (key-value, ordered by insertion)
user = {"name": "Alex", "age": 28}
val = user.get("city", "Unknown")  # safe access with default
user["role"] = "Admin"             # insert/update
for k, v in user.items():          # iterate keys and values
    print(k, v)

# Set (unique, unordered)
tags = {"python", "ai", "web"}
tags.add("cloud")
union = tags | {"docker", "ai"}
intersect = tags & {"python", "c++"}
Control Flow
Python
# Conditionals
if score >= 90:
    grade = "A"
elif score >= 75:
    grade = "B"
else:
    grade = "C"

# Ternary operator
status = "Adult" if age >= 18 else "Minor"

# Loops
for i in range(5):          # 0, 1, 2, 3, 4
    pass

for idx, val in enumerate(["a", "b"]):
    print(idx, val)         # 0 'a', 1 'b'

while count > 0:
    count -= 1
    if count == 2:
        break               # exits loop
Comprehensions
Python
# List comprehension
evens = [x for x in range(10) if x % 2 == 0]

# Dict comprehension
square_map = {x: x**2 for x in range(5)}

# Set comprehension
unique_lengths = {len(w) for w in ["apple", "pear", "banana"]}
Functions & Lambdas
Python
# Standard function with defaults and type hints
def greet(name: str, shout: bool = False) -> str:
    return name.upper() if shout else name

# Variable arguments (*args, **kwargs)
def collect(*args, **kwargs):
    # args is a tuple, kwargs is a dict
    return sum(args), kwargs.get("multiplier", 1)

# Lambda
multiply = lambda a, b: a * b
File Handling & Exceptions
Python
# File I/O using context manager
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("Line 1\n")

with open("data.txt", "r", encoding="utf-8") as f:
    lines = f.readlines()

# Exception handling
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
except Exception as e:
    print(f"General error: {e}")
else:
    print("Runs if no exception")
finally:
    print("Always runs")
Classes & OOP
Python
class User:
    def __init__(self, username: str):
        self.username = username
        self._score = 0     # convention for protected

    def add_score(self, points: int):
        self._score += points

    def __str__(self):
        return f"User({self.username}, score={self._score})"

# Dataclass (cleaner model definitions)
from dataclasses import dataclass

@dataclass
class Item:
    name: str
    price: float
    in_stock: bool = True
Built-in Cheats
Function	What it does	Example
zip(a, b)	Combines iterables pairwise	list(zip([1,2], ['a','b'])) -> [(1,'a'), (2,'b')]
enumerate(seq)	Generates (index, value)	for i, x in enumerate(items):
sorted(seq, key=...)	Returns new sorted list	sorted(words, key=len)
any(seq) / all(seq)	Checks truthiness	all([True, False]) -> False
map(func, seq)	Applies func to elements	list(map(str, [1, 2])) -> ['1', '2']
filter(func, seq)	Keeps truthy evaluations	list(filter(lambda x: x > 0, [-1, 2])) -> [2]
Want a focused cheat sheet on Python collections, OOP, or file/API operations?

Yes
also provide print all parameters

Here are all the parameters for Python’s built-in print() function:

Function Signature
Python
print(*objects, sep=' ', end='\n', file=None, flush=False)
Parameter Breakdown
Parameter	Type / Default	Description	Example
*objects	Any	Zero or more objects to print. Python automatically converts them to strings using str().	print("A", 1, [2, 3])
sep	str | None (default: ' ')	String inserted between multiple objects. Set to "" or custom characters.	
print(1, 2, 3, sep="-")


# 1-2-3

end	str | None (default: '\n')	String appended at the very end after the last object. Set to "" or ' ' to avoid a newline.	print("Loading...", end="")
file	file-like object (default: sys.stdout)	Target output stream. Can be an open writable file, sys.stderr, or an io.StringIO buffer.	print("Log", file=open("app.log", "a"))
flush	bool (default: False)	If True, forcibly flushes the output stream buffer immediately rather than waiting for buffer fill/newline.	print("Processing...", flush=True)
Practical Examples
Python
import sys
import time

# 1. Using 'sep' (joining items)
print("2026", "09", "07", sep="-")
# Output: 2026-09-07

print("user", "domain.com", sep="@")
# Output: user@domain.com


# 2. Using 'end' (printing on the same line)
for i in range(3):
    print(i, end=" -> ")
print("done")
# Output: 0 -> 1 -> 2 -> done


# 3. Using 'flush' (live countdown/progress bar)
for i in range(3, 0, -1):
    print(f"\rStarting in {i}...", end="", flush=True)
    time.sleep(1)
print("\rGo!          ")


# 4. Using 'file' (redirecting output)
# To standard error (stderr)
print("Warning: Missing config key", file=sys.stderr)

# Directly to a file
with open("output.txt", "w", encoding="utf-8") as f:
    print("Report summary", 2026, sep=": ", file=f)
now compile all and form a proper notes with comments easy to understand in short time

A consolidated, structured Python quick-study guide with inline comments for fast review.

Core Syntax & Primitive Types
Python
# Variables are dynamically typed
x = 42              # int
pi = 3.14159        # float
name = "Dev"        # str
is_active = True    # bool (Capital T / F)
empty_val = None    # NoneType (Python's null)

# Explicit type conversion
num = int("10")     # converts string to int -> 10
flt = float(5)      # converts int to float -> 5.0
txt = str(100)      # converts int to string -> '100'

# f-strings: dynamic interpolation and decimal precision
greeting = f"User {name} has score: {pi:.2f}"  # 'User Dev has score: 3.14'
print() Parameters Mastered
Signature: print(*objects, sep=' ', end='\n', file=None, flush=False)

Python
import sys

# *objects: Any number of comma-separated values
print("A", 1, True)

# sep: Custom separator between objects (default: ' ')
print("2026", "09", "07", sep="-")             # Output: 2026-09-07

# end: What prints after the line (default: '\n' for newline)
print("Loading", end="...")                    # Keeps next print on same line
print("Done")                                  # Output: Loading...Done

# flush: Force immediate terminal update (useful for real-time progress)
print("Updating...", end="", flush=True)

# file: Direct output to streams (sys.stderr) or files
print("Warning: Check logs!", file=sys.stderr)
with open("log.txt", "w") as f:
    print("Log Entry #1", file=f)
Data Structures
Python
# 1. LIST: Ordered, mutable, allows duplicates
nums = [1, 2, 3]
nums.append(4)          # [1, 2, 3, 4]
nums.pop()              # Removes & returns last item: 4
first_two = nums[0:2]   # Slicing: [1, 2]
reversed_nums = nums[::-1] # Reverse: [3, 2, 1]

# 2. TUPLE: Ordered, immutable (cannot change values)
coords = (10, 20)
x_pos, y_pos = coords   # Unpacking: x_pos=10, y_pos=20

# 3. DICTIONARY: Key-value store, preserves insertion order
user = {"name": "Alex", "age": 28}
city = user.get("city", "N/A")  # Safe fetch: returns 'N/A' if key missing
user["role"] = "Admin"          # Insert / update
for k, v in user.items():       # Iterate key and value simultaneously
    print(k, v)

# 4. SET: Unordered, unique elements only
tags = {"python", "ai", "web"}
tags.add("cloud")
union_set = tags | {"docker", "ai"}        # Merge unique values
common_set = tags & {"python", "c++"}     # Intersection: {'python'}
Control Flow & Loops
Python
# Conditionals
score = 85
if score >= 90:
    grade = "A"
elif score >= 75:
    grade = "B"
else:
    grade = "C"

# Ternary (single-line if-else)
status = "Pass" if score >= 50 else "Fail"

# Iterating with index using enumerate()
for idx, item in enumerate(["alpha", "beta"]):
    print(f"Index {idx}: {item}")

# While loop with break/continue
count = 3
while count > 0:
    count -= 1
    if count == 1:
        continue        # Skip this iteration
Comprehensions
Python
# List comprehension: [expression for item in iterable if condition]
evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]

# Dict comprehension: {key: value for item in iterable}
squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}

# Set comprehension: {expression for item in iterable}
word_lens = {len(w) for w in ["apple", "pear", "banana"]}
Functions, *args, & **kwargs
Python
# Default arguments & type annotations
def calculate_area(width: float, height: float = 1.0) -> float:
    return width * height

# *args gathers positional args into a tuple; **kwargs gathers named args into a dict
def demo_args(*args, **kwargs):
    print("Positional:", args)      # (1, 2)
    print("Keyword:", kwargs)       # {'mode': 'fast'}

demo_args(1, 2, mode="fast")

# Lambda (one-line anonymous function)
double = lambda x: x * 2
File I/O & Error Handling
Python
# Context manager 'with' handles automatic file closing
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("Line 1\nLine 2")

with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

# Exception handling
try:
    result = 10 / 0
except ZeroDivisionError as err:
    print("Math error:", err)
except Exception as err:
    print("Other error:", err)
else:
    print("Runs only if no error occurred")
finally:
    print("Always runs (for cleanup)")
Classes & Dataclasses
Python
# Standard OOP
class BankAccount:
    def __init__(self, owner: str, balance: float = 0.0):
        self.owner = owner          # Public attribute
        self._balance = balance     # Protected by convention

    def deposit(self, amount: float):
        self._balance += amount

    def __str__(self):
        return f"Account({self.owner}, Balance: {self._balance})"

# Dataclasses (auto-generates __init__, __repr__, and comparisons)
from dataclasses import dataclass

@dataclass
class Product:
    name: str
    price: float
    in_stock: bool = True
High-Utility Built-ins
Function	Purpose	Quick Example
zip()	Pairs multiple iterables element-by-element	list(zip(['a', 'b'], [1, 2])) → [('a', 1), ('b', 2)]
sorted()	Returns a new sorted list (supports key)	sorted(['cat', 'zebra', 'ox'], key=len)
any() / all()	Tests boolean conditions across an iterable	all([True, True, False]) → False
map()	Applies a function to each item	list(map(str.upper, ['a', 'b'])) → ['A', 'B']
filter()	Filters elements where condition evaluates True	list(filter(lambda x: x > 0, [-1, 2])) → [2]
convert it to ipynb

Here is the complete Jupyter Notebook code. You can save this text directly as a .ipynb file (e.g., python_quick_notes.ipynb) and open it in VS Code, JupyterLab, or Google Colab, or run the conversion script below.

Method 1: Save Directly as python_quick_notes.ipynb
Paste the following JSON block into a text file and save it with the .ipynb extension:

JSON
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Python Quick Notes & Reference\n",
    "A concise, structured reference notebook covering core syntax, `print()` parameters, data structures, control flow, functions, file handling, and OOP."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 1. Core Syntax & Primitive Types"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Variables are dynamically typed\n",
    "x = 42              # int\n",
    "pi = 3.14159        # float\n",
    "name = \"Dev\"        # str\n",
    "is_active = True    # bool (Capital T / F)\n",
    "empty_val = None    # NoneType (Python's null)\n",
    "\n",
    "# Explicit type conversion\n",
    "num = int(\"10\")     # converts string to int -> 10\n",
    "flt = float(5)      # converts int to float -> 5.0\n",
    "txt = str(100)      # converts int to string -> '100'\n",
    "\n",
    "# f-strings: dynamic interpolation and decimal precision\n",
    "greeting = f\"User {name} has score: {pi:.2f}\"\n",
    "print(greeting)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 2. `print()` Parameters Mastered\n",
    "Signature: `print(*objects, sep=' ', end='\\n', file=None, flush=False)`"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import sys\n",
    "\n",
    "# *objects: Any number of comma-separated values\n",
    "print(\"A\", 1, True)\n",
    "\n",
    "# sep: Custom separator between objects (default: ' ')\n",
    "print(\"2026\", \"09\", \"07\", sep=\"-\")             # Output: 2026-09-07\n",
    "\n",
    "# end: What prints after the line (default: '\\n' for newline)\n",
    "print(\"Loading\", end=\"...\")                    # Keeps next print on same line\n",
    "print(\"Done\")                                  # Output: Loading...Done\n",
    "\n",
    "# flush: Force immediate terminal update (useful for real-time progress)\n",
    "print(\"Updating...\", end=\"\", flush=True)\n",
    "\n",
    "# file: Direct output to streams (sys.stderr) or files\n",
    "print(\"\\nWarning: Check logs!\", file=sys.stderr)\n",
    "with open(\"log.txt\", \"w\") as f:\n",
    "    print(\"Log Entry #1\", file=f)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 3. Data Structures"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# 1. LIST: Ordered, mutable, allows duplicates\n",
    "nums = [1, 2, 3]\n",
    "nums.append(4)             # [1, 2, 3, 4]\n",
    "popped = nums.pop()        # Removes & returns last item: 4\n",
    "first_two = nums[0:2]      # Slicing: [1, 2]\n",
    "reversed_nums = nums[::-1] # Reverse: [3, 2, 1]\n",
    "\n",
    "# 2. TUPLE: Ordered, immutable (cannot change values)\n",
    "coords = (10, 20)\n",
    "x_pos, y_pos = coords      # Unpacking: x_pos=10, y_pos=20\n",
    "\n",
    "# 3. DICTIONARY: Key-value store, preserves insertion order\n",
    "user = {\"name\": \"Alex\", \"age\": 28}\n",
    "city = user.get(\"city\", \"N/A\")  # Safe fetch: returns 'N/A' if key missing\n",
    "user[\"role\"] = \"Admin\"          # Insert / update\n",
    "for k, v in user.items():       # Iterate key and value simultaneously\n",
    "    print(f\"{k}: {v}\")\n",
    "\n",
    "# 4. SET: Unordered, unique elements only\n",
    "tags = {\"python\", \"ai\", \"web\"}\n",
    "tags.add(\"cloud\")\n",
    "union_set = tags | {\"docker\", \"ai\"}       # Merge unique values\n",
    "common_set = tags & {\"python\", \"c++\"}    # Intersection: {'python'}\n",
    "print(\"Union:\", union_set)\n",
    "print(\"Common:\", common_set)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 4. Control Flow & Loops"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Conditionals\n",
    "score = 85\n",
    "if score >= 90:\n",
    "    grade = \"A\"\n",
    "elif score >= 75:\n",
    "    grade = \"B\"\n",
    "else:\n",
    "    grade = \"C\"\n",
    "\n",
    "# Ternary (single-line if-else)\n",
    "status = \"Pass\" if score >= 50 else \"Fail\"\n",
    "\n",
    "# Iterating with index using enumerate()\n",
    "for idx, item in enumerate([\"alpha\", \"beta\"]):\n",
    "    print(f\"Index {idx}: {item}\")\n",
    "\n",
    "# While loop with break/continue\n",
    "count = 3\n",
    "while count > 0:\n",
    "    count -= 1\n",
    "    if count == 1:\n",
    "        continue  # Skip this iteration\n",
    "    print(f\"Count: {count}\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 5. Comprehensions"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# List comprehension: [expression for item in iterable if condition]\n",
    "evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]\n",
    "\n",
    "# Dict comprehension: {key: value for item in iterable}\n",
    "squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}\n",
    "\n",
    "# Set comprehension: {expression for item in iterable}\n",
    "word_lens = {len(w) for w in [\"apple\", \"pear\", \"banana\"]}\n",
    "\n",
    "print(\"Evens:\", evens)\n",
    "print(\"Squares:\", squares)\n",
    "print(\"Word Lengths:\", word_lens)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 6. Functions, `*args`, & `**kwargs`"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Default arguments & type annotations\n",
    "def calculate_area(width: float, height: float = 1.0) -> float:\n",
    "    return width * height\n",
    "\n",
    "# *args gathers positional args into a tuple; **kwargs gathers named args into a dict\n",
    "def demo_args(*args, **kwargs):\n",
    "    print(\"Positional:\", args)      # (1, 2)\n",
    "    print(\"Keyword:\", kwargs)       # {'mode': 'fast'}\n",
    "\n",
    "demo_args(1, 2, mode=\"fast\")\n",
    "\n",
    "# Lambda (one-line anonymous function)\n",
    "double = lambda x: x * 2\n",
    "print(\"Double of 5:\", double(5))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 7. File I/O & Error Handling"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Context manager 'with' handles automatic file closing\n",
    "with open(\"data.txt\", \"w\", encoding=\"utf-8\") as f:\n",
    "    f.write(\"Line 1\\nLine 2\")\n",
    "\n",
    "with open(\"data.txt\", \"r\", encoding=\"utf-8\") as f:\n",
    "    content = f.read()\n",
    "print(\"File content:\\n\", content)\n",
    "\n",
    "# Exception handling\n",
    "try:\n",
    "    result = 10 / 0\n",
    "except ZeroDivisionError as err:\n",
    "    print(\"Math error caught:\", err)\n",
    "except Exception as err:\n",
    "    print(\"Other error caught:\", err)\n",
    "else:\n",
    "    print(\"Runs only if no error occurred\")\n",
    "finally:\n",
    "    print(\"Always runs (for cleanup)\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 8. Classes & Dataclasses"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Standard OOP\n",
    "class BankAccount:\n",
    "    def __init__(self, owner: str, balance: float = 0.0):\n",
    "        self.owner = owner          # Public attribute\n",
    "        self._balance = balance     # Protected by convention\n",
    "\n",
    "    def deposit(self, amount: float):\n",
    "        self._balance += amount\n",
    "\n",
    "    def __str__(self):\n",
    "        return f\"Account({self.owner}, Balance: {self._balance})\"\n",
    "\n",
    "acc = BankAccount(\"Alice\", 100.0)\n",
    "acc.deposit(50.0)\n",
    "print(acc)\n",
    "\n",
    "# Dataclasses (auto-generates __init__, __repr__, and comparisons)\n",
    "from dataclasses import dataclass\n",
    "\n",
    "@dataclass\n",
    "class Product:\n",
    "    name: str\n",
    "    price: float\n",
    "    in_stock: bool = True\n",
    "\n",
    "item = Product(\"Keyboard\", 49.99)\n",
    "print(item)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## 9. High-Utility Built-ins\n",
    "\n",
    "| Function | Purpose | Quick Example |\n",
    "| :--- | :--- | :--- |\n",
    "| `zip()` | Pairs multiple iterables element-by-element | `list(zip(['a', 'b'], [1, 2]))` $\\rightarrow$ `[('a', 1), ('b', 2)]` |\n",
    "| `sorted()` | Returns a new sorted list (supports `key`) | `sorted(['cat', 'zebra', 'ox'], key=len)` |\n",
    "| `any()` / `all()` | Tests boolean conditions across an iterable | `all([True, True, False])` $\\rightarrow$ `False` |\n",
    "| `map()` | Applies a function to each item | `list(map(str.upper, ['a', 'b']))` $\\rightarrow$ `['A', 'B']` |\n",
    "| `filter()` | Filters elements where condition evaluates `True` | `list(filter(lambda x: x > 0, [-1, 2]))` $\\rightarrow$ `[2]` |"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Demonstrating the built-ins\n",
    "print(\"zip:\", list(zip(['a', 'b'], [1, 2])))\n",
    "print(\"sorted by len:\", sorted(['cat', 'zebra', 'ox'], key=len))\n",
    "print(\"all truthy:\", all([True, 1, 'yes']))\n",
    "print(\"map upper:\", list(map(str.upper, ['a', 'b'])))\n",
    "print(\"filter positive:\", list(filter(lambda x: x > 0, [-1, 2, -3, 4])))"
   ]
  }
 ],
 "metadata": {
  "language_info": {
   "name": "python",
   "version": "3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
Method 2: Generate via Python Script
If you prefer generating the file locally using Python:

Python
import json

notebook_content = {
    # paste the JSON structure above inside this variable
}

with open("python_notes.ipynb", "w", encoding="utf-8") as f:
    json.dump(notebook_content, f, indent=2)
markdown language please

2. print() Parameters Mastered
Signature: print(*objects, sep=' ', end='\\n', file=None, flush=False)

Parameter	Type / Default	Purpose
*objects	Any	Zero or more objects to print (auto-stringified via str()).
sep	str | None (default: ' ')	String placed between multiple printed objects.
end	str | None (default: '\\n')	String printed at the very end (newline by default).
file	file-like (default: sys.stdout)	Output destination (sys.stderr, open writable file, etc.).
flush	bool (default: False)	If True, forces stream buffer to flush immediately.
Python
import sys

# sep: Custom separator
print("2026", "09", "07", sep="-")             # Output: 2026-09-07

# end: Suppress newline, print next call on same line
print("Loading", end="...")
print("Done")                                  # Output: Loading...Done

# flush: Immediate output to screen (progress counters/spinners)
print("Updating...", end="", flush=True)

# file: Direct output to stderr or a file on disk
print("\\nWarning: check logs", file=sys.stderr)

with open("log.txt", "w", encoding="utf-8") as f:
    print("Log entry #1", 200, sep=" -> ", file=f)
3. Data Structures
Python
# 1. LIST: Ordered, mutable, allows duplicate values
nums = [1, 2, 3]
nums.append(4)             # [1, 2, 3, 4]
popped = nums.pop()        # Removes & returns last item: 4
first_two = nums[0:2]      # Slicing: [1, 2]
reversed_nums = nums[::-1] # Step -1 reverses: [3, 2, 1]

# 2. TUPLE: Ordered, immutable (fixed records)
coords = (10, 20)
x_pos, y_pos = coords      # Unpacking: x_pos=10, y_pos=20

# 3. DICTIONARY: Key-value map, preserves insertion order
user = {"name": "Alex", "age": 28}
city = user.get("city", "N/A")  # Safe fetch: returns 'N/A' if key missing
user["role"] = "Admin"          # Insert / update key
for k, v in user.items():       # Iterate key and value simultaneously
    print(f"{k}: {v}")

# 4. SET: Unordered, unique elements only
tags = {"python", "ai", "web"}
tags.add("cloud")
union_set = tags | {"docker", "ai"}       # Union (merge unique items)
common_set = tags & {"python", "c++"}    # Intersection: {'python'}
4. Control Flow & Loops
Python
# Standard conditionals
score = 85
if score >= 90:
    grade = "A"
elif score >= 75:
    grade = "B"
else:
    grade = "C"

# Ternary operator (inline if-else)
status = "Pass" if score >= 50 else "Fail"

# Iterating with index using enumerate()
for idx, item in enumerate(["alpha", "beta"]):
    print(f"Index {idx}: {item}")

# While loop with break/continue
count = 3
while count > 0:
    count -= 1
    if count == 1:
        continue  # Skip rest of this iteration
    print(f"Count: {count}")
5. Comprehensions
Python
# List comprehension: [expression for item in iterable if condition]
evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]

# Dict comprehension: {key: value for item in iterable}
squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}

# Set comprehension: {expression for item in iterable}
word_lens = {len(w) for w in ["apple", "pear", "banana"]}
6. Functions, *args, & **kwargs
Python
# Default arguments & type annotations
def calculate_area(width: float, height: float = 1.0) -> float:
    return width * height

# *args gathers positional args into a tuple; **kwargs gathers named args into a dict
def demo_args(*args, **kwargs):
    print("Positional args:", args)     # (1, 2)
    print("Keyword args:", kwargs)      # {'mode': 'fast'}

demo_args(1, 2, mode="fast")

# Lambda: concise one-line anonymous function
double = lambda x: x * 2
7. File I/O & Exception Handling
Python
# Context manager 'with' guarantees proper file closing
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("Line 1\\nLine 2")

with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

# Exception handling blocks
try:
    result = 10 / 0
except ZeroDivisionError as err:
    print("Math error caught:", err)
except Exception as err:
    print("Other error caught:", err)
else:
    print("Runs only if try block succeeded with no error")
finally:
    print("Always runs (ideal for resource cleanup)")
8. Classes & Dataclasses
Python
# Standard OOP class definition
class BankAccount:
    def __init__(self, owner: str, balance: float = 0.0):
        self.owner = owner          # Public attribute
        self._balance = balance     # Protected attribute convention

    def deposit(self, amount: float):
        self._balance += amount

    def __str__(self):
        return f"Account({self.owner}, Balance: {self._balance})"

acc = BankAccount("Alice", 100.0)
acc.deposit(50.0)
print(acc)

# Dataclasses: auto-generates __init__, __repr__, and comparisons
from dataclasses import dataclass

@dataclass
class Product:
    name: str
    price: float
    in_stock: bool = True

item = Product("Keyboard", 49.99)
print(item)
9. High-Utility Built-ins
Function	Purpose	Example
zip()	Pairs iterables element-by-element	list(zip(['a', 'b'], [1, 2])) → [('a', 1), ('b', 2)]
sorted()	Returns a new sorted list (supports key=)	sorted(['cat', 'zebra', 'ox'], key=len)
any() / all()	Evaluates truthiness across iterable	all([True, 1, 'yes']) → True
map()	Applies a function to every item	list(map(str.upper, ['a', 'b'])) → ['A', 'B']
filter()	Keeps items where condition evaluates True	list(filter(lambda x: x > 0, [-1, 2])) → [2]
"""		
with open("python_quick_notes.md", "w", encoding="utf-8") as f:
f.write(md_content)

print("Markdown file created successfully.")


```text?code_stdout&code_event_index=1
Markdown file created successfully.

Your Markdown file is ready:

MD icon
python_quick_notes
 MD 
Here is the raw Markdown content for quick copying:

Markdown
# Python Quick Reference Notes

A concise, high-yield Python cheat sheet and reference guide designed for fast reading and revision.

---

## 1. Core Syntax & Primitive Types

```python
# Variables are dynamically typed (no explicit type declaration needed)
x = 42              # int
pi = 3.14159        # float
name = "Dev"        # str
is_active = True    # bool (Capital T or F)
empty_val = None    # NoneType (Python's null)

# Explicit type casting / conversion
num = int("10")     # str to int -> 10
flt = float(5)      # int to float -> 5.0
txt = str(100)      # int to str -> '100'

# f-strings: dynamic interpolation and decimal formatting
greeting = f"User {name} has score: {pi:.2f}"  # 'User Dev has score: 3.14'
2. print() Parameters Mastered
Signature: print(*objects, sep=' ', end='\n', file=None, flush=False)

Parameter	Type / Default	Purpose
*objects	Any	Zero or more objects to print (auto-stringified via str()).
sep	`str	None(default:' '`)
end	`str	None(default:'\n'`)
file	file-like (default: sys.stdout)	Output destination (sys.stderr, open writable file, etc.).
flush	bool (default: False)	If True, forces stream buffer to flush immediately.
Python
import sys

# sep: Custom separator
print("2026", "09", "07", sep="-")             # Output: 2026-09-07

# end: Suppress newline, print next call on same line
print("Loading", end="...")
print("Done")                                  # Output: Loading...Done

# flush: Immediate output to screen (progress counters/spinners)
print("Updating...", end="", flush=True)

# file: Direct output to stderr or a file on disk
print("\nWarning: check logs", file=sys.stderr)

with open("log.txt", "w", encoding="utf-8") as f:
    print("Log entry #1", 200, sep=" -> ", file=f)
3. Data Structures
Python
# 1. LIST: Ordered, mutable, allows duplicate values
nums = [1, 2, 3]
nums.append(4)             # [1, 2, 3, 4]
popped = nums.pop()        # Removes & returns last item: 4
first_two = nums[0:2]      # Slicing: [1, 2]
reversed_nums = nums[::-1] # Step -1 reverses: [3, 2, 1]

# 2. TUPLE: Ordered, immutable (fixed records)
coords = (10, 20)
x_pos, y_pos = coords      # Unpacking: x_pos=10, y_pos=20

# 3. DICTIONARY: Key-value map, preserves insertion order
user = {"name": "Alex", "age": 28}
city = user.get("city", "N/A")  # Safe fetch: returns 'N/A' if key missing
user["role"] = "Admin"          # Insert / update key
for k, v in user.items():       # Iterate key and value simultaneously
    print(f"{k}: {v}")

# 4. SET: Unordered, unique elements only
tags = {"python", "ai", "web"}
tags.add("cloud")
union_set = tags | {"docker", "ai"}       # Union (merge unique items)
common_set = tags & {"python", "c++"}    # Intersection: {'python'}
4. Control Flow & Loops
Python
# Standard conditionals
score = 85
if score >= 90:
    grade = "A"
elif score >= 75:
    grade = "B"
else:
    grade = "C"

# Ternary operator (inline if-else)
status = "Pass" if score >= 50 else "Fail"

# Iterating with index using enumerate()
for idx, item in enumerate(["alpha", "beta"]):
    print(f"Index {idx}: {item}")

# While loop with break/continue
count = 3
while count > 0:
    count -= 1
    if count == 1:
        continue  # Skip rest of this iteration
    print(f"Count: {count}")
5. Comprehensions
Python
# List comprehension: [expression for item in iterable if condition]
evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]

# Dict comprehension: {key: value for item in iterable}
squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}

# Set comprehension: {expression for item in iterable}
word_lens = {len(w) for w in ["apple", "pear", "banana"]}
6. Functions, *args, & **kwargs
Python
# Default arguments & type annotations
def calculate_area(width: float, height: float = 1.0) -> float:
    return width * height

# *args gathers positional args into a tuple; **kwargs gathers named args into a dict
def demo_args(*args, **kwargs):
    print("Positional args:", args)     # (1, 2)
    print("Keyword args:", kwargs)      # {'mode': 'fast'}

demo_args(1, 2, mode="fast")

# Lambda: concise one-line anonymous function
double = lambda x: x * 2
7. File I/O & Exception Handling
Python
# Context manager 'with' guarantees proper file closing
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("Line 1\nLine 2")

with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

# Exception handling blocks
try:
    result = 10 / 0
except ZeroDivisionError as err:
    print("Math error caught:", err)
except Exception as err:
    print("Other error caught:", err)
else:
    print("Runs only if try block succeeded with no error")
finally:
    print("Always runs (ideal for resource cleanup)")
8. Classes & Dataclasses
Python
# Standard OOP class definition
class BankAccount:
    def __init__(self, owner: str, balance: float = 0.0):
        self.owner = owner          # Public attribute
        self._balance = balance     # Protected attribute convention

    def deposit(self, amount: float):
        self._balance += amount

    def __str__(self):
        return f"Account({self.owner}, Balance: {self._balance})"

acc = BankAccount("Alice", 100.0)
acc.deposit(50.0)
print(acc)

# Dataclasses: auto-generates __init__, __repr__, and comparisons
from dataclasses import dataclass

@dataclass
class Product:
    name: str
    price: float
    in_stock: bool = True

item = Product("Keyboard", 49.99)
print(item)
9. High-Utility Built-ins
Function	Purpose	Example
zip()	Pairs iterables element-by-element	list(zip(['a', 'b'], [1, 2])) → [('a', 1), ('b', 2)]
sorted()	Returns a new sorted list (supports key=)	sorted(['cat', 'zebra', 'ox'], key=len)
any() / all()	Evaluates truthiness across iterable	all([True, 1, 'yes']) → True
map()	Applies a function to every item	list(map(str.upper, ['a', 'b'])) → ['A', 'B']
filter()	Keeps items where condition evaluates True	list(filter(lambda x: x > 0, [-1, 2])) → [2]
Gemini is AI and can make mistakes.




Analysing
# Python Quick Reference Notes

A concise, high-yield Python cheat sheet and reference guide designed for fast reading and revision.

---

## 1. Core Syntax & Primitive Types

```python
# Variables are dynamically typed (no explicit type declaration needed)
x = 42              # int
pi = 3.14159        # float
name = "Dev"        # str
is_active = True    # bool (Capital T or F)
empty_val = None    # NoneType (Python's null)

# Explicit type casting / conversion
num = int("10")     # str to int -> 10
flt = float(5)      # int to float -> 5.0
txt = str(100)      # int to str -> '100'

# f-strings: dynamic interpolation and decimal formatting
greeting = f"User {name} has score: {pi:.2f}"  # 'User Dev has score: 3.14'
```

---

## 2. `print()` Parameters Mastered

**Signature:** `print(*objects, sep=' ', end='\n', file=None, flush=False)`

| Parameter | Type / Default | Purpose |
| :--- | :--- | :--- |
| `*objects` | `Any` | Zero or more objects to print (auto-stringified via `str()`). |
| `sep` | `str \| None` (default: `' '`) | String placed between multiple printed objects. |
| `end` | `str \| None` (default: `'\n'`) | String printed at the very end (newline by default). |
| `file` | `file-like` (default: `sys.stdout`) | Output destination (`sys.stderr`, open writable file, etc.). |
| `flush` | `bool` (default: `False`) | If `True`, forces stream buffer to flush immediately. |

```python
import sys

# sep: Custom separator
print("2026", "09", "07", sep="-")             # Output: 2026-09-07

# end: Suppress newline, print next call on same line
print("Loading", end="...")
print("Done")                                  # Output: Loading...Done

# flush: Immediate output to screen (progress counters/spinners)
print("Updating...", end="", flush=True)

# file: Direct output to stderr or a file on disk
print("\nWarning: check logs", file=sys.stderr)

with open("log.txt", "w", encoding="utf-8") as f:
    print("Log entry #1", 200, sep=" -> ", file=f)
```

---

## 3. Data Structures

```python
# 1. LIST: Ordered, mutable, allows duplicate values
nums = [1, 2, 3]
nums.append(4)             # [1, 2, 3, 4]
popped = nums.pop()        # Removes & returns last item: 4
first_two = nums[0:2]      # Slicing: [1, 2]
reversed_nums = nums[::-1] # Step -1 reverses: [3, 2, 1]

# 2. TUPLE: Ordered, immutable (fixed records)
coords = (10, 20)
x_pos, y_pos = coords      # Unpacking: x_pos=10, y_pos=20

# 3. DICTIONARY: Key-value map, preserves insertion order
user = {"name": "Alex", "age": 28}
city = user.get("city", "N/A")  # Safe fetch: returns 'N/A' if key missing
user["role"] = "Admin"          # Insert / update key
for k, v in user.items():       # Iterate key and value simultaneously
    print(f"{k}: {v}")

# 4. SET: Unordered, unique elements only
tags = {"python", "ai", "web"}
tags.add("cloud")
union_set = tags | {"docker", "ai"}       # Union (merge unique items)
common_set = tags & {"python", "c++"}    # Intersection: {'python'}
```

---

## 4. Control Flow & Loops

```python
# Standard conditionals
score = 85
if score >= 90:
    grade = "A"
elif score >= 75:
    grade = "B"
else:
    grade = "C"

# Ternary operator (inline if-else)
status = "Pass" if score >= 50 else "Fail"

# Iterating with index using enumerate()
for idx, item in enumerate(["alpha", "beta"]):
    print(f"Index {idx}: {item}")

# While loop with break/continue
count = 3
while count > 0:
    count -= 1
    if count == 1:
        continue  # Skip rest of this iteration
    print(f"Count: {count}")
```

---

## 5. Comprehensions

```python
# List comprehension: [expression for item in iterable if condition]
evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]

# Dict comprehension: {key: value for item in iterable}
squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}

# Set comprehension: {expression for item in iterable}
word_lens = {len(w) for w in ["apple", "pear", "banana"]}
```

---

## 6. Functions, `*args`, & `**kwargs`

```python
# Default arguments & type annotations
def calculate_area(width: float, height: float = 1.0) -> float:
    return width * height

# *args gathers positional args into a tuple; **kwargs gathers named args into a dict
def demo_args(*args, **kwargs):
    print("Positional args:", args)     # (1, 2)
    print("Keyword args:", kwargs)      # {'mode': 'fast'}

demo_args(1, 2, mode="fast")

# Lambda: concise one-line anonymous function
double = lambda x: x * 2
```

---

## 7. File I/O & Exception Handling

```python
# Context manager 'with' guarantees proper file closing
with open("data.txt", "w", encoding="utf-8") as f:
    f.write("Line 1\nLine 2")

with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()

# Exception handling blocks
try:
    result = 10 / 0
except ZeroDivisionError as err:
    print("Math error caught:", err)
except Exception as err:
    print("Other error caught:", err)
else:
    print("Runs only if try block succeeded with no error")
finally:
    print("Always runs (ideal for resource cleanup)")
```

---

## 8. Classes & Dataclasses

```python
# Standard OOP class definition
class BankAccount:
    def __init__(self, owner: str, balance: float = 0.0):
        self.owner = owner          # Public attribute
        self._balance = balance     # Protected attribute convention

    def deposit(self, amount: float):
        self._balance += amount

    def __str__(self):
        return f"Account({self.owner}, Balance: {self._balance})"

acc = BankAccount("Alice", 100.0)
acc.deposit(50.0)
print(acc)

# Dataclasses: auto-generates __init__, __repr__, and comparisons
from dataclasses import dataclass

@dataclass
class Product:
    name: str
    price: float
    in_stock: bool = True

item = Product("Keyboard", 49.99)
print(item)
```

---

## 9. High-Utility Built-ins

| Function | Purpose | Example |
| :--- | :--- | :--- |
| `zip()` | Pairs iterables element-by-element | `list(zip(['a', 'b'], [1, 2]))` $
ightarrow$ `[('a', 1), ('b', 2)]` |
| `sorted()` | Returns a new sorted list (supports `key=`) | `sorted(['cat', 'zebra', 'ox'], key=len)` |
| `any()` / `all()` | Evaluates truthiness across iterable | `all([True, 1, 'yes'])` $
ightarrow$ `True` |
| `map()` | Applies a function to every item | `list(map(str.upper, ['a', 'b']))` $
ightarrow$ `['A', 'B']` |
| `filter()` | Keeps items where condition evaluates `True` | `list(filter(lambda x: x > 0, [-1, 2]))` $
ightarrow$ `[2]` |
