# Question

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

Example 1:
```
Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
```
Example 2:
```
Input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
Output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Explanation: First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
```
Notes:

1 <= A.length = A[0].length <= 20
0 <= A[i][j] <= 1

# Thoughts
We can use the JS .reverse method on each subarray and then go through each subarray and invert each number. However we can do better and do both at the same time.

For each subarray we can reverse it and invert under one custom operation. This would result in a linear time complexity as we are not changing array size, only the value at each index.

# Code

```JS
const helperFlipAndInvert = arr => {
  let s = 0;
  let e = arr.length - 1;

  while (s < e) {
    const newStart = arr[e] === 1 ? 0 : 1;
    const newEnd = arr[s] === 1 ? 0 : 1;

    arr[s] = newStart;
    arr[e] = newEnd;

    s++;
    e--;
  }

  if (arr.length % 2 !== 0) {

  }
};

const flipAndInvertImage = arr => {
  arr.forEach(subArr => helperFlipAndInvert(subArr));

  return arr;
};
```