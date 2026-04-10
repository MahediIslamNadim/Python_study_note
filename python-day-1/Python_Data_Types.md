# Python Data Types — Full Notes

## 1) Data type কী?

**Data type** হলো কোনো value কেমন ধরনের data ধরে রাখে, আর তার ওপর কী কী operation করা যাবে।

উদাহরণ:

```python
x = 10        # int
y = 3.14      # float
name = "Nadim" # str
```

type check:

```python
print(type(x))     # <class 'int'>
print(type(name))  # <class 'str'>
```

---

## 2) Python-এর main built-in data type categories

Python-এর built-in types broadly এভাবে ভাগ করা যায়:

* **Numeric types**
* **Sequence types**
* **Mapping type**
* **Set types**
* **Binary types**
* **Boolean**
* **NoneType**
  এগুলোর বাইরেও classes, instances, exceptions ইত্যাদি type hierarchy-এর অংশ।

---

# 3) Numeric Types

## 3.1 `int`

পূর্ণ সংখ্যা।

```python
a = 10
b = -25
c = 0
```

common operations:

```python
print(a + 5)   # 15
print(a * 2)   # 20
print(a // 3)  # floor division
print(a % 3)   # remainder
```

---

## 3.2 `float`

দশমিক সংখ্যা।

```python
x = 3.14
y = -0.5
```

```python
print(x + 2.0)
print(x / 2)
```

---

## 3.3 `complex`

বাস্তব + imaginary অংশ।

```python
z = 2 + 3j
print(z.real)  # 2.0
print(z.imag)  # 3.0
```

Python-এর standard numeric types হলো `int`, `float`, এবং `complex`; আর `bool` হচ্ছে `int`-এর একটি subtype। ([Python documentation][1])

---

# 4) Boolean Type

## 4.1 `bool`

শুধু দুইটা value:

* `True`
* `False`

```python
is_ok = True
is_fail = False
```

```python
print(10 > 5)   # True
print(10 == 5)  # False
```

`bool` truth-value testing-এর জন্য ব্যবহৃত হয়, আর Python-এ false হিসেবে ধরা হয় যেমন `False`, `None`, numeric zero, এবং empty collections/strings। ([Python documentation][1])

---

# 5) Sequence Types

Sequence মানে ordered collection।

## 5.1 `str`

Text data রাখে। Python `str` Unicode text ধরে। ([Python documentation][2])

```python
name = "Python"
```

### common operations

```python
print(name[0])      # P
print(name[-1])     # n
print(name[0:3])    # Pyt
print(len(name))    # 6
print(name.lower()) # python
print(name.upper()) # PYTHON
```

### immutable

```python
s = "hello"
# s[0] = "H"   # Error
```

---

## 5.2 `list`

Ordered, mutable collection.

```python
nums = [1, 2, 3, 4]
mixed = [1, "hello", 3.5, True]
```

### common operations

```python
nums.append(5)
nums.insert(1, 100)
nums.remove(3)
print(nums)
```

### indexing / slicing

```python
print(nums[0])
print(nums[1:3])
```

---

## 5.3 `tuple`

Ordered, immutable collection.

```python
point = (10, 20)
single = (5,)   # single-element tuple
```

```python
print(point[0])   # 10
```

### immutable

```python
t = (1, 2, 3)
# t[0] = 10   # Error
```

---

## 5.4 `range`

Number sequence generate করতে ব্যবহৃত হয়।

```python
r = range(5)
print(list(r))   # [0, 1, 2, 3, 4]
```

```python
print(list(range(2, 10, 2)))  # [2, 4, 6, 8]
```

`str`, `list`, `tuple`, আর `range` sequence family-এর গুরুত্বপূর্ণ built-in types। ([Python documentation][1])

---

# 6) Mapping Type

## 6.1 `dict`

Key-value pair store করে।

```python
student = {
    "name": "Nadim",
    "age": 18,
    "city": "Sylhet"
}
```

### access

```python
print(student["name"])      # Nadim
print(student.get("age"))   # 18
```

### add / update

```python
student["age"] = 19
student["skill"] = "Python"
```

