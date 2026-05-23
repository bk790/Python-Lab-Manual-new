# Module 4: Modules, Mutability, and OOP

---

# Part 1: Modules

# What is a Module?

A **module** is a Python file containing functions, variables, and classes that can be reused in other programs.

## Advantages of Modules

* Code reuse
* Better organization
* Easier debugging
* Avoids repetition

---

# Random Module

The `random` module generates pseudorandom numbers.

## Example 1: random()

```python
import random

print(random.random())
```

### Output

```python
0.5738291
```

---

## Example 2: randint()

```python
import random

print(random.randint(1, 10))
```

---

## Example 3: choice()

```python
import random

colors = ["Red", "Blue", "Green"]

print(random.choice(colors))
```

---

## Example 4: shuffle()

```python
import random

numbers = [1,2,3,4,5]

random.shuffle(numbers)

print(numbers)
```

---

# Time Module

The `time` module is used for:

* delays
* execution time
* timestamps

---

## Example 1: Current Time

```python
import time

print(time.time())
```

---

## Example 2: Sleep Function

```python
import time

print("Start")

time.sleep(3)

print("End")
```

---

## Example 3: Execution Time

```python
import time

start = time.time()

for i in range(1000000):
    pass

end = time.time()

print("Execution Time:", end - start)
```

---

# Math Module

Provides mathematical functions.

---

## Example 1: Constants

```python
import math

print(math.pi)
print(math.e)
```

---

## Example 2: Square Root

```python
import math

print(math.sqrt(25))
```

---

## Example 3: Trigonometric Functions

```python
import math

print(math.sin(0))
print(math.cos(0))
```

---

# Creating User-Defined Modules

## File: calculator.py

```python
def add(a, b):
    return a + b

def sub(a, b):
    return a - b
```

---

## Main Program

```python
import calculator

print(calculator.add(10, 5))
print(calculator.sub(10, 5))
```

---

# Namespace

A namespace stores identifiers:

* variables
* functions
* classes

---

## Example Program

```python
x = 100

def display():
    y = 50
    print(y)

display()

print(x)
```

---

# LEGB Rule

Python searches variables in this order:

1. Local
2. Enclosing
3. Global
4. Built-in

---

## Example Program

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

### Output

```python
local
```

---

# Attributes and Dot Operator

Dot operator (`.`) accesses attributes and methods.

---

## Example Program

```python
import math

print(math.pi)
print(math.sqrt(16))
```

---

# Import Statement Variants

---

## 1. Standard Import

```python
import math

print(math.pi)
```

---

## 2. Specific Import

```python
from math import sqrt

print(sqrt(36))
```

---

## 3. Wildcard Import

```python
from math import *

print(cos(0))
```

---

# Part 2: Mutable and Immutable Objects

# Immutable Objects

Cannot be changed after creation.

Examples:

* int
* float
* string
* tuple

---

## Example 1: Integer

```python
x = 10

print(id(x))

x = x + 5

print(id(x))
```

Different IDs occur because a new object is created.

---

## Example 2: String

```python
name = "Python"

print(id(name))

name = name + " Programming"

print(id(name))
```

---

# Mutable Objects

Can be modified after creation.

Examples:

* list
* dictionary
* set

---

## Example 1: List

```python
numbers = [1,2,3]

numbers[0] = 99

print(numbers)
```

---

## Example 2: Dictionary

```python
student = {"name": "Bhanu"}

student["marks"] = 95

print(student)
```

---

# Aliasing

Two variables referring to the same object.

---

## Example Program

```python
list1 = [1,2,3]

list2 = list1

list2[0] = 99

print(list1)
print(list2)
```

### Output

```python
[99, 2, 3]
[99, 2, 3]
```

---

# Cloning to Avoid Aliasing

```python
list1 = [1,2,3]

list2 = list1.copy()

list2[0] = 99

print(list1)
print(list2)
```

### Output

```python
[1, 2, 3]
[99, 2, 3]
```

---

# Part 3: Object Oriented Programming

# Class

A class is a blueprint for objects.

---

# Object

An object is an instance of a class.

---

# Example Program

