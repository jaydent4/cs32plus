# Stacks and Queues
Python also has "built-in" (not really) stacks and queues too. We will show how to implement and use them.

## Stacks
Here is a simple stack implementation:

```python
stack = []
```

... and yes, a stack in Python is pretty much just a list. Here are a few things we can do with them (pretty much the same as in C++):

```python
stack = []
stack.append(10)
stack.append(20)
stack.append(30) # stack now contains [10, 20, 30]
x = stack.pop()  # stack now contains [10, 20] and x = 30
```

Note: since stacks are just lists, we can still do list things with them.

## Queues
Queues can be implemented using a list as well with the only change being:

```python
queue = []
queue.append(10)
queue.append(20)
queue.append(30)
y = queue.pop(0) # Pop the index 0
```

However, this is an inefficient way of doing this (if you know about time complexity, doing queue.pop(0) is an O(n) operation). Instead, we will use a library:

```python
import collections # library, analogous to #include in C++

queue = deque()
queue.append(10)
queue.append(20)
queue.append(30)
z = queue.popleft()
```

We use deque() to have an efficient queue implementation (we can also use deque for stacks and call stack.popright() instead).\

While stacks and queues seem very niche in terms of their use cases, the next lesson will go over very crucial use cases for these data structures. It turns out, they are incredibly useful!