### delete

```python
del student["city"]
```

### iterate

```python
for key, value in student.items():
    print(key, value)
```

Dictionary হলো mapping type; keys সাধারণত immutable হতে হয়, যেমন `str`, `int`, `tuple` ইত্যাদি। ([Python documentation][3])

---

# 7) Set Types

## 7.1 `set`

Unordered, mutable, unique elements.

```python
s = {1, 2, 3, 3, 4}
print(s)   # duplicates removed
```

### common operations

```python
s.add(10)
s.remove(2)
```

### set math

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)  # union
print(a & b)  # intersection
print(a - b)  # difference
```

---

## 7.2 `frozenset`

Immutable set।

```python
fs = frozenset([1, 2, 3])
```

```python
# fs.add(4)   # Error
```

`set` এবং `frozenset` built-in set types। ([Python documentation][1])

---

# 8) Binary Types

Python binary data রাখার জন্য `bytes`, `bytearray`, আর `memoryview` দেয়। `bytes` immutable, `bytearray` mutable। ([Python documentation][2])

## 8.1 `bytes`

Immutable binary data.

```python
b = b"hello"
print(b[0])   # ASCII value
```

---

## 8.2 `bytearray`

Mutable binary data.

```python
ba = bytearray(b"hello")
ba[0] = 72
print(ba)
```

---

## 8.3 `memoryview`

Binary objects-এর data copy না করে access করতে দেয়।

```python
data = bytes([1, 2, 3, 4])
mv = memoryview(data)
print(mv[0])   # 1
```

---

# 9) Special Type

## 9.1 `NoneType`

এর একটাই value: `None`।

```python
x = None
print(x)
```

অনেক function explicit return না দিলে `None` return করে। `None`-এর truth value false। ([Python documentation][4])

---

# 10) Mutable vs Immutable

## Immutable types

Value change করা যায় না:

* `int`
* `float`
* `complex`
* `bool`
* `str`
* `tuple`
* `range`
* `bytes`
* `frozenset`
* `NoneType`

## Mutable types

Value change করা যায়:

* `list`
* `dict`
* `set`
* `bytearray`

example:

```python
x = [1, 2, 3]
x[0] = 100
print(x)   # [100, 2, 3]
```

```python
s = "hello"
# s[0] = "H"   # Error
```

Python docs অনুযায়ী mutable collections-এর যেসব methods in-place modify করে, সেগুলো সাধারণত object নিজে return না করে `None` return করে। ([Python documentation][1])

---

# 11) Type Conversion

## implicit conversion

```python
x = 5
y = 2.5
print(x + y)   # 7.5
```

## explicit conversion

```python
print(int("10"))       # 10
print(float("3.14"))   # 3.14
print(str(100))        # "100"
print(list((1, 2, 3))) # [1, 2, 3]
print(tuple([1, 2]))   # (1, 2)
print(set([1, 1, 2]))  # {1, 2}
```

---

# 12) Truth Value Testing

Python-এ কোন value true/false হিসেবে কেমন behave করে:

## False হিসেবে ধরা হয়

```python
False
None
0
0.0
0j
""
[]
()
{}
set()
range(0)
```

## True হিসেবে ধরা হয়

উপরের বাইরে বেশিরভাগ non-empty / non-zero value।

```python
if "hello":
    print("True")
