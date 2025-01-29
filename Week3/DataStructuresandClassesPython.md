# Data Structures and Classes in Python
We will now go over a few data structures covered in class and some others that you might not have used before.\

## Arrays in Python (really called lists...)
In C++, there a are a few characteristics of arrays:
1. Zero-indexed: First item starts at 0.
2. Static Sizing: Size is determined at compile time (unless dynamically allocated).

In Python, "arrays" are zero-indexed as well. The difference lies in the latter characteristic. "Arrays" in Python are dynamically sized... and not really arrays. They are called lists and are more analogous to "std::vector" and "std::list" in C++ (covered later in the class). Here are a few operations we can do with lists in Python:

```python
empty = []                                  # create an empty list
non_empty_list = [1, 2, 3]                  # list with values inside
weird_list = [1, "hello", float('inf'), []] # anything can be placed in a list, even more lists! (try not to put objects of different types in the same list, however)

inserting_list = []
inserting_list.append(10)                   # inserting_list now has 10 in it (looks like [10])
x = inserting_list[0]                       # indexing inserting_list at index 0, x is now 10!

size_5_list = [1, 2, 3, 4, 5]
y = len(size_5_list)                        # We can get the size of the list (something you can't really do in C++ arrays)
total = sum(size_5_list)                    # total contains the sum of the list (15)
```

If you recall for-loops in the previous lesson, for-loops iterate over some kind of "iterable"--a list is one of those. We can do something like this:
```python
x = [10, 100, 1000, 10000]
for i in x:
    print(i)

"""
will print:
10
100
1000
10000
"""
```
i in our program will become each of the values of the list. This is analogous to something like this in C++:
```cpp
int arr[4] = {10, 100, 1000, 10000}
for (int i = 0; i < n; i++) {
    std::cout << arr[i] << std::endl;
}
```

There is a lot of stuff we can do with lists, but we will go over them when we need them.

## List Comprehension
Let's say we need a list to contain 5 0's (something like [0, 0, 0, 0, 0], we will need to do this a lot). We could do something like this:

```python
five_zeroes = []
for i in range(5):
    five_zeroes.append(0)
```

Instead, we can do this in one line, which will save us a lot of time:

```python
five_zeroes = [0] * 5
```

This will work for any primitive type.\
Now imagine a different scenario where we will need a list containing 5 empty lists (something like [[], [], [], [], []], we will also need to do this a lot). If we try the same thing as above.

```python
weird_nested_list = [[]] * 5
```

printing out this list would look fine, however, if we try to insert something in one of the lists, something weird happens...

```python
weird_nested_list[0].append(10)
```

printing this out, we get a strange output...

```
[[10], [10], [10], [10], [10]]
```

What happens internally is that doing the multiplication method results in each array index referencing the exact same list object (some weird memory stuff that is not really important, CS 131 will probably go more into programming language implementation if you are interested!). Instead, we use for-loops to create this type of list (among other types of lists):

```python
better_nested_list = [[] for _ in range(5)]
# note: using _ in a for-loop does not change any implementation, but it is a common practice if we just want to loop something and not care about the actual values 0-4

zero_to_four_list = [i for i in range(5)]    # creates the list [1, 2, 3, 4]

x = [1, 2, 3, 4, 5]

mult_ten_list = [i * 10 for i in x]          # creates the list [10, 20, 30, 40, 50]

three_by_three = [[0] * 3 for _ in range(3)] # we can combine both methods to create a 3x3 matrix of zeroes (very useful)

very_very_very_nested_list = [[[[] for _ in range(5)] for _ in range(5)] for _ in zero_to_five_listrange(5)] # creates a 3D list (very unlikely to actually use something like this)
```

This is called list comprehension and it is used to size and create lists. We can also do some very weird stuff with it like one-liner code (look up Code Golf if you want to see very weird code, it gets pretty crazy). Here is a funny example:

```python
"""
Given a list, return a list where we add 1 to numbers at odd indices and 2 to numbers at even indices.
"""

# Here is a normal solution:
def addOneAndTwo(nums):
    for i in range(len(nums)):
        if i % 2 == 1:
            nums[i] += 1
        else:
            nums[i] += 2
    return nums


# Here is a cool one-liner
def addOneAndTwoOneLine(nums):
    return [nums[i] + 1 if i % 2 == 0 else nums[i] + 2 for i in range(len(nums))]
```

Note: One-liners are not exactly preferable for interviews. If you have the chance to write it out, please write it out. Interviewers probably do not want to read the one-liner garbage like the one above...

## Tuples
Here is one more data structure that may not seem useful at first but we will use pretty often. They are called tuples and just refers to an ordered collection of numbers. Here is an example:

```python
two_items = (1, 2)
x = two_items[0] # x = 1
y = two_items[1] # y = 2
```

There is are two key characteristics of tuples that may not make sense right now, but are important to keep in mind:
1. tuples are immutable (you cannot change the values within a tuple)
2. tuples are hashable (you will learn later in the class what hashing is)

We will use these on occasion (usually combined with other data structures).

## Classes
For the purpose of doing interview/online assessment questions, classes are not too important but here is how to implement them:

```python
class MyClass:
    def __init__(self, val): # Constructor
        self.value = val
    
    def doSomething(self):   # Member function
        print(self.value)
    
    def __del__(self):       # Destructor (we don't use too often)
        print("goodbye")
```

The keyword "self" is a lot like "this" in C++. Additionally, you might know that there are no pointers in Python. We don't need to dynamically allocate anything using new nor do we need to delete objects manually (internally Python does clean up objects, but also more of a CS 131 thing). Here is an example of a linked list in Python:

```python
class ListNode:
    def __init__(self, val, next=None): # None represents a null, kind of like nullptr
        self.value = val
        self.next = next
...
n3 = ListNode(3)
n2 = ListNode(2, n3)
n1 = ListNode(1, n2)

# Creates 1 -> 2 -> 3 ->
```

While there are no pointers, still be careful about losing objects (like losing a list node).\

Those are the data structures and OOP we will cover for now. As we continue needing more specialized data structures (and you learn more in CS 32), we will cover more of them. For now, we will stick to using these.





