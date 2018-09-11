# Question

Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

Example 1:

```
Input:
	Tree 1                     Tree 2
          1                         2
         / \                       / \
        3   2                     1   3
       /                           \   \
      5                             4   7
Output:
Merged tree:
	     3
	    / \
	   4   5
	  / \   \
	 5   4   7
```

Note: The merging process must start from the root nodes of both trees.

# Thoughts

We can traverse a tree recursively or iteratively. Since it does not make a difference how we traverse the tree for this problem, I will go with the recursive solution.

Let us first assume we are comparing the correct nodes from each tree. Then if both nodes have a value we must add them and continue the recursive call. If one of them is null then we just return the branch that has values.

Time Complexity `O(n + m)`

- where n is the number of nodes of tree1 and m is the number of nodes in tree2. In the worse case we need to merge each node of both trees, we would touch every node from both trees.

Space Complexity `O(min(n, m))`

- where n is the number of levels in tree1 and m is the number of levels in tree2. The space we need gets generated from each recursive call. Therefore the maximum amount of stacks we need is generated from how many times we need to call mergeTrees, which is the minumum level of nodes between the two trees.

# Code

```JS
const mergeTrees = (t1, t2) => {
  if(!t1) return t2;
  if(!t2) return t1;

  t1.val += t2.val;
  // continue merging
  t1.left = mergeTrees(t1.left, t2.left);
  t1.right = mergeTrees(t1.right, t2.right);

  return t1;
};
```