```

Truth-value testing প্রায় সব object-এর জন্য support করা হয়। ([Python documentation][1])

---

# 13) `type()` এবং `isinstance()`

## `type()`

exact type দেখায়।

```python
x = 10
print(type(x))   # <class 'int'>
```

## `isinstance()`

inheritance/subtype-friendly check।

```python
print(isinstance(10, int))    # True
print(isinstance(True, bool)) # True
print(isinstance(True, int))  # True
```

---

# 14) Practical beginner notes

## `list` কবে ব্যবহার করবে?

যখন data change হবে:

```python
tasks = ["study", "practice"]
tasks.append("revision")
```

## `tuple` কবে ব্যবহার করবে?

যখন fixed data:

```python
location = (24.9, 91.8)
```

## `dict` কবে ব্যবহার করবে?

যখন label সহ data:

```python
user = {"name": "Nadim", "age": 18}
```

## `set` কবে ব্যবহার করবে?

যখন unique values দরকার:

```python
tags = {"python", "ai", "python"}
```

## `str` কবে ব্যবহার করবে?

যখন text:

```python
message = "Hello"
```

---

# 15) Built-in vs specialized data types

Python-এর built-in data types ছাড়াও standard library-তে specialized data types আছে, যেমন date/time, arrays, heap queues, deque, enum ইত্যাদি। এগুলো built-in না হলেও official data types chapter-এ documented আছে। ([Python documentation][2])

উদাহরণ:

* `datetime`
* `collections.deque`
* `array.array`
* `enum.Enum`

---

# 16) Type hints নিয়ে ছোট note

Python-এর `typing` module type hints-এর জন্য vocabulary দেয়, কিন্তু runtime-এ Python নিজে function/variable annotations enforce করে না; এগুলো type checkers, IDEs, linters ইত্যাদির জন্য useful। ([Python documentation][5])

example:

```python
def add(a: int, b: int) -> int:
    return a + b
```

---

# 17) Interview-style summary table

| Type         | Example              |   Ordered | Mutable | Notes                   |
| ------------ | -------------------- | --------: | ------: | ----------------------- |
| `int`        | `10`                 |        No |      No | whole number            |
| `float`      | `3.14`               |        No |      No | decimal                 |
| `complex`    | `2+3j`               |        No |      No | imaginary part আছে      |
| `bool`       | `True`               |        No |      No | logical type            |
| `str`        | `"hello"`            |       Yes |      No | text / Unicode          |
| `list`       | `[1,2,3]`            |       Yes |     Yes | common mutable sequence |
| `tuple`      | `(1,2,3)`            |       Yes |      No | fixed sequence          |
| `range`      | `range(5)`           |       Yes |      No | integer sequence        |
| `dict`       | `{"a":1}`            | Key-based |     Yes | key-value               |
| `set`        | `{1,2,3}`            |        No |     Yes | unique items            |
| `frozenset`  | `frozenset([1,2])`   |        No |      No | immutable set           |
| `bytes`      | `b"abc"`             |       Yes |      No | binary data             |
| `bytearray`  | `bytearray(b"abc")`  |       Yes |     Yes | mutable binary          |
| `memoryview` | `memoryview(b"abc")` |      View | Depends | buffer view             |
| `NoneType`   | `None`               |        No |      No | no value                |

---

# 18) Very important beginner mistakes

## 1. list vs tuple গুলিয়ে ফেলা

```python
a = [1, 2, 3]   # mutable
b = (1, 2, 3)   # immutable
```

## 2. dict key mutable দেওয়া

```python
# wrong
# d = {[1,2]: "value"}   # Error

# correct
d = {(1,2): "value"}
```

## 3. set-এ duplicate আশা করা

```python
s = {1, 1, 2, 2}
print(s)   # {1, 2}
```

## 4. string change করার চেষ্টা

```python
text = "python"
# text[0] = "P"   # Error
```

## 5. `==` আর `is` mix করা

```python
a = None
print(a is None)   # best practice
```

---

# 19) Quick revision notes

মনে রাখার shortcut:

* **Number** → `int`, `float`, `complex`
* **True/False** → `bool`
* **Text** → `str`
* **Ordered mutable** → `list`
* **Ordered immutable** → `tuple`
* **Key-value** → `dict`
* **Unique items** → `set`
* **Immutable set** → `frozenset`
* **Binary** → `bytes`, `bytearray`, `memoryview`
* **No value** → `None`

---

# 20) Practice set

নিজে try করো:

```python
a = 25
b = 4.5
c = "Bangladesh"
d = [1, 2, 3]
e = (10, 20)
f = {"name": "Nadim", "age": 18}
g = {1, 2, 2, 3}
h = None

print(type(a))
print(type(b))
print(type(c))
print(type(d))
print(type(e))
print(type(f))
print(type(g))
print(type(h))
```
