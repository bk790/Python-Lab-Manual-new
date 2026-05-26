# Python Lab (Experiment 4–12)

---

# Experiment 4: File Word Frequency Analysis

## Aim

Develop a program to print the 10 most frequently appearing words in a file using a dictionary.

## Algorithm/Approach

1. Read file content and convert to lowercase.
2. Remove punctuation and split words.
3. Count frequencies using `Counter`.
4. Display top 10 frequent words.

## Required Input File

Create a file named:

`sample.txt`

### Example Content of `sample.txt`

```text
Hello world.
Hello again world.
Python is great.
Python programming is fun.
```

## Program

```python
from collections import Counter
import string

filename = "sample.txt"

with open(filename, 'r') as file:
    text = file.read().lower()

words = [
    word.strip(string.punctuation)
    for word in text.split()
    if word.strip(string.punctuation)
]

word_freq = Counter(words)
top_10 = word_freq.most_common(10)

print("Top 10 Most Frequent Words:")

for word, freq in top_10:
    print(f"{word}: {freq}")
```

## Sample Output

```text
Top 10 Most Frequent Words:
hello: 2
world: 2
python: 2
again: 1
is: 2
great: 1
programming: 1
fun: 1
```

---

# Experiment 5: Sorting Student Marks with Bubble Sort

## Aim

Read 6 subject marks, sort from highest to lowest using Bubble Sort, and display.

## Algorithm/Approach

1. Read marks into a list.
2. Apply Bubble Sort in descending order.
3. Display sorted marks.

## Program

```python
marks = []

for _ in range(6):
    marks.append(int(input("Enter mark: ")))

n = len(marks)

for i in range(n):
    for j in range(0, n - i - 1):
        if marks[j] < marks[j + 1]:
            marks[j], marks[j + 1] = marks[j + 1], marks[j]

print("Sorted Marks (Highest to Lowest):", marks)
```

## Sample Input

```text
85
92
78
95
88
70
```

## Sample Output

```text
Sorted Marks (Highest to Lowest): [95, 92, 88, 85, 78, 70]
```

---

# Experiment 6: File Sorting

## Aim

Sort the contents of a file and write to a new file.

## Algorithm/Approach

1. Read lines from input file.
2. Remove extra whitespace.
3. Sort lines alphabetically.
4. Write sorted lines into output file.

## Required Input File

Create a file named:

`input.txt`

### Example Content

```text
banana
apple
cherry
mango
grapes
```

## Program

```python
input_file = "input.txt"
output_file = "sorted_output.txt"

with open(input_file, 'r') as f:
    lines = [line.strip() for line in f.readlines() if line.strip()]

lines.sort()

with open(output_file, 'w') as f:
    for line in lines:
        f.write(line + '\n')

print("Sorted contents written to", output_file)
```

## Output File Generated

`sorted_output.txt`

### Example Output Content

```text
apple
banana
cherry
grapes
mango
```

---

# Experiment 7: Exception Handling in Division Function

## Aim

Develop DivExp function with assertion for `a > 0` and exception for `b = 0`.

## Algorithm/Approach

1. Define division function.
2. Assert that `a > 0`.
3. Raise exception if `b == 0`.
4. Return division result.

## Program

```python
def DivExp(a, b):

    assert a > 0, "a must be positive"

    if b == 0:
        raise ValueError("Division by zero!")

    return a / b


a = float(input("Enter a (>0): "))
b = float(input("Enter b: "))

try:
    result = DivExp(a, b)
    print(f"Result: {result}")

except AssertionError as e:
    print(f"Assertion Error: {e}")

except ValueError as e:
    print(f"Value Error: {e}")
```

## Sample Output

```text
Enter a (>0): 10
Enter b: 2
Result: 5.0
```

---

# Experiment 8: Complex Number Addition

## Aim

Define a Complex class and add complex numbers.

## Algorithm/Approach

1. Create Complex class.
2. Define methods for addition and display.
3. Read N complex numbers.
4. Compute total sum.

## Program

```python
class Complex:

    def __init__(self, real, imag):
        self.real = real
        self.imag = imag

    def __str__(self):
        return f"{self.real} + {self.imag}i"

    def add(self, other):
        return Complex(
            self.real + other.real,
            self.imag + other.imag
        )


def add_complex(c1, c2):
    return c1.add(c2)


N = int(input("Enter N (>=2): "))

total = Complex(0, 0)

for _ in range(N):

    real = float(input("Real: "))
    imag = float(input("Imag: "))

    c = Complex(real, imag)

    total = total.add(c)

print("Sum =", total)
```

