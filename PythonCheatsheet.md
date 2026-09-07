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

## 2. Escape Sequences, Backslash & Line Continuation

| Syntax | Use | Example |
| :--- | :--- | :--- |
| `\` | Continue statement on the next line | `total = 10 + 20 + \`<br>`30 + 40` |
| `\n` | New line | `"Hello\nWorld"` |
| `\t` | Tab space | `"Name:\tJai"` |
| `\\` | Literal backslash | `"C:\\Users\\Jai"` |
| `\"` | Double quote inside double-quoted string | `"He said \"Hi\""` |
| `\'` | Single quote inside single-quoted string | `'It\'s good'` |
| `r"..."` | Raw string (treats backslashes literally) | `r"C:\Users\Jai"` |

> **Best Practice:** Prefer parentheses `()`, brackets `[]`, or braces `{}` for multi-line expressions instead of `\`:

```python
# Clean multi-line statement via grouping parentheses
total = (
    10 + 20 +
    30 + 40
)
```

---

## 3. `print()` Parameters Mastered

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

## 4. Data Structures

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

## 5. Control Flow & Loop Controls

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
```

### Loop Jump Statements

| Keyword | Use | Behavior |
| :--- | :--- | :--- |
| `continue` | Skip iteration | Skips remainder of current cycle and jumps to next |
| `break` | Exit loop | Terminates loop immediately |
| `pass` | Placeholder | Does nothing (keeps syntax valid) |

```python
for i in range(5):
    if i == 2:
        continue   # Skips 2, proceeds directly to 3
    if i == 4:
        break      # Stops the entire loop
    print(i)       # Prints 0, 1, 3
```

* **`\`** $\rightarrow$ Line continuation or string escape
* **`continue`** $\rightarrow$ Skip current iteration
* **`break`** $\rightarrow$ Stop loop completely
* **`pass`** $\rightarrow$ No-op placeholder

---

## 6. Comprehensions

```python
# List comprehension: [expression for item in iterable if condition]
evens = [x for x in range(10) if x % 2 == 0]     # [0, 2, 4, 6, 8]

# Dict comprehension: {key: value for item in iterable}
squares = {x: x**2 for x in range(4)}            # {0: 0, 1: 1, 2: 4, 3: 9}

# Set comprehension: {expression for item in iterable}
word_lens = {len(w) for w in ["apple", "pear", "banana"]}
```

---

## 7. Functions, `*args`, & `**kwargs`

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

## 8. File I/O & Exception Handling

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

## 9. Classes & Dataclasses

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

## 10. High-Utility Built-ins

| Function | Purpose | Example |
| :--- | :--- | :--- |
| `zip()` | Pairs iterables element-by-element | `list(zip(['a', 'b'], [1, 2]))` $\rightarrow$ `[('a', 1), ('b', 2)]` |
| `sorted()` | Returns a new sorted list (supports `key=`) | `sorted(['cat', 'zebra', 'ox'], key=len)` |
| `any()` / `all()` | Evaluates truthiness across iterable | `all([True, 1, 'yes'])` $\rightarrow$ `True` |
| `map()` | Applies a function to every item | `list(map(str.upper, ['a', 'b']))` $\rightarrow$ `['A', 'B']` |
| `filter()` | Keeps items where condition evaluates `True` | `list(filter(lambda x: x > 0, [-1, 2]))` $\rightarrow$ `[2]` |
