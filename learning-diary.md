# MIT Python Learning Diary

A daily diary summarizing concepts, code, and key learnings from the MIT Python lectures.

---

## **Day 1 — Lecture 1: Introduction to Python**

**Topics Covered:**
- Basic printing and variables
- Arithmetic operations

**Code:**
```python
print("Hello, world!")

x = 3
print(x)
print(x * x)
print("My favorite number is", x)

x, y = 3, 4
print("x:", x, "y:", y)

print("Sum:", x + y)
print("Difference:", x - y)
print("Product:", x * y)
print("Quotient:", x / y)
print("Power:", x ** y)
```

---

## **Day 2 — Lecture 2: Conditionals and Loops**

**Topics Covered:**
- Input and integer conversion
- If/else statements
- While and for loops

**Code:**
```python
x = int(input("Enter an integer: "))

if x % 2 == 0:
    print("Even")
else:
    print("Odd")

count = 0
while count < 5:
    print(count)
    count += 1

for i in range(5):
    print("i:", i)
```

---

## **Day 3 — Lecture 3: Functions and Approximations**

**Topics Covered:**
- Defining and using functions
- Even/odd checker
- Cube root approximation (linear search)

**Code:**
```python
def is_even(i):
    return i % 2 == 0

print("All numbers between 0 and 20: even or not")
for i in range(21):
    if is_even(i):
        print(i, "even")
    else:
        print(i, "odd")

cube = 27
epsilon = 0.01
guess = 0.0
increment = 0.0001
num_guesses = 0

while abs(guess**3 - cube) >= epsilon:
    guess += increment
    num_guesses += 1

print('num_guesses =', num_guesses)

if abs(guess**3 - cube) >= epsilon:
    print('Failed on cube root of', cube)
else:
    print(guess, 'is close to the cube root of', cube)
```

---

## **Day 4 — Lecture 4: Recursion**

**Topics Covered:**
- Writing recursive functions

**Code:**
```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print("Factorial of 5:", factorial(5))
```

---

## **Day 5 — Lecture 5: Tuples & Data Manipulation**

**Topics Covered:**
- Tuples
- Extracting data and unique elements

**Code:**
```python
def get_data(aTuple):
    nums = ()
    words = ()
    for t in aTuple:
        nums = nums + (t[0],)
        if t[1] not in words:
            words = words + (t[1],)
    min_n = min(nums)
    max_n = max(nums)
    unique_words = len(words)
    return (min_n, max_n, unique_words)

sample = ((1, 'apple'), (3, 'banana'), (2, 'apple'), (5, 'orange'))
result = get_data(sample)
print(result)
```

---

## **Day 6 — Lecture 6: Towers of Hanoi (Recursion Example)**

**Topics Covered:**
- Recursive problem-solving

**Code:**
```python
def printMove(fr, to):
    print('Move from', fr, 'to', to)

def Towers(n, fr, to, spare):
    if n == 1:
        printMove(fr, to)
    else:
        Towers(n - 1, fr, spare, to)
        Towers(1, fr, to, spare)
        Towers(n - 1, spare, to, fr)

Towers(3, 'A', 'C', 'B')
```

---

## **Day 7 — Lecture 7: Exception Handling and Data Structures**

**Topics Covered:**
- Average calculation
- Exception handling (try/except)
- Nested lists

**Code:**
```python
def avg(grades):
    try:
        return sum(grades) / len(grades)
    except ZeroDivisionError:
        print('warning: no grades data')
        return 0.0

def get_stats(class_list):
    new_stats = []
    for elt in class_list:
        new_stats.append([elt[0], elt[1], avg(elt[1])])
    return new_stats

students = [
    [['peter', 'parker'], [10.0, 5.0, 85.0]],
    [['bruce', 'wayne'], [10.0, 8.0, 74.0]],
    [['captain', 'america'], [0.0, 10.0, 90.0]],
    [['deadpool'], []]
]

stats = get_stats(students)
for student in stats:
    print(student)

try:
    a = int(input("Tell me one number: "))
    b = int(input("Tell me another number: "))
    print("a / b =", a / b)
    print("a + b =", a + b)
except ValueError:
    print("Could not convert to a number.")
except ZeroDivisionError:
    print("Can't divide by zero.")
except:
    print("Something went very wrong.")
```

