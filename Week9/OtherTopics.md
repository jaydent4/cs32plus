# Other Topics

There are obviously a lot more topics to cover. However, due to the lack of time (and possibly my poor time management), we cannot cover all of the necessary topics. While I may expand on these topics in the future, I'll just list them here for now.

## Binary Search
In CS 32, you have learned how to implement and use binary search. The question is now when we use it. We could use binary search in the following conditions:

1. We want to to avoid linear searching (O(n) vs. O(logn)).
2. Our data has some kind of ordering to it (sorted, non-decreasing, non-increasing, sorted with displacement).
3. Data is bounded. We must know that our result must fall within a minimum and maximum value.

These conditions allow us to perform the search.

## Sliding Window
A sliding window is implemented two pointers/indices that represent some subarray. We often use the slding window in combination with other algorithm types when some part of our result involves dealing with contiguous subarrays.

## Prefix Sum
Let's say we want to calculate the sum of any given subarray in some array. One way we can do this by using the `sum()` function in python on the subarray. However, this is an O(n) operation as it adds all of the numbers every time (a lot of revisiting). Instead, we can use a prefix sum array. A prefix sum follows the recurrence relation on the prefix array `prefix` and number array `nums`: `prefix[i] = prefix[i - 1] + nums[i]` or `prefix[i] = prefix[i - 1] + nums[i - 1]` if you initialize the first value of the prefix sum array to be 0. For example:

```python
nums = [1, 2, 3, 4, 5]
prefix = [0, 1, 3, 6, 10, 15] # initial value is 0

subarray_sum = prefix[4] - prefix[1] # 9, sum of nums[1:4]
```

This allows us to compute sum of subarrays in O(1) time. You can make prefixes for any operation that can be reversed (mulitplication with division, XOR with XOR, etc., not AND since AND is not reversible).

## Conclusion
This marks the (potential) end of CS 32. Thank you for reading these lessons and I hope this has at least provide some awareness of what is out there in terms of solving coding problems. Again, there is so many topics out there than what is covered in this class and in these lessons. In fact, there is so much we can do outside of what you will learn in CS 180 (upper division algorithms).

While individually, we may not be able to know everything there is to algorithms, the most important thing is to explore--apply what we know now and learn more about how we can creatively manipulate what we have to solve new problems. Always try to create new solutions and see where these solutions perform the best and worst at.

Once again, thank you for reading these lesson guides! Good luck with the rest of your algorithms journey!