## Sample Output

```text
Enter N (>=2): 2

Real: 2
Imag: 3

Real: 4
Imag: 5

Sum = 6.0 + 8.0i
```

---

# Experiment 9: Analysis Tool

## Aim

Analyze paragraph statistics such as frequency, sentence count, and longest word.

## Algorithm/Approach

1. Read paragraph.
2. Split words and remove punctuation.
3. Count word frequencies.
4. Count sentences.
5. Find longest word.

## Program

```python
from collections import Counter
import string

paragraph = input("Enter paragraph: ")

words = [
    word.strip(string.punctuation).lower()
    for word in paragraph.split()
]

sentences = [
    s.strip()
    for s in paragraph.split('.')
    if s.strip()
]

word_freq = Counter(words)

longest_word = max(words, key=len) if words else ""

print("Word Frequencies:", dict(word_freq))
print("Number of Sentences:", len(sentences))
print("Longest Word:", longest_word,
      f"(Length: {len(longest_word)})")
```

## Sample Output

```text
Enter paragraph: Hello world. This is a test.

Word Frequencies:
{'hello': 1, 'world': 1, 'this': 1, 'is': 1, 'a': 1, 'test': 1}

Number of Sentences: 2
Longest Word: hello (Length: 5)
```

---

# Experiment 10: Data Summary Generator

## Aim

Read CSV file and calculate max, min, and average values.

## Algorithm/Approach

1. Read CSV using `csv.DictReader`.
2. Store rows in list.
3. Read column name.
4. Calculate max, min, and average.

## Required Input File

Create a file named:

`data.csv`

### Example Content

```csv
col1,col2,col3
10,20,30
15,25,35
12,22,32
18,28,38
```

## Program

```python
import csv
from statistics import mean

filename = "data.csv"

data = []

with open(filename, 'r') as f:
    reader = csv.DictReader(f)

    for row in reader:
        data.append(row)

col = input("Enter column name: ")

values = [
    float(row[col])
    for row in data
    if col in row
]

if values:
    print(f"Max: {max(values)}")
    print(f"Min: {min(values)}")
    print(f"Average: {mean(values):.2f}")

else:
    print("Column not found!")
```

## Sample Output

```text
Enter column name: col1

Max: 18.0
Min: 10.0
Average: 13.75
```

---

# Experiment 11: Student Grade Tracker

## Aim

Accept multiple students’ names and marks and display summaries.

## Algorithm/Approach

1. Read student details.
2. Store in dictionary list.
3. Compute averages.
4. Find topper and overall average.

## Program

```python
from statistics import mean

students = []

N = int(input("Enter number of students: "))

for _ in range(N):

    name = input("Name: ")

    marks = list(
        map(int,
            input("Marks (space-separated): ").split())
    )

    students.append({
        'name': name,
        'marks': marks,
        'avg': sum(marks) / len(marks)
    })

print("\nStudent Averages:")

for s in students:
    print(f"{s['name']}: {s['avg']:.2f}")

overall_avg = mean([s['avg'] for s in students])

topper = max(
    students,
    key=lambda x: x['avg']
)

print(f"Overall Average: {overall_avg:.2f}")

print(
    f"Topper: {topper['name']} "
    f"({topper['avg']:.2f})"
)
```

## Sample Output

```text
Student Averages:
Alice: 87.50
Bob: 93.50

Overall Average: 90.50
Topper: Bob (93.50)
```

---

# Experiment 12: Recursive Directory Lister

## Aim

Display contents of a folder recursively.

## Algorithm/Approach

1. Use `os` module.
2. Traverse directories recursively.
3. Print folders and files.

## Required Folder Structure

```text
test/
│
├── file1.txt
├── file2.py
│
└── subdir/
    ├── notes.txt
    └── demo.py
```

## Program

```python
import os

def list_directory(path):

    for item in os.listdir(path):

        item_path = os.path.join(path, item)

        if os.path.isdir(item_path):

            print(f"Folder: {item}")

            list_directory(item_path)

        else:
            print(f"File: {item}")


path = input("Enter directory path: ")

list_directory(path)
```

## Sample Output

```text
Enter directory path: ./test

File: file1.txt
File: file2.py
Folder: subdir
File: notes.txt
File: demo.py
```
