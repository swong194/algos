# Question
You have an array of integers, and for each index you want to find the product of every integer except the integer at that index.

Write a function getProductsOfAllIntsExceptAtIndex() that takes an array of integers and returns an array of the products.

For example, given:

  [1, 7, 3, 4]

your function would return:

  [84, 12, 28, 21]

by calculating:

  [7 * 3 * 4,  1 * 3 * 4,  1 * 7 * 4,  1 * 7 * 3]

Here's the catch: You can't use division in your solution!

# Thoughts
We can initialize an array with the same size as the input and fill it with 1. We can then iterate through the input array and multiply each bucket with a number besides the index we are on.

Time Complexity `O(n)`
- Where n is the length of the input array
Space Complexity `O(n)`
- Where n is the length of the input array.

# Code
```JS
const productOfOthers = arr => {
  if (arr.length < 2) throw 'error';
  
  const result = new Array(arr.length).fill(1);

  for (let i = 0; i < arr.length; i++) {
    const num = arr[i];

    for (let j = 0; j < result.length; j++) {
      if (i === j) {
        continue;
      } else {
        result[j] *= num;
      }
    }
  }

  return result;
};
```