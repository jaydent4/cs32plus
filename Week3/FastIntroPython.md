# (Fast) Introduction to Python

I know that a lot of you don't have the time to go through documentations/tutorials about learning languages. Here is a really quick tutorial on Python that will (hopefully) teach you all that you need to do these types of questions (Fun Fact: I learned Python by solely doing Leetcode). As stated before, Python is the go-to language for coding interviews/assessments.

## Static vs. Dynamic Typing

C++ is statically-typed, meaning that variable types are defined at compile time (there is also static casting in C++ that can "switch" the type of a variable temporaily). For example:

```cpp
...
int x = 0;      // x is an integer!
double y = 1.5; // y is a double!
x = y + 1;      // x is still an integer, it is 2!
...
```

Since x is declared as an integer, x stays as an integer, even if we try to add a double (y) to it.\
In Python, it is a lot less strict. For example: 

```python
x = 0             # x is an integer!
x = "Hello World" # x is now a string!
x = float('inf')  # wait, x is now the float representation of infinity?!
x = Object()      # x is now an object! (more on Python OOP later in this lesson)
```
As seen from the exmaple, Python allows variables to be dynamically-typed, the type can "change." However, try not to assign a single variable with multiple types.\
NOTE: casting variables to a different type is okay and sometimes convenient, for example:

```python
x = "100"
int_x = int(x) # x is now 100 as an integer!
y = 100
str_y = str(y) # y is now "100" as a string!

# These are both okay!
```

## Basic Syntax and Functions
As you have probably seen already, there are no semicolons. Lines of code are denoted by new lines instead (see previous examples).\
Here is an example of a function in Python:
```python
def function(x): 
    x += 1 # increment x, same as x++ in C++ (+= is also a thing in C++)
    return x
```
There are a few things to note in this function.

1. Functions are also dynamically typed and are declared by using the keyword "def" instead of a type. Parameters are also dynamically-typed.
2. There is an indent. In C++, we have brackets that define what is encapsulated by a function. In Python, we don't. Indents define what is encapsulated under the function.
3. No semicolons! New lines mark the end of some line of code.

You can also define a type for functions and parameters if you would like. The above example with defined types might look like this:
```python
def function(x: int) -> int:
    x += 1
    return x
```

## Conditionals
Conditionals in Python are very similar to C++ conditionals. Here are a few examples of if-statements in Python:
```python
def conditionals(x, y):
    # Logical Operators!
    if x == 1:
        print("x is 1!") # print() is the same as std::cout << ... ;
    if x == 2 or x == 3:
        print("x is 2 or 3!")
    if x == 4 and y == 5:
        print("x is 4 and y is 5!")
    if x < 5:
        print("x is less than 5")
    if not x == 0:
        print("x is not zero")
    if x != 0:
        print("This is the same as the above conditional")
    
    # If-else, If-elif-else
    if x == 0:
        print("x is 0!")
    elif x == 10:
        print("This is an else-if or elif (in Python) and x is 10")
    else:
        print("This is an else case and x is not 0!")
        print("Goodbye!")
    
```

The only differences between Python and C++ conditionals is its syntax:
1. No parentheses around conditions.
2. Operators are just the word "and","or", and "not".
3. Indents show what is under the if-statement and it allows for multiple lines (like functions)
4. Colons ":" mark the end of the condition (kind of acts as the bracket)

## Loops
There are while loops and for loops in Python too. We will go over both here!

### While Loops
```python
def function(x):
    i = 0
    while i < x:
        print(i)
        i+= 1
    return i
```

Python while loops work the exact same way as they do in C++ and they also follow the same syntax as if-statements.\
For loops are a bit different, however...

### For Loops
```python
def function(x):
    for i in range(x):
        print(i)
```

This function mostly has the same functionality as the previous function aside from returning i. Calling range(n) will assign i to all values from 1 to n (non-inclusive, or in interval notation, [0, n)). Here is the general format for for loops:

```python
for [VARIABLE NAME] in [ITERABLE]:
    ...
```

There are other things that can go in [ITERABLE] but this will be covered in the next part of this lesson.



