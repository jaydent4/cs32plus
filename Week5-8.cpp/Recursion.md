# Recursion

## Recursion in Python
Recursion in Python works the same way it works in C++ (or any language, really). Here is a quick example on computing the nth Fibonacci number:

```python
def fibonacci(n):
    if n == 0 or n == 1:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)
```

As in any recursive function, this function has a **base case** and a **recursive step**.

## Some helpful techniques for recursion (maybe)
Something that may be helpful is creating a helper function that solves a question recursively when the original function does not have convenient parameters for it. In some languages (like C++), we have to define it outside like this:

```cpp
int helper_recursive() {
    ...
}

int original_function() {
    return helper_recursive();
}
```

In Python, we can nest functions like this:

```python
def original_function():
    def helper_recursive():
        # implementation here
    
    return helper_recursive()
```

Does this help with anything? No. Is there an actual reason to do this? No. But, this allows us to compact our recursive function into the original function. It is a personal preference at the end of the day.