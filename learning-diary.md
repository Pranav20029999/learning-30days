# Learning Diary

# Learning Diary — MIT 6.100L (Python)

---

## Day 1 — Lecture 1: Introduction to Computation

**What is Computation?**  
Computation is the process of following a precise sequence of steps (an algorithm) to transform **input** into **output**.  
It can involve:
- **Numerical tasks** — e.g., calculating interest rates
- **Symbolic tasks** — e.g., spell-checking, language translation
- **Mixed tasks** — e.g., simulations, AI, video games  

**Key characteristics of computation:**
1. **Precise instructions** — the computer must know exactly what to do.
2. **No ambiguity** — every step is clearly defined.
3. **Automation** — steps can be executed by a computer without human intervention.

**In simple terms:**  
Computation is *"turning instructions into results"* using logic, math, and rules.

---

**Code from Lecture 1:**
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

Day 2 — Lecture 2 Code
python
Copy
Edit
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


    Day 3 — Lecture 3 Code
python
Copy
Edit
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



    ChatGPT said:
Got it — you just want a clean learning-diary.md with only the exact code from each lecture, clearly labeled, no long notes.

Here’s the ready-to-paste version for Lectures 1–8:

markdown
Copy
Edit
# Learning Diary — MIT 6.100L Python Code

---

## Day 1 — Lecture 1 Code
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



Day 2 — Lecture 2 Code
python
Copy
Edit
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



Day 3 — Lecture 3 Code
python
Copy
Edit
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




Day 4 — Lecture 4 Code
python
Copy
Edit
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print("Factorial of 5:", factorial(5))


Day 5 — Lecture 5 Code
python
Copy
Edit
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



Day 6 — Lecture 6 Code
python
Copy
Edit
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



Day 7 — Lecture 7 Code
python
Copy
Edit
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



Day 8 — Lecture 8 Code
python
Copy
Edit
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







