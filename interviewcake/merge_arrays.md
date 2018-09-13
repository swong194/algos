# Question

In order to win the prize for most cookies sold, my friend Alice and I are going to merge our Girl Scout Cookies orders and enter as one unit.

Each order is represented by an "order id" (an integer).

We have our lists of orders sorted numerically already, in arrays. Write a function to merge our arrays of orders into one sorted array.

For example:

```
var myArray     = [3, 4, 6, 10, 11, 15];
var alicesArray = [1, 5, 8, 12, 14, 19];

console.log(mergeArrays(myArray, alicesArray));
// logs [1, 3, 4, 5, 6, 8, 10, 11, 12, 14, 15, 19]
```

# Thoughts

We can keep track of two pointers, one per array. We can then build a merged array by comparing the values at each pointer. We would push the lower value first, and shift it off the original array. At the end we can concat the answer array with the remaining values of both arrays.

Time Complexity `O(m + n)`

- Where m, n are the length of the two arrays respectively
  Space Complexity `O(m + n)`
- Where m, n are the length of the two arrays respectively

# Code

```JS
const mergeArrays = (a1, a2) => {
  const merged = [];

  while (a1.length || a2.length) {
    if (a1[0] <= a2[0]) {
      merged.push(a1[0]);
      a1.shift();
    } else {
      merged.push(a2[0]);
      a2.shift();
    }
  }

  return [...merged, ...a1, ...a2];
};
```