---

## **Day 8 — Lecture 8: Classes and Objects**

**Topics Covered:**
- Object-oriented programming
- Defining and using classes

**Code:**
```python
class Coordinate(object):
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def distance(self, other):
        x_diff_sq = (self.x - other.x) ** 2
        y_diff_sq = (self.y - other.y) ** 2
        return (x_diff_sq + y_diff_sq) ** 0.5

p1 = Coordinate(3, 4)
p2 = Coordinate(0, 0)
print(p1.distance(p2))  # Output: 5.0
```

---

## **Day 9 — Lecture 9: Inheritance and More OOP**

**Topics Covered:**
- Inheritance
- Class variables
- Parent-child relationships

**Code:**
```python
# Base Animal class
class Animal(object):
    def __init__(self, age):
        self.age = age
        self.name = None

    def get_age(self):
        return self.age

    def get_name(self):
        return self.name

    def set_age(self, newage):
        self.age = newage

    def set_name(self, newname=""):
        self.name = newname

    def __str__(self):
        return "animal: " + str(self.name) + ":" + str(self.age)

# Rabbit class inheriting from Animal
class Rabbit(Animal):
    tag = 1  # Class variable to keep unique IDs

    def __init__(self, age, parent1=None, parent2=None):
        Animal.__init__(self, age)
        self.parent1 = parent1
        self.parent2 = parent2
        self.rid = Rabbit.tag
        Rabbit.tag += 1

    def get_rid(self):
        return str(self.rid).zfill(3)  # Pads with zeros, e.g., 001

    def get_parent1(self):
        return self.parent1

    def get_parent2(self):
        return self.parent2

    def __str__(self):
        return "rabbit: " + str(self.get_rid())

# Running Example
if __name__ == "__main__":
    r1 = Rabbit(2)
    r1.set_name("Bunny")

    r2 = Rabbit(3)
    r2.set_name("Snowy")

    r3 = Rabbit(1, r1, r2)  # Child rabbit with parents r1 and r2
    r3.set_name("Fluffy")

    # Print rabbits
    print(r1)  # rabbit: 001
    print(r2)  # rabbit: 002
    print(r3)  # rabbit: 003

    # Access parents
    print("Fluffy's parents:", r3.get_parent1().get_name(), "and", r3.get_parent2().get_name())
```

---

## **Day 10 — Lecture 10: Understanding Program Efficiency (Part 1)**

**Concepts Learned:**
- Program efficiency describes how runtime grows with input size.
- **Big-O notation** is used to analyze algorithm growth rates:
  - Linear Search → O(n)
  - Bisection Search → O(log n)

**Code:**
```python
# Linear Search (O(n))
def linear_search(L, x):
    for e in L:
        if e == x:
            return True
    return False

# Bisection Search (O(log n)) - works on sorted lists
def bisection_search(L, x):
    low = 0
    high = len(L) - 1
    while low <= high:
        mid = (low + high) // 2
        if L[mid] == x:
            return True
        elif L[mid] < x:
            low = mid + 1
        else:
            high = mid - 1
    return False

# Example usage
L = list(range(100))
print(linear_search(L, 42))      # True
print(bisection_search(L, 42))   # True
```

---

## **Day 11 — Lecture 11: Program Efficiency (Part 2) and Search Comparison**

**Key Concepts:**
- **Big-O Notation**: A way to measure algorithm efficiency.
- **Linear Search (O(n))**: Checks elements one by one.
- **Binary Search (O(log n))**: Divides list in half each step.
- **Sorting Efficiency**: Some algorithms (like bubble sort) are slower compared to built-in optimized ones.

**Practice Problem:** Compare Linear Search vs. Binary Search.

**Code:**
```python
import random
import time

def linear_search(lst, target):
    for i in range(len(lst)):
        if lst[i] == target:
            return i
    return -1

def binary_search(lst, target):
    low = 0
    high = len(lst) - 1
    while low <= high:
        mid = (low + high) // 2
        if lst[mid] == target:
            return mid
        elif lst[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1

size = 1000000
sorted_list = list(range(size))
target = random.randint(0, size - 1)

start = time.time()
linear_result = linear_search(sorted_list, target)
end = time.time()
print("Linear Search:", end - start, "seconds")

start = time.time()
binary_result = binary_search(sorted_list, target)
end = time.time()
print("Binary Search:", end - start, "seconds")
```

