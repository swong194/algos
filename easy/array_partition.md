# Question

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Example 1:

```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```

Note:
n is a positive integer, which is in the range of [1, 10000].
All the integers in the array will be in the range of [-10000, 10000].

# Thoughts

If we minimize each pair than the most effective sum we can obtain is the sum of every other number in the array after it is sorted.

Time Complexity `O(nlog(n))`

- where n is the length of the array

# Code

```JS
const arrayPairSum = nums => {
  nums = nums.sort((a, b) => a - b);
  let sum = 0;

  for (let i = 0; i < nums.length; i+=2) {
    sum += nums[i];
  }

  return sum;
};
```