# Python for JS developer

## Intendation
Intendation is crucuial for Python, since there are no brackets, like in JS. Standard is 4 spaces, but any amount of spaces can be used while it remains consistent. 

## Variables and types
Every variable is an object in Python. 

Declaring a variable in general is similar to JS, so you don't need to specify a type.

You don't need to specify any keywords to declare variables, like, var, let or const. You just declare them:

```python
# Boolean
var_bool = True

# Integer
var_int = 5

# Float
var_float = 2.3
var_float2 = float(var_int)

# String
var_str = 'hello'
var_str2 = "hello"
```

Another way to declare variables:

```python
x, y = 3, 4
```

## Lists
Lists are generally similar to JS arrays. Initializing and accessing an element is the same, but other things are a bit different:

```python
var_list = []

# Adding an element
var_list.append(1)

# Getting a list length
len(var_list)

# Accessing index that is not exist will throw an IndexError
var_list[10]
```

## Numpy arrays
Alternative to lists. Advantages: fase, easy to work with, opportunity to perform calculatuins accross entire arrays.

```python
import numpy as np

height = [1.82, 1.65, 1.76]
weight = [80, 91, 68]

np_height = np.array(height)
np_weight = np.array(weight)

bmi = np_weight / np_height ** 2

print(bmi > 23)      # [ True  True False]
print(bmi[bmi > 23]) # [24.1516725 33.4251607]
```

## List comprehensions
Allow as to create a new list based on another list, in a single, readable line.

```python
animals = ['dog', 'crocodile', 'cat', 'bull', 'fox', 'bear']
three_letter_animals = [animal for animal in animals if len(animal) == 3]
print(three_letter_animals) # ['dog', 'cat', 'fox']
```

## Basic operations
Math operations are the same, but there are more functions of operators `+` or `*`:

```python
# Basic math
number = 1 + 2 * 3 / 4

# Remainder
remainder = 11 % 3

# Power
squared = 2 ** 2
cubed = 2 ** 3

# Concatenation of strings
"hello" + " " + "world"

# Repeating a string
"hello " * 10

list_a = [1, 2, 3]
list_b = [3, 4, 5]
list_a + list_b

# Repeating a list
[1, 2, 3] * 3

# Attempt to concatenate string and number will throw a TypeError
1 + "hello"
```

## String formatting and text output
You can output text to the console using `print` method.
Variables can be formatted if you need concatenate them with a string.


Old style (% operator):

```python
# %s - String (or any object with a string representation, like numbers)
# %d - Integers
# %f - Floating point numbers
# %.<number of digits>f - Floating point numbers with a fixed amount of digits to the right of the dot.
# %x/%X - Integers in hex representation (lowercase/uppercase)

name = "Mike";
age = 31;

print("Hello, %s!" % name)
print("%s is %d years old." % (name, age))

# Not a string can be formatted as string as well
mylist = [1, 2, 3]
print("List: %s." % mylist)
```

New style (str.format) is preffered over %-style formatting:

```python
name = "Mike"
greeting = "Hello"

"Hello, {}!".format(name)

"{greeting}, {name}!".format(greeting=greeting, name=name)
```

String interpolation / f-Strings (Python 3.6+) is similar to JS:

```
name = "Mike"

f'Hello, {name}!'
```

Template strings (standard library):

```python
from string import Template

name = "Mike"

t = Template('Hello, $name!')
t.substitute(name=name)
```

## Basic string operations
You can use single quotes as well as double qoutes to declare as string the same way as in JS. String methods usually can do the same things:

```python
str = "Hello world!"

# Finding index of the char
str.index('d')

# Selecting part of a string [start:stop:step]
str[3:4]   # l
str[3:7]   # lo w
str[3:7:2] # l

# Reversing a string
str[::-1]

# Changing case of the letters
str.lower()
str.upper()

# Check on occurences
str.startswith('Hello')
str.endswith('!')

# Splitting string to be a list
list_of_strings = str.split(' ')
```

## Conditions
Equality operators are the same to JS ones, but there is no strict equality operator `===`, because all variables are already compared this way.

Values are considered truthy:
1. `True`
2. Not empty object

Values are considered falsy:
1. `False`
2. `""`
3. `[]`
4. `0`

Boolean operators are the same, but syntax is a bit different:

```python
name = "Mike"
salary = 5000
role = "developer"
if name == "Mike" and (salary < 5000 or (not role == "manager")):
    pass # this operator can be used as noop for conditions or in loops
```

You can check if there something in the list, like `Array.prototype.includes`:

```python
if "Mike" in ["Mike", "Alex"]:
    pass
```

Full syntax of `if/else` is the next:

```python
statement = False
another_statement = False

if statement is True:
    pass
elif another_statement is True:
    pass
else:
    pass
```

The is operator matches instances of variables rather than values:

```python
x = [1,2,3]
y = [1,2,3]

x == y # True
x is y # False
```

## Loops
`for` is similar to `for in` in JS:

```python
employees = ["Mike", "Joe"]
for employee in employees:
    print(employee)
```

Functions `range` and `xrange` allow as to create sequence of number. `xrange` returns an iterator. In Python 3 `range` acts like `xrange`. We can use this function to iterate over some generated sequence:

```python
for x in range(5):
    pass # 0, 1, 2, 3, 4

for x in range(1, 4):
    pass # 1, 2, 3

for x in range(1, 5, 2):
    pass # 1, 3
```

Behavior of `while`, `break` and `continue` statemens are the same.

Unlike in JS we can use `else` with loops alltogether:

