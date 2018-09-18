# Question
You created a game that is more popular than Angry Birds.

Each round, players receive a score between 0 and 100, which you use to rank them from highest to lowest. So far you're using an algorithm that sorts in O(nlgn) time, but players are complaining that their rankings aren't updated fast enough. You need a faster sorting algorithm.

Write a function that takes:

an array of unsortedScores
the highestPossibleScore in the game
and returns a sorted array of scores in less than O(nlgn) time.

For example:
```
var unsortedScores = [37, 89, 41, 65, 91, 53];
const HIGHEST_POSSIBLE_SCORE = 100;

sortScores(unsortedScores, HIGHEST_POSSIBLE_SCORE);
// returns [91, 89, 65, 53, 41, 37]
```
We’re defining nn as the number of unsortedScores because we’re expecting the number of players to keep climbing.

And, we'll treat highestPossibleScore as a constant instead of factoring it into our big O time and space costs because the highest possible score isn’t going to change. Even if we do redesign the game a little, the scores will stay around the same order of magnitude.

# Thoughts
We can create a bucket using an array, where the indices represent the number and the value at the index the amount of times a number occurs in unsorted array.

We can iterate through 

Time Complexity `O(n)`
- Where n is the length of the array
Space Complexity `O(n)`
- Where n is the length of the array

# Code
```JS
const topScore = (unsortedArr, highest) => {
  // initialize bucket
  const store = [];
  for (let i = 0; i < highest + 1; i++) {
    store.push(0);
  }

  // add counts to bucket
  unsortedArr.forEach(num => {
    if(store[num]) {
      store[num] += 1;
    } else {
      store[num] = 1;
    }
  });

  // fill sorted array
  const sorted = [];
  for (let i = store.length - 1; i >= 0; i--) {
    const count = store[i];
    if (count) {
      for (let j = 0; j < count; j++) {
        sorted.push(i);
      }
    }
  }

  return sorted;
};
```