---

## **Day 12 — Lecture 12: Sorting Algorithms**

**Key Concepts:**
- Bubble Sort and Selection Sort (simple but slow for large lists)
- Python's built-in sort is much faster

**Code:**
```python
import random
import time

# Bubble Sort
def bubble_sort(lst):
    n = len(lst)
    for i in range(n):
        for j in range(0, n - i - 1):
            if lst[j] > lst[j + 1]:
                lst[j], lst[j + 1] = lst[j + 1], lst[j]
    return lst

# Selection Sort
def selection_sort(lst):
    n = len(lst)
    for i in range(n):
        min_index = i
        for j in range(i + 1, n):
            if lst[j] < lst[min_index]:
                min_index = j
        lst[i], lst[min_index] = lst[min_index], lst[i]
    return lst

# Test Performance
size = 5000  # bubble/selection are slow for big lists
nums = [random.randint(0, 10000) for _ in range(size)]

# Bubble Sort
nums_copy = nums[:]
start = time.time()
bubble_sort(nums_copy)
end = time.time()
print("Bubble Sort Time:", end - start, "seconds")

# Selection Sort
nums_copy = nums[:]
start = time.time()
selection_sort(nums_copy)
end = time.time()
print("Selection Sort Time:", end - start, "seconds")

# Python's Built-in Sort
nums_copy = nums[:]
start = time.time()
nums_copy.sort()
end = time.time()
print("Python Built-in Sort Time:", end - start, "seconds")
```

---

> _End of diary. More lectures and code coming soon!_



## codes from MIT 6.100L

## Lecture 7: Decomposition, Abstraction, and Functions

**Code Examples:**

```python
# Example: Function to compute square root using Newton-Raphson method

def sqrt_newton(x, epsilon=1e-6):
    guess = x / 2.0
    while abs(guess * guess - x) > epsilon:
        guess = guess - (((guess ** 2) - x) / (2 * guess))
    return guess

print("Square root of 25:", sqrt_newton(25))
print("Square root of 2:", sqrt_newton(2))




## **Day 8 — Lecture 8: Functions as Objects**

**Topics Covered:**
- Functions can be passed as arguments and used as objects in Python

**Code:**

def square(x):
    return x * x

def cube(x):
    return x * x * x

def apply_func(f, values):
    result = []
    for val in values:
        result.append(f(val))
    return result

nums = [1, 2, 3, 4, 5]
print("Squares:", apply_func(square, nums))
print("Cubes:", apply_func(cube, nums))
```

---

## **Day 9 — Lecture 9: Lambda Functions, Tuples, and Lists**

**Topics Covered:**
- Lambda (anonymous) functions
- Tuples and lists

**Code:**
```python
# Lambda Functions
square = lambda x: x * x
add = lambda a, b: a + b

print("Square of 5:", square(5))
print("Sum of 3 and 7:", add(3, 7))
```

---

## **Day 10 — Lecture 10: Lists and Mutability**

**Topics Covered:**
- Lists are mutable (can be changed)
- List methods: append, insert, remove

**Code:**
```python
animals = ["cat", "dog", "rabbit"]
print("Original list:", animals)

# Change element
animals[0] = "lion"
print("After change:", animals)

# Add new elements
animals.append("tiger")
print("After append:", animals)

# Insert at position
animals.insert(1, "elephant")
print("After insert:", animals)

# Remove elements
animals.remove("dog")
print("After remove:", animals)


Day 11 — Lecture 11: Aliasing and Cloning
Topics Covered:

Aliasing: When two variables refer to the same list
Cloning: Creating a copy of a list to avoid aliasing
Code:

# Aliasing example
a = [1, 2, 3]
b = a  # b is an alias for a (both point to the same list)

print("Original a:", a)
print("Original b:", b)

b[0] = 100  # Changing b also changes a
print("After modifying b:")
print("a:", a)
print("b:", b)

# Cloning example
a = [1, 2, 3]
b = a[:]  # Clone using slicing

print("\nOriginal a:", a)
print("Cloned b:", b)

b[0] = 100  # Changing b does NOT change a
print("After modifying b:")
print("a:", a)
print("b:", b)







