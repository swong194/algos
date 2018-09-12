# Question

Given a matrix A, return the transpose of A.

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

Example 1:

```
Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: [[1,4,7],[2,5,8],[3,6,9]]
```

Example 2:

```
Input: [[1,2,3],[4,5,6]]
Output: [[1,4],[2,5],[3,6]]
```

Note:

1 <= A.length <= 1000
1 <= A[0].length <= 1000

# Thoughts

We can iterate through the values of the array and create a transposed matrix by swapping indices.

Time Complexity `O(n)`

- Where n is the number of elements in the matrix

Space Complexity `O(n)`

- Where n is the number of elements in the matrix

# Code

```JS
const transposeMatrix = matrix => {
  const transpose = [];

  for (let i = 0; i < matrix[0].length; i++) {
    const hold = [];
    for (let j = 0; j < matrix.length; j++) {
      hold.push(matrix[j][i]);
    }
    transpose.push(hold);
  }

  return transpose
};
```
