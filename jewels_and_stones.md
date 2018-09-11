# Question

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:

```
Input: J = "aA", S = "aAAbbbb"
Output: 3
```

Example 2:

```
Input: J = "z", S = "ZZ"
Output: 0
```
Note:

S and J will consist of letters and have length at most 50.
The characters in J are distinct.

# Thoughts
We keep a count variable which we increment. We iterate through String "S" and check if the letter is inside string "J", if it is we increase count. Return count at the end of the iteration.

A optimization could be iterating through J first and storing the letters in a set. Then we can iterate through S and check if it exists in the set.

However, using indexOf seems to be more efficient then creating a set. This is most likely due to its implementation under the hood.


# Code

```JS
  const countJewel = (J, S) => {
    let count = 0;

    for (let i = 0; i < S.length; i++) {
      if (J.indexOf(S[i]) > -1) count += 1;
    }

    return count;
  };
```
