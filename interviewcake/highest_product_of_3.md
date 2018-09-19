# Question

Given an array of integers, find the highest product you can get from three of the integers.

The input arrayOfInts will always have at least three integers.

# Thoughts

# Code

```JS
const maxProdOfThree = arr => {
  let high = Math.max(arr[0], arr[1]);
  let low = Math.min(arr[0], arr[1]);
  let highProd = low * high;
  let lowProd = low * high;
  let maxProd = low * high * arr[2];

  for (let i = 2; i < arr.length; i++) {
    const newNum = arr[i];

    // set new maximum product
    maxProd = Math.max(maxProd, newNum * highProd, newNum * lowProd);

    // set new highest prod of two nums, and lowest prod of two nums
    highProd = Math.max(highProd, newNum * high, newNum * low);
    lowProd = Math.min(lowProd, newNum * high, newNum * low);

    // set new high num and new low num
    high = Math.max(high, newNum);
    low = Math.min(low, newNum);
  }
};
```
