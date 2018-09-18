# Question
Write an efficient function that checks whether any permutation of an input string is a palindrome.

You can assume the input string only contains lowercase letters.

Examples:
```
"civic" should return true
"ivicc" should return true
"civil" should return false
"livci" should return false
"But 'ivicc' isn't a palindrome!"
```

If you had this thought, read the question again carefully. We're asking if any permutation of the string is a palindrome. Spend some extra time ensuring you fully understand the question before starting. Jumping in with a flawed understanding of the problem doesn't look good in an interview.

# Thoughts
We know a string can be formed into a palindrome as long as each letter is paired off. We allow for a maximum of one string that is unpaired (an odd length string palindrome). 

We can use a set to add and remove letters, if the set size is greater than 1 when we finish iterating through the string, we know it cannot be a palindrome in any arrangment.

Time Complexity `O(n)`
- Where n is the length of the string
Space Complexity `O(n)`
- Where n is the length of the string

# Code
```JS
const permutationPalindrome = string => {
  const store = new Set();

  for (let i = 0; i < string.length; i++) {
    const letter = string[i];

    if (store.has(letter)) {
      store.delete(letter)
    } else {
      store.add(letter)
    }
  }

  return store.size <= 1;
}
```