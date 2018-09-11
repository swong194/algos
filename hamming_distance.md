# Question
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

Note:
0 ≤ x, y < 231.

Example:
```
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

# Thoughts

We can XOR between the two integers and then convert the resulting number to binary. Wherever there is a "1" we know that the corresponding bits were different, since XOR between a 0 and 1 results in a 1. We can iterate through the binary conversion and count how many 1's to get the number of positions the bits were different between x and y.

# Code 

```JS
const hammingDistance = (x, y) => {
  const bin = (x ^ y).toString(2);
  let count = 0;

  for (let i = 0; i < bin.length; i++) {
    if (bin[i] === '1') count++;
  }
  
  return count;
};
```