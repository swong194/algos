# Question

International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.

For convenience, the full table for the 26 letters of the English alphabet is given below:

[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cab" can be written as "-.-.-....-", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.

Return the number of different transformations among all words we have.

Example:

```
Input: words = ["gin", "zen", "gig", "msg"]
Output: 2
Explanation: 
The transformation of each word is:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."
```

There are 2 different transformations, "--...-." and "--...--.".
 

Note:

The length of words will be at most 100.
Each words[i] will have length in range [1, 12].
words[i] will only consist of lowercase letters.

# Thoughts
Using a set here will be useful in seeing how many unique transformations we have. After we convert all the words into their morse code counterparts, we can just return the size of the set for the unique transformations. We can extract the conversion of a word to morse code as a helper function.

# Code

```JS
const morseCollection = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."];

const encodeToMorse = word => {
  let morse = '';

  for (let i = 0; i < word.length; i++) {
      const index = word.charCodeAt(i) - 97;
      morse += morseCollection[index];
  }

  return morse;
};

const countMorse = words => {
  const store = new Set();

  for (let i = 0; i < words.length; i++) {
    store.add(encodeToMorse(words[i]));
  }

  return store;
};
```