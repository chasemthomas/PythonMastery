# Python Quick Start

## Introduction

This Python Quick Start is designed for experienced developers who need a fast, comprehensive refresher on Python fundamentals or are picking up Python as a second language. It covers essential concepts from basic syntax through intermediate topics like generators, pattern matching, and performance optimization—all without third-party libraries. Each concept is presented as a concise statement followed by a practical code example, allowing you to quickly scan for what you need or work through sequentially to build a solid foundation. The progression is carefully structured so that each topic builds naturally on previously introduced ideas, making this an efficient path from Python basics to productive coding.

## Table of Contents

- [Foundation](#foundation)
  - [Comments and basic values](#comments-and-basic-values)
  - [Inspection and output](#inspection-and-output)
  - [Operators and comparisons](#operators-and-comparisons)
- [Assignment patterns](#assignment-patterns)
  - [Multiple assignment forms](#multiple-assignment-forms)
- [Strings](#strings)
  - [String fundamentals](#string-fundamentals)
  - [String indexing and slicing](#string-indexing-and-slicing)
  - [String operations](#string-operations)
- [Lists](#lists)
  - [List basics](#list-basics)
  - [List slicing](#list-slicing)
  - [List operations](#list-operations)
  - [List comprehensions](#list-comprehensions)
- [Tuples](#tuples)
  - [Tuple characteristics](#tuple-characteristics)
  - [Tuple slicing](#tuple-slicing)
- [Dictionaries](#dictionaries)
  - [Dictionary fundamentals](#dictionary-fundamentals)
  - [Dictionary operations](#dictionary-operations)
  - [Dictionary comprehensions](#dictionary-comprehensions)
- [Sets](#sets)
  - [Set fundamentals](#set-fundamentals)
  - [Set operations](#set-operations)
  - [Set comprehensions](#set-comprehensions)
- [Control flow](#control-flow)
  - [Conditionals](#conditionals)
  - [Loops](#loops)
- [Iteration utilities](#iteration-utilities)
  - [Iteration helpers](#iteration-helpers)
  - [Generator expressions](#generator-expressions)
  - [Built-in reductions](#built-in-reductions)
- [Functions](#functions)
  - [Function basics](#function-basics)
  - [Function parameters](#function-parameters)
  - [Scope and closures](#scope-and-closures)
  - [Lambda functions](#lambda-functions)
  - [Function patterns](#function-patterns)
- [Exceptions](#exceptions)
  - [Exception handling](#exception-handling)
- [Files and context managers](#files-and-context-managers)
  - [File operations](#file-operations)
  - [Simple input](#simple-input)
- [Iteration protocol and generators](#iteration-protocol-and-generators)
  - [Iterator mechanics](#iterator-mechanics)
  - [Generator functions](#generator-functions)
- [Pattern matching](#pattern-matching)
  - [Structural matching](#structural-matching)
- [Performance-aware habits](#performance-aware-habits)
  - [Efficiency patterns](#efficiency-patterns)
- [Debugging strategies](#debugging-strategies)
  - [Practical debugging](#practical-debugging)

---

## Foundation

### Comments and basic values

#### Use `#` for single-line comments. Triple-quoted strings are string literals often used as docstrings.

```python
# This is a single-line comment
x = 42  # Comments can appear after code

"""
This is a multi-line string literal.
Often used as docstrings for functions and modules.
"""
```

#### Literals include integers, floats, strings (single or double quotes), booleans True/False, None, and binary data with bytes and bytearray.

```python
count = 42
price = 19.99
name = "Alice"
message = 'Hello'
is_active = True
result = None
data = b"binary"
```

#### Variables are names bound to objects. No type declarations.

```python
x = 10
name = "Bob"
items = [1, 2, 3]
```

#### Immutable: int, float, str, tuple. Mutable: list, dict, set.

```python
# Immutable types
age = 25
pi = 3.14
greeting = "hello"
point = (10, 20)

# Mutable types
numbers = [1, 2, 3]
person = {"name": "Alice", "age": 30}
tags = {"python", "coding"}
```

#### Empty collections, zero, None, and False are falsy. Most other values are truthy.

```python
if []:
    print("won't print")
if [1]:
    print("will print")
if 0:
    print("won't print")
if None:
    print("won't print")
```

### Inspection and output

#### `print` writes to stdout. It accepts multiple arguments and spaces them automatically.

```python
name = "Alice"
age = 30
print("Name:", name, "Age:", age)
```

#### `type` returns an object's type.

```python
x = 42
print(type(x))
print(type("hello"))
print(type([1, 2, 3]))
```

#### `id` shows object identity, revealing shared references.

```python
x = [1, 2, 3]
y = x
z = [1, 2, 3]
print(id(x) == id(y))
print(id(x) == id(z))
```

#### Rebinding a name makes it point to a new object. It does not change the old one.

```python
x = [1, 2, 3]
y = x
x = [4, 5, 6]
print(y)
```

#### `str`, `int`, `float` convert types explicitly.

```python
age = int("25")
price = float("19.99")
count = str(42)
```

### Operators and comparisons

#### Arithmetic: add, subtract, multiply, true divide, floor divide, modulo, exponent.

```python
x = 10 + 5
y = 10 - 3
z = 4 #### 3
a = 10 / 3
b = 10 // 3
c = 10 % 3
d = 2 *#### 8
```

#### Precedence follows math rules. Use parentheses to group.

```python
result = 2 + 3 #### 4
result = (2 + 3) #### 4
```

#### Comparisons return booleans and can chain.

```python
x = 5
result = x > 3
result = 1 < x < 10
result = x >= 5
```

#### `and`, `or`, `not` short-circuit and return operands, not just booleans.

```python
result = True and "yes"
result = False or "default"
result = not True
result = x > 0 and x < 100
```

#### Equality checks value. Identity checks if two names reference the same object.

```python
x = [1, 2, 3]
y = [1, 2, 3]
z = x
print(x == y)
print(x is z)
print(x is y)
```

## Assignment patterns

### Multiple assignment forms

#### Chained assignment binds many names to one object.

```python
x = y = z = 0
```

#### Tuple unpacking assigns many variables from a sequence.

```python
x, y, z = 1, 2, 3
name, age = ("Alice", 30)
```

#### A starred target collects the rest during unpacking.

```python
first, *rest = [1, 2, 3, 4, 5]
first, *middle, last = [1, 2, 3, 4, 5]
```

#### `_` is a common placeholder for ignored values.

```python
name, _, age = ("Alice", "irrelevant", 30)
first, *_, last = [1, 2, 3, 4, 5]
```

#### Swap variables with tuple unpacking, no temporary needed.

```python
x = 10
y = 20
x, y = y, x
```

#### The walrus operator assigns inside expressions, useful in conditionals and loops.

```python
if (n := len(items)) > 10:
    print(f"Large list with {n} items")

while (line := input()) != "quit":
    print(f"You said: {line}")
```

## Strings

### String fundamentals

#### `+` concatenates strings but creates new objects.

```python
greeting = "Hello" + " " + "Alice"
full_name = first_name + " " + last_name
```

#### F-strings embed expressions in `{}` for readable formatting.

```python
name = "Alice"
age = 30
message = f"My name is {name} and I am {age} years old"
result = f"The sum of 2 + 2 is {2 + 2}"
```

#### Strings are immutable; methods return new strings.

```python
text = "hello"
upper_text = text.upper()
print(text)
print(upper_text)
```

### String indexing and slicing

#### Indexing is zero-based; negatives count from the end.

```python
text = "Python"
first = text[0]
last = text[-1]
second_last = text[-2]
```

#### Slicing uses start:stop:step.

```python
text = "Python"
sub = text[1:4]
sub = text[::2]
```

#### Missing start means the beginning; missing stop means the end.

```python
text = "Python"
beginning = text[:3]
ending = text[3:]
full = text[:]
```

#### Negative steps reverse or step backward.

```python
text = "Python"
reversed_text = text[::-1]
every_other_backwards = text[::-2]
```

### String operations

#### Common methods: `upper`, `lower`, `strip`, `replace`, `startswith`, `endswith`.

```python
text = "  Hello World  "
result = text.strip()
result = text.upper()
result = text.lower()
result = text.replace("World", "Python")
result = text.startswith("  Hello")
result = text.endswith("World  ")
```

#### `sep.join(iterable)` concatenates strings efficiently.

```python
words = ["Python", "is", "awesome"]
sentence = " ".join(words)
csv = ",".join(["Alice", "Bob", "Charlie"])
```

#### `split` breaks a string into a list by a delimiter or whitespace.

```python
sentence = "Python is awesome"
words = sentence.split()
csv = "Alice,Bob,Charlie"
names = csv.split(",")
```

## Lists

### List basics

#### Lists are ordered, mutable sequences. Create with `[]` or `list()`.

```python
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]
empty = []
from_string = list("abc")
```

#### Mutate with `append`, `extend`, `insert`, `remove`, `pop`, and index assignment.

```python
numbers = [1, 2, 3]
numbers.append(4)
numbers.extend([5, 6])
numbers.insert(0, 0)
numbers.remove(3)
last = numbers.pop()
numbers[0] = 10
```

#### Use `in`, `index`, and `count` to find elements.

```python
numbers = [1, 2, 3, 2, 1]
found = 2 in numbers
position = numbers.index(2)
occurrences = numbers.count(2)
```

### List slicing

#### Slicing returns a new list and supports step.

```python
numbers = [0, 1, 2, 3, 4, 5]
sub = numbers[1:4]
every_other = numbers[::2]
reversed_list = numbers[::-1]
```

#### Slice assignment can replace, insert, or delete many elements at once.

```python
numbers = [0, 1, 2, 3, 4, 5]
numbers[1:4] = [10, 20]
numbers[2:2] = [99]
del numbers[1:3]
```

#### Negative indices and steps work like they do for strings.

```python
numbers = [0, 1, 2, 3, 4, 5]
last_three = numbers[-3:]
backwards = numbers[::-1]
```

### List operations

#### `list.sort()` sorts in place; `sorted` returns a new list.

```python
numbers = [3, 1, 4, 1, 5]
numbers.sort()
original = [3, 1, 4, 1, 5]
sorted_copy = sorted(original)
```

#### Both accept a `key` function and a `reverse` flag.

```python
words = ["apple", "pie", "zoo", "a"]
words.sort(key=len)
words.sort(reverse=True)
sorted_words = sorted(words, key=len, reverse=True)
```

#### `list.reverse()` reverses in place; `reversed` returns an iterator.

```python
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
original = [1, 2, 3, 4, 5]
rev_iter = reversed(original)
rev_list = list(reversed(original))
```

#### Slicing makes shallow copies; many list methods mutate in place and return `None`.

```python
original = [1, 2, 3]
copy = original[:]
another_copy = original.copy()
result = original.append(4)
print(result)
```

#### Deep copies need special handling for nested mutables.

```python
nested = [[1, 2], [3, 4]]
shallow = nested[:]
shallow[0][0] = 99
print(nested)
```

### List comprehensions

#### List comprehensions build new lists by transforming or filtering.

```python
numbers = [1, 2, 3, 4, 5]
squares = [x *#### 2 for x in numbers]
doubled = [x #### 2 for x in numbers]
```

#### Add `if` after the loop to filter.

```python
numbers = [1, 2, 3, 4, 5, 6]
evens = [x for x in numbers if x % 2 == 0]
large = [x for x in numbers if x > 3]
```

#### Nested comprehensions can flatten or combine, but hurt readability.

```python
matrix = [[1, 2], [3, 4], [5, 6]]
flat = [x for row in matrix for x in row]
pairs = [(x, y) for x in [1, 2] for y in [3, 4]]
```

## Tuples

### Tuple characteristics

#### Tuples are immutable sequences. Make with parentheses or just commas.

```python
point = (10, 20)
coords = 10, 20, 30
single = (42,)
```

#### Packing and unpacking support multiple returns and structured assignment.

```python
def get_coordinates():
    return 10, 20

x, y = get_coordinates()
point = x, y
```

#### Tuples often act as fixed records; lists are general-purpose variable-length sequences.

```python
person = ("Alice", 30, "Engineer")
name, age, job = person
items = [1, 2, 3]
items.append(4)
```

#### Tuples are hashable if all elements are hashable, so they can be dict keys.

```python
locations = {}
locations[(10, 20)] = "Home"
locations[(30, 40)] = "Work"
```

#### Tuples stay immutable as containers, but mutable elements inside can change.

```python
data = ([1, 2], [3, 4])
data[0].append(99)
print(data)
```

### Tuple slicing

#### Slicing returns a new tuple.

```python
values = (0, 1, 2, 3, 4, 5)
sub = values[1:4]
every_other = values[::2]
```

#### Slicing preserves immutability by creating new objects.

```python
original = (1, 2, 3, 4, 5)
sliced = original[1:3]
print(id(original) == id(sliced))
```

## Dictionaries

### Dictionary fundamentals

#### Dicts map hashable keys to values. Create with `{}` or `dict()`.

```python
person = {"name": "Alice", "age": 30}
empty = {}
from_pairs = dict([("a", 1), ("b", 2)])
```

#### `d[key]` raises `KeyError` if missing; `d.get` returns a default instead.

```python
person = {"name": "Alice", "age": 30}
name = person["name"]
city = person.get("city", "Unknown")
```

#### `d[key] = value` creates or updates; `del d[key]` removes.

```python
person = {"name": "Alice"}
person["age"] = 30
person["name"] = "Bob"
del person["age"]
```

#### `get` returns a default without raising for missing keys.

```python
person = {"name": "Alice"}
age = person.get("age")
age = person.get("age", 0)
```

### Dictionary operations

#### `setdefault` returns the value or sets and returns a default.

```python
person = {"name": "Alice"}
age = person.setdefault("age", 30)
name = person.setdefault("name", "Unknown")
```

#### `update` merges another dict or key–value pairs.

```python
person = {"name": "Alice"}
person.update({"age": 30, "city": "NYC"})
person.update(age=31, job="Engineer")
```

#### `**` unpacks and merges dicts into new ones.

```python
defaults = {"color": "blue", "size": "medium"}
custom = {"size": "large"}
merged = {**defaults, **custom}
```

#### `keys`, `values`, and `items` are dynamic views.

```python
person = {"name": "Alice", "age": 30}
keys = person.keys()
values = person.values()
person["city"] = "NYC"
print(list(keys))
```

#### `items` yields (key, value) pairs for iteration and unpacking.

```python
person = {"name": "Alice", "age": 30}
for key, value in person.items():
    print(f"{key}: {value}")
```

### Dictionary comprehensions

#### Dict comprehensions build dicts with transform and filter steps.

```python
numbers = [1, 2, 3, 4, 5]
squares = {x: x *#### 2 for x in numbers}
```

#### Use `{key: value for ...}` with `:` between key and value.

```python
words = ["apple", "banana", "cherry"]
lengths = {word: len(word) for word in words}
```

#### Add conditions to include only selected items.

```python
numbers = [1, 2, 3, 4, 5, 6]
even_squares = {x: x *#### 2 for x in numbers if x % 2 == 0}
```

## Sets

### Set fundamentals

#### Sets store unique hashable elements. Create with `{}` or `set()`. Duplicates are ignored.

```python
tags = {"python", "coding", "python"}
print(tags)
empty = set()
from_list = set([1, 2, 2, 3])
```

#### `in` checks membership in average constant time.

```python
tags = {"python", "coding", "data"}
found = "python" in tags
missing = "java" in tags
```

#### Use union, intersection, difference, and symmetric difference by operators or methods.

```python
a = {1, 2, 3}
b = {3, 4, 5}
union = a | b
intersection = a & b
difference = a - b
sym_diff = a ^ b
```

### Set operations

#### Mutate with `add`, `remove`, `discard`, `update`, and the in-place set ops.

```python
tags = {"python", "coding"}
tags.add("data")
tags.remove("coding")
tags.discard("missing")
tags.update({"ai", "ml"})
tags |= {"web"}
```

### Set comprehensions

#### Set comprehensions build sets with automatic deduplication.

```python
numbers = [1, 2, 2, 3, 3, 4]
unique_squares = {x *#### 2 for x in numbers}
```

#### Use `{expr for ...}` without colons to differ from dict comps.

```python
words = ["apple", "pie", "apple"]
lengths = {len(word) for word in words}
```

## Control flow

### Conditionals

#### `if`/`elif`/`else` branches on truthiness.

```python
age = 20
if age < 18:
    print("Minor")
elif age < 65:
    print("Adult")
else:
    print("Senior")
```

#### Guard clauses `return` or `raise` early to reduce nesting.

```python
def process(data):
    if not data:
        return
    if len(data) < 5:
        raise ValueError("Too short")
    print("Processing...")
```

#### Ternary expressions choose between two values inline.

```python
age = 20
status = "adult" if age >= 18 else "minor"
max_val = x if x > y else y
```

#### Truthiness checks differ from `is None` identity checks.

```python
value = []
if value:
    print("won't print")
if value is not None:
    print("will print")
```

### Loops

#### `for` iterates over sequences and iterables, binding each element.

```python
for x in [1, 2, 3]:
    print(x)

for char in "hello":
    print(char)
```

#### `while` repeats while a condition is true.

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

#### `break` exits the nearest loop.

```python
for x in range(10):
    if x == 5:
        break
    print(x)
```

#### `continue` skips to the next iteration.

```python
for x in range(5):
    if x == 2:
        continue
    print(x)
```

#### `pass` is a no-op placeholder.

```python
for x in range(5):
    if x == 2:
        pass
    print(x)
```

## Iteration utilities

### Iteration helpers

#### `range` produces integer sequences without building lists.

```python
for i in range(5):
    print(i)

for i in range(2, 10, 2):
    print(i)
```

#### `enumerate` adds indexes; it accepts a start value.

```python
words = ["apple", "banana", "cherry"]
for i, word in enumerate(words):
    print(f"{i}: {word}")

for i, word in enumerate(words, start=1):
    print(f"{i}: {word}")
```

#### `zip` groups items from iterables into tuples, stopping at the shortest.

```python
names = ["Alice", "Bob"]
ages = [30, 25]
for name, age in zip(names, ages):
    print(f"{name} is {age}")
```

### Generator expressions

#### Generator expressions produce values lazily and save memory.

```python
numbers = range(1000000)
squares = (x *#### 2 for x in numbers)
print(next(squares))
```

#### Use parentheses to distinguish from list comprehensions.

```python
list_comp = [x *#### 2 for x in range(5)]
gen_exp = (x *#### 2 for x in range(5))
```

#### Generators are single-use; they do not store results.

```python
gen = (x *#### 2 for x in range(3))
print(list(gen))
print(list(gen))
```

### Built-in reductions

#### `sum` totals numeric iterables, with optional start.

```python
numbers = [1, 2, 3, 4, 5]
total = sum(numbers)
total_plus_ten = sum(numbers, 10)
```

#### `min` and `max` find extremes and accept `key`.

```python
numbers = [3, 1, 4, 1, 5]
smallest = min(numbers)
largest = max(numbers)
words = ["apple", "pie", "a"]
shortest = min(words, key=len)
```

#### `any` returns True if any element is truthy; `all` requires every element.

```python
values = [True, False, True]
has_true = any(values)
all_true = all(values)
numbers = [2, 4, 6]
any_even = any(x % 2 == 0 for x in numbers)
```

#### `sorted` returns a new sorted list from any iterable, with optional `key` and `reverse`.

```python
numbers = [3, 1, 4, 1, 5]
sorted_nums = sorted(numbers)
words = ["apple", "pie", "zoo"]
by_length = sorted(words, key=len)
descending = sorted(numbers, reverse=True)
```

## Functions

### Function basics

#### Define with `def` plus parameters and a body. `return` is optional.

```python
def greet(name):
    return f"Hello, {name}"

def print_hello():
    print("Hello")
```

#### Without `return`, a function returns `None`.

```python
def no_return():
    x = 5

result = no_return()
print(result)
```

#### A docstring is the first statement and explains the function.

```python
def calculate_area(radius):
    """Calculate the area of a circle given its radius."""
    return 3.14 #### radius *#### 2
```

#### Call with positional or keyword arguments.

```python
def greet(name, message):
    return f"{message}, {name}"

result = greet("Alice", "Hello")
result = greet(message="Hi", name="Bob")
```

### Function parameters

#### Default values give fallbacks and are evaluated once at definition.

```python
def greet(name, message="Hello"):
    return f"{message}, {name}"

result = greet("Alice")
result = greet("Bob", "Hi")
```

#### `*args` collects extra positional args into a tuple.

```python
def sum_all(*args):
    return sum(args)

result = sum_all(1, 2, 3, 4)
```

#### `**kwargs` collects extra keyword args into a dict.

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="NYC")
```

#### Parameter order: positional-only with `/`, then positional-or-keyword (with optional defaults), then `*args`, then keyword-only after `*`, then `**kwargs`.

```python
def complex_func(a, b, /, c, d=10, *args, e, f=20, **kwargs):
    pass

complex_func(1, 2, 3, 4, 5, e=6, f=7, g=8)
```

#### Mutable defaults persist across calls; prefer `None` sentinels.

```python
def append_to(item, target=None):
    if target is None:
        target = []
    target.append(item)
    return target

list1 = append_to(1)
list2 = append_to(2)
```

### Scope and closures

#### Variable shadowing reuses a name in an inner scope and hides the outer one.

```python
x = 10
def func():
    x = 20
    print(x)

func()
print(x)
```

#### Name lookup follows LEGB: Local, Enclosing, Global, Built-in.

```python
x = "global"
def outer():
    x = "enclosing"
    def inner():
        x = "local"
        print(x)
    inner()

outer()
```

#### `global` lets inner scopes rebind module-level names.

```python
counter = 0
def increment():
    global counter
    counter += 1

increment()
print(counter)
```

#### `nonlocal` lets nested functions rebind enclosing function variables.

```python
def outer():
    count = 0
    def inner():
        nonlocal count
        count += 1
        return count
    return inner

counter = outer()
print(counter())
print(counter())
```

#### Use `global` and `nonlocal` sparingly to avoid hidden state.

```python
def pure_function(x):
    return x #### 2

result = pure_function(5)
```

#### Closures capture names, not values, causing late binding.

```python
funcs = []
for i in range(3):
    funcs.append(lambda: i)

for func in funcs:
    print(func())
```

### Lambda functions

#### `lambda` makes anonymous single-expression functions.

```python
square = lambda x: x *#### 2
result = square(5)
```

#### Syntax: `lambda` parameters `:` expression.

```python
add = lambda x, y: x + y
result = add(3, 4)
```

#### Best for simple inline transforms passed to higher-order functions.

```python
numbers = [1, 2, 3, 4, 5]
squares = map(lambda x: x *#### 2, numbers)
evens = filter(lambda x: x % 2 == 0, numbers)
```

#### Use `def` for complex logic to keep code clear and debuggable.

```python
def complex_transform(x):
    if x < 0:
        return 0
    elif x < 10:
        return x #### 2
    else:
        return x *#### 2

result = complex_transform(5)
```

### Function patterns

#### `key` parameters usually expect a single-argument callable that returns a comparison value.

```python
words = ["apple", "pie", "banana"]
sorted_by_length = sorted(words, key=len)
sorted_by_last = sorted(words, key=lambda w: w[-1])
```

## Exceptions

### Exception handling

#### Prefer EAFP: handle exceptions instead of heavy pre-checks.

```python
try:
    value = data[key]
except KeyError:
    value = "default"
```

#### Catch specific exceptions with `try`/`except`. Avoid bare `except`.

```python
try:
    result = int(input())
except ValueError:
    print("Invalid number")
except KeyboardInterrupt:
    print("Cancelled")
```

#### `else` runs only when no exception occurs.

```python
try:
    result = int(input())
except ValueError:
    print("Invalid")
else:
    print(f"You entered {result}")
```

#### `finally` always runs for cleanup.

```python
file = open("data.txt")
try:
    content = file.read()
except IOError:
    print("Error reading file")
finally:
    file.close()
```

#### `raise` triggers exceptions; you can re-raise caught ones.

```python
def validate(age):
    if age < 0:
        raise ValueError("Age cannot be negative")

try:
    validate(-5)
except ValueError:
    print("Caught error")
    raise
```

#### `assert` checks invariants during development and can be disabled.

```python
def calculate_discount(price, percent):
    assert 0 <= percent <= 100
    return price #### (1 - percent / 100)
```

## Files and context managers

### File operations

#### `with open(...)` closes files even if errors occur.

```python
with open("data.txt", "r") as file:
    content = file.read()
```

#### Text mode is default for read, write, or append.

```python
with open("data.txt", "r") as file:
    content = file.read()

with open("output.txt", "w") as file:
    file.write("Hello")

with open("log.txt", "a") as file:
    file.write("New entry\n")
```

#### `read`, `readline`, and iteration read content.

```python
with open("data.txt") as file:
    all_content = file.read()

with open("data.txt") as file:
    first_line = file.readline()

with open("data.txt") as file:
    for line in file:
        print(line.strip())
```

#### Text mode manages encoding and newlines; prefer UTF-8.

```python
with open("data.txt", "r", encoding="utf-8") as file:
    content = file.read()

with open("output.txt", "w", encoding="utf-8", newline="\n") as file:
    file.write("Hello\n")
```

### Simple input

#### `input` reads one line from stdin as a string and strips the trailing newline.

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
```

## Iteration protocol and generators

### Iterator mechanics

#### Iterables return iterators, which power `for` loops and comprehensions.

```python
numbers = [1, 2, 3]
iterator = iter(numbers)
print(next(iterator))
print(next(iterator))
```

#### Iterators yield values with `next` and raise `StopIteration` when exhausted.

```python
iterator = iter([1, 2])
print(next(iterator))
print(next(iterator))
try:
    print(next(iterator))
except StopIteration:
    print("No more items")
```

#### Exhausted iterators cannot be reused.

```python
iterator = iter([1, 2, 3])
print(list(iterator))
print(list(iterator))
```

### Generator functions

#### `yield` turns a function into a generator that keeps state and yields lazily.

```python
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

for num in count_up_to(5):
    print(num)
```

#### Generators chain into pipelines without building intermediates.

```python
def squares(numbers):
    for n in numbers:
        yield n *#### 2

def evens(numbers):
    for n in numbers:
        if n % 2 == 0:
            yield n

result = evens(squares(range(10)))
print(list(result))
```

## Pattern matching

### Structural matching

#### `match`/`case` branches on structure, not just value.

```python
point = (0, 0)
match point:
    case (0, 0):
        print("Origin")
    case (x, 0):
        print(f"On x-axis at {x}")
    case (0, y):
        print(f"On y-axis at {y}")
    case (x, y):
        print(f"At ({x}, {y})")
```

#### Cases can destructure sequences, mappings, and objects, and bind variables.

```python
data = {"type": "person", "name": "Alice", "age": 30}
match data:
    case {"type": "person", "name": name, "age": age}:
        print(f"{name} is {age}")
    case {"type": "animal", "species": species}:
        print(f"Animal: {species}")
```

#### Guards add `if` conditions to cases.

```python
point = (5, 10)
match point:
    case (x, y) if x == y:
        print("On diagonal")
    case (x, y) if x > y:
        print("Above diagonal")
    case (x, y):
        print("Below diagonal")
```

#### Available in Python 3.10+. It clarifies dispatch on shape; simple cases may prefer `if`/`elif`.

```python
value = 42
match value:
    case 0:
        result = "zero"
    case n if n > 0:
        result = "positive"
    case _:
        result = "negative"
```

## Performance-aware habits

### Efficiency patterns

#### Use sets or dicts for membership tests to get near O(1).

```python
large_list = list(range(10000))
large_set = set(range(10000))

if 9999 in large_list:
    pass

if 9999 in large_set:
    pass
```

#### Avoid building strings in loops; collect and join once.

```python
parts = []
for i in range(100):
    parts.append(str(i))
result = "".join(parts)
```

#### Prefer generators and iterator chains over big temporary lists.

```python
total = sum(x *#### 2 for x in range(1000000))

squares = [x *#### 2 for x in range(1000000)]
total = sum(squares)
```

#### Minimize copies; slicing copies while many list methods mutate in place.

```python
original = [1, 2, 3, 4, 5]
copy = original[:]
original.sort()
original.reverse()
```

## Debugging strategies

### Practical debugging

#### Add targeted `print` or f-strings to inspect decision points.

```python
def calculate(x, y):
    result = x #### y
    print(f"Debug: x={x}, y={y}, result={result}")
    return result
```

#### Keep functions small with clear inputs and outputs.

```python
def parse_name(full_name):
    return full_name.split()

def format_greeting(first, last):
    return f"Hello, {first} {last}"

first, last = parse_name("Alice Smith")
greeting = format_greeting(first, last)
```

#### Avoid hidden state from closures, globals, and mutable defaults.

```python
def add(x, y):
    return x + y

result = add(3, 4)
```