```python
statement = True
while(statement):
    statement = False
else:
    print("statement is not True anymore")

for index in range(1, 10):
    break
else:
    print("if the loop terminated because of break but not due to fail in condition then else block won't be executed")
```

## Functions
Function can be declared using `def` keyword:

```python
def fn_without_args():
    pass

def fn_with_args(arg1, arg2):
    pass

fn_without_args()
fn_with_args(1, 2)
```

## Lambda functions
Similar to JS function expressions by nature, even more to arrow functions, because of short syntax without `return` keyword.

```python
add = lambda a, b : a + b
add(1, 2)
```

## Function arguments
Similar to JS rest operator usage:

```python
def sum(*arguments):
    sum = 0
    for i in list(arguments):
        sum += i
    return sum
sum(1, 2, 3)

def calc(operation, *operands):
    result = 0
    if operation == 'sum':
        for i in list(operands):
            result += i
    # other operations...
    return result
calc('sum', 2, 3)
```

There is a way to pass arguments with names, where order does not matter, like using object in JS.

```python
def calc(a, b, **options):
    if options.get('action') == 'sub':
        return a - b
    # other operations...
    return a + b
calc(2, 2, action = 'sub')
```

## Classes
```python
class Employee:
    is_internal = True

    def __init__(self, name): # like constructor in JS
        self.name = name

    def setSalary(self, salary): # self is like this in JS 
        is (self.is_internal):
            self.salary = salary

mike = Employee('Mike') # you don't need a keyword new like in JS 
mike.setSalary(10000)
print(mike.salary)
```

## Dictionaries
Dictionary is a similar to JS object. You can create them with a set of fields, even nested ones, and also accessing, adding, deleting them as well as iterating over them:

```python
config = {
    "description": "Employees config", # using quotes for a key name is obligatory
    "salaries": {}
}

# Accessing
config["description"]

# Adding
config["salaries"]["Mike"] = 10000
config["salaries"]["Jessica"] = 5000
config["salaries"]["Bob"] = 7000

# Deleting
del config["salaries"]["Jessica"]
# Or
config["salaries"].pop("Bob")

# Iterating over
for employee, salary in config["salaries"].items():
    pass
```

## Pandas DataFrames
Allow to store and manipulate tabular data:

```python
import pandas as pd

dict = {
    "employee": ["Mike", "Bob", "Jessica"],
    "salary": [10000, 5000, 7000],
    "role": ["developer", "manager", "developer"],
}

employees = pd.DataFrame(dict)

print(employees)  
#   employee  salary       role
# 0     Mike   10000  developer
# 1      Bob    5000    manager
# 2  Jessica    7000  developer

# If you'd like to change indexes 0, 1, 2 to something other:
employees.index = ["M", "B", "J"]

# It's also possible to import data from csv file:
employees = pd.read_csv('employees.csv', index_col=0)

print(employees)
#          age  salary       role seniority
# name                                     
# Mike      31   10000  developer    senior
# Bob       40    5000    manager    junior
# Jessica   27    7000  developer    middle

# Print out salary column as Pandas Series
print(employees['salary'])

# Print out salary column as Pandas DataFrame
print(employees[['salary']])

# Print out DataFrame with role and salary columns
print(employees[['role', 'salary']])

# You can use the next syncax to access obserwations (rows) from a DataFrame.
# Print out first two rows
print(employees[0:2])

# Print observation for Mike (by index number)
print(employees.iloc(0))

# Print observations by index names
print(employees.loc[['Mike', 'Jessica']])
```

## Modules
Modules importing is similar as JS `import` works: it executing mode in the imported module only once, so local variables inside the module are singletones.

```python
# Importing module
import calc
calc.add(1, 2)

# Importing module objects to the current namespace
from calc import add
add(1, 2)

# Importing all objects from a module
from calc import *
mul(5, 6)

# Custom import name
from calc import mul as multiply
multiply(5, 6)
```

Note that you don't need to export variables or functions from the module like in JS, they are all can be imported by default.

You can create packages. Package is a namespace that can contain multiple packages and modules. It's just a directory, that is contains special file `__init__.py`:

```
calc/
    __init__.py
    system.py
    calc.py
```

This file can be empty, but can also contain some settings, for example this mean that only module `calc` is exported:

```python
# __init__.py
__all__ = ["calc"]
```

Standard modules library can be found here:
https://docs.python.org/3/library/

## Generators
Similar to JS:

```python
import types

def fibonacci():
    a, b = 1, 1
    while 1:
        yield a
        a, b = b, a + b

if type(fibonacci()) == types.GeneratorType:
    counter = 0
    for n in fibonacci():
        print(n) # 1 1 2 3 5 8 11
        counter += 1
        if counter == 7:
            break
else:
    print('Function is not a generator')
```

## Regular expressions
Docs can be found [here](https://docs.python.org/3/library/re.html#regular-expression-syntax%22RE%20syntax).

```python
import re

all_lowercase_letters_pattern = re.compile(r"^[a-z]+$")
bool(re.match(all_lowercase_letters_pattern, 'lowercase')) # True
bool(re.match(all_lowercase_letters_pattern, 'camelCase')) # False

cat_pattern = re.compile(r"cat")
re.search(cat_pattern, 'dog, cat and parrot').span() # (5, 8)
```

## Exception handling
Unlike JS, there is a possibility to catch exact error:

```python
try:
    print(a)
except NameError:
    print("You need to declare variable 'a' before using")
```

Or any other error:

```python
try:
    print(a)
except Exception:
    print("Unexpected error has happened")
```

More can be found in [docs](https://docs.python.org/3/tutorial/errors.html#handling-exceptions)
