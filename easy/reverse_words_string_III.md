# Question

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

Example 1:

```
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"
```

Note: In the string, each word is separated by single space and there will not be any extra space in the string.

# Thoughts

We can create a helper function that takes in a string and a start and end indices. We can swap the values of the string within that range.

However in JS strings are immutable, so we need to convert the input string into an array first.

Time Complexity `O(n)`

- Where n is the length of the string

Space Complexity `O(1)`

- We are making the changes in place

# Code

```JS
const reverseRange = (string, s, e) => {
  while(s < e) {
    const hold = string[s];
    string[s] = string[e];
    string[e] = hold;

    s++;
    e--;
  }
};

const reverseString = string => {
  string = string.split('');
  let currentStart = 0;

  for (let i = 0; i <= string.length; i++) {
    if (string[i] === ' ' || i === string.length) {
      reverseRange(string, currentStart, i - 1);
      i++;
      currentStart = i;
    }
  }

  return string.join('');
};
```