```python
class Student:

    def __init__(self, name):

        self.name = name


s1 = Student("Bhanu")

print(s1.name)
```

---

# Attributes

Attributes are variables inside objects.

---

## Example Program

```python
class Point:
    pass

p1 = Point()

p1.x = 3
p1.y = 4

print(p1.x)
print(p1.y)
```

---

# Constructor (**init**)

Automatically called when object is created.

---

## Example Program

```python
class Person:

    def __init__(self, name, age):

        self.name = name
        self.age = age


p = Person("Bhanu", 22)

print(p.name)
print(p.age)
```

---

# Methods

Methods are functions inside classes.

---

## Example Program

```python
class Calculator:

    def add(self, a, b):

        return a + b


c = Calculator()

print(c.add(10, 20))
```

---

# self Keyword

`self` refers to the current object.

---

## Example Program

```python
class Demo:

    def show(self):

        print("Current object:", self)


d = Demo()

d.show()
```

---

# Instance Variables

Variables unique to each object.

---

## Example Program

```python
class Student:

    def __init__(self, name):

        self.name = name


s1 = Student("Alice")
s2 = Student("Bob")

print(s1.name)
print(s2.name)
```

---

# Class Variables

Shared by all objects.

---

## Example Program

```python
class Student:

    school = "ABC School"

    def __init__(self, name):

        self.name = name


s1 = Student("Alice")
s2 = Student("Bob")

print(s1.school)
print(s2.school)
```

---

# Object Methods

```python
class Point:

    def __init__(self, x, y):

        self.x = x
        self.y = y

    def move_up(self, amount):

        self.y += amount


p = Point(5, 10)

p.move_up(3)

print(p.y)
```

---

# Objects as Arguments

```python
class Point:

    def __init__(self, x, y):

        self.x = x
        self.y = y


def display(point):

    print(point.x, point.y)


p = Point(2, 4)

display(p)
```

---

# Objects as Return Values

```python
class Point:

    def __init__(self, x, y):

        self.x = x
        self.y = y


def midpoint(p1, p2):

    mx = (p1.x + p2.x) / 2
    my = (p1.y + p2.y) / 2

    return Point(mx, my)


a = Point(2, 4)
b = Point(6, 8)

m = midpoint(a, b)

print(m.x, m.y)
```

---

# **str** Method

Defines object string representation.

---

## Example Program

```python
class Point:

    def __init__(self, x, y):

        self.x = x
        self.y = y

    def __str__(self):

        return f"({self.x}, {self.y})"


p = Point(7, 8)

print(p)
```

---

# == vs is Operator

---

## == Operator

Checks values.

---

## is Operator

Checks memory identity.

---

## Example Program

```python
a = [1,2,3]
b = [1,2,3]

print(a == b)
print(a is b)
```

### Output

```python
True
False
```

---

# Practice Program: Stopwatch

```python
import random
import time

intervals = []

for i in range(5):

    t = random.randint(1, 3)

    start = time.time()

    time.sleep(t)

    end = time.time()

    elapsed = end - start

    intervals.append(elapsed)

print(intervals)

avg = sum(intervals) / len(intervals)

print("Average:", avg)
```

---

# utilities.py Module

```python
def square(x):
    return x * x

def cube(x):
    return x * x * x

def factorial(n):

    f = 1

    for i in range(1, n+1):

        f *= i

    return f
```

---

# Using Standard Import

```python
import utilities

print(utilities.square(5))
```

---

# Using Specific Import

```python
from utilities import cube

print(cube(3))
```

---

# Using Wildcard Import

```python
from utilities import *

print(factorial(5))
```

---

# mathfunc.py

```python
def factorial(n):

    f = 1

    for i in range(1, n+1):

        f *= i

    return f
```

---

# Binomial Coefficient Program

```python
import mathfunc

n = int(input("Enter n: "))
r = int(input("Enter r: "))

nCr = mathfunc.factorial(n) / (
       mathfunc.factorial(r) *
       mathfunc.factorial(n-r)
)

print("Binomial Coefficient:", nCr)
```

---

# Formula

$$
nCr = \frac{n!}{r!(n-r)!}
$$
