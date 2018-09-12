# Question

A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

Example 1:

```
Input:
left = 1, right = 22
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```

Note:

The boundaries of each input argument are 1 <= left <= right <= 10000.

# Thoughts

We can iterate through all the numbers and use a helper to see if the number is self-dividing. The helper function would do this recursively by seeing if the number divides by its modulo by 10. We then push all the numbers that pass into an answer array.

The time analysis is interesting. Let's take the number 2222, in the worse case we need to go through each number and check if its divisible. This gives a log(n) run time for a number. The bottle neck would be that amount of times we have to do this operation, which is a linear time complexity.

Time Complexity `O(n)`

- where n is the range of numbers needing to be checked

# Code

```JS
const isSelfDividing = (divisor, num) => {
  if (divisor < 10) {
    return num % divisor === 0 ? true : false
  }

  return (num % (divisor % 10)) === 0 && isSelfDividing(Math.floor(divisor / 10), num);
}

const selfDividingNums = (l, r) => {
  const nums = [];
  for (let i = l; i <= r; i++) {
    if (isSelfDividing(i, i)) nums.push(i);
  }
  return nums;
}
```
