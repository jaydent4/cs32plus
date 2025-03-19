# Memoization
This lesson goes into stuff that is not taught in CS 32 (in fact, this is a CS 180 concept). However, I personally think it is a pretty neat strategy that is very applicable with two topics the class has covered so far and a topic that was just covered: recursion, time complexity, and caching.

## What is bad about recursion?
If you did a thorough time complexity analysis of a recursive function, you may find that it has a bad time complexity. Let's look at the Fibonacci recursive function:

```python
def fib(n):
    if n == 0 or n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)
```

If we map the function calls, we get something called a "recursion tree." Let's run fib(4):

```
                 fib(4)
                /      \
          fib(3)        fib(2)
          /    \        /   \
      fib(2)   fib(1) fib(1)  fib(0)
      /    \
  fib(1)  fib(0)
```

Tracing out the function calls can lead us to obtainin a time complexity of O(2^n), which is not good at all (NOTE: Generally, a polynomial time complexity if considered efficient, especially compared to something that is exponential time). How can we optimize this?

## Memoization
Look at the recursion tree and see what is actually called. Notice how there is many repeated function calls (e.g. fib(2)). Every time we see a function call, we recursively find a return value each time and perform a lot of recomputations. Instead, what if we just saved certain computations instead of recomputing it.

For simplicity, let n < 32. Let us utilize some data structure to save computed function calls:

```python
def fib(n):
    def fib_efficient(n, memo):
        if n == 0 or n == 1:
            return 1
        if memo[n] != -1:
            return memo[n]
        memo[n] = fib_efficient(n - 1, memo) + fib_efficient (n - 2, memo)
        return memo[n]
    
    memo = [-1] * 32 # initialize all of them to -1, memo[n] == -1 implies that the function call fib(n) was never called
    return fib_efficient(n, memo)
```

Using the data structure `memo`, we are allowed to store computed values and reuse them whenever we see that value again. This strategy is called "memoization" because we are using a "memo" to store computed values. By caching these values, we can turn our O(n^2) algorithm to an O(n) algorithm.

Memoization is a subtopic of another core algorithm concept called "dynamic programming." The idea of using previous subproblems to solve our current problem (like in memoization) in an efficient way is the essence of dynamic programming.
