# Question
There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot ends up at (0, 0) after it completes its moves.

The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

Note: The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.

Example 1:
```
Input: "UD"
Output: true 
Explanation: The robot moves up once, and then down once. All moves have the same magnitude, so it ended up at the origin where it started. Therefore, we return true.
```
 

Example 2:
```
Input: "LL"
Output: false
Explanation: The robot moves left twice. It ends up two "moves" to the left of the origin. We return false because it is not at the origin at the end of its moves.
```


# Thoughts
Since the vertical directions are complimentary and the horizontal directions are complimentary. We can keep track of the number of times the robot moves in each direction specifically. If the robot moves up the same amount of times it moves down then it has made no movement in the vertical direction. If the robot moves the same amount of times left and right then it has made no movement in the horizontal direction. If Both conditions are true then the robot has returned to its origin.

Time Complexity `O(n)`

- Where n is the length of moves

Space Complexity `O(1)`

# Code
```JS
const atOrigin = moves => {
  let y = 0;
  let x = 0;

  for (let i = 0; i < moves.length; i++) {
    const move = moves[i];

    switch (move) {
      case 'U':
        y++;
        break;
      case 'D':
        y--;
        break;
      case 'R':
        x++;
        break;
      case 'L':
        x--;
        break;
    }
  }

  return !x && !y;
};
```