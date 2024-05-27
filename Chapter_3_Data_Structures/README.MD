# Chapter 3: Data structures

## Course material
- Lectures: [Elementary Data Structures](https://www.youtube.com/watch?v=vg2u8Hbb6lE&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=4), [ Dictionaries](https://www.youtube.com/watch?v=27jDhSEJ1ag&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=5), [ Hashing](https://www.youtube.com/watch?v=cGv8J2DBFPk&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=6)
- Reading: Chapter 3 (Data Structures) from "The Algorithm Design Manual"

## Assignment 1: Stacks, Queues, and Lists
### 3-1
#### Question
A common problem for compilers and text editors is determining whether the parentheses in a string are balanced and properly nested. For example, the string ((())())() contains properly nested pairs of parentheses, while the strings )()( and ()) do not. Give an algorithm that returns true if a string contains properly nested and balanced parentheses, and false if otherwise. For full credit, identify the position of the first offending parenthesis if the string is not properly nested and balanced.

#### Solution
TBD

### 3-2
#### Question
Give an algorithm that takes a string S consisting of opening and closing parentheses, say )()(())()()))())))(, and finds the length of the longest balanced parentheses in S, which is 12 in the example above. (Hint: The solution is not necessarily a contiguous run of parenthesis from S.)
#### Solution
TBD

### 3-3
#### Question
Give an algorithm to reverse the direction of a given singly linked list. In other words, after the reversal all pointers should now point backwards. Your algorithm should take linear time.
#### Solution
TBD

### 3-4
#### Question
Design a stack S that supports S.push(x), S.pop(), and S.findmin(), which returns the minimum element of S. All operations should run in constant time.

#### Solution
TBD

### 3-5
#### Question
Tic-tac-toe is a game played on an n × n board (typically n = 3) where two players take consecutive turns placing “O” and “X” marks onto the board cells. The game is won if n consecutive “O” or ‘X” marks are placed in a row, column, or diagonal. Create a data structure with O(n) space that accepts a sequence of moves, and reports in constant time whether the last move won the game.

#### Solution
TBD


## Assignment 2: Applications of Tree Structures
### 3-11
#### Question
Design a dictionary data structure in which search, insertion, and deletion can all be processed in O(1) time in the worst case. You may assume the set elements are integers drawn from a finite set 1, 2, .., n, and initialization can take O(n) time.

#### Solution
TBD

### 3-12
#### Question
The maximum depth of a binary tree is the number of nodes on the path from the root down to the most distant leaf node. Give an O(n) algorithm to find the maximum depth of a binary tree with n nodes.

#### Solution
TBD

### 3-17
#### Question
Give an O(n) algorithm that determines whether a given n-node binary tree is height-balanced (see Problem 3-15).

#### Solution
TBD

### 3-22
#### Question
Design a data structure that supports the following two operations:• insert(x) – Insert item x from the data stream to the data structure. • median() – Return the median of all elements so far. All operations must take O(log n) time on an n-element set.

#### Solution
TBD

## Assignment 5: LeetCode
### 3-1: Valid binary search tree
#### Question
https://leetcode.com/problems/validate-binary-search-tree/

#### Solution
Thought process: Check recursively whether any node violates max and min of its parent, and return false; otherwise, keep checking the left and right subtrees.

```javascript
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
const isValidBST = function(root) {
    validate(root, null, null)
    return true;
};

/**
 * @param {TreeNode} root
 * @param {Number} min
 * @param {Number} max
 * @return {boolean}
 */
const validate = function (root, min, max){
    // if we've made it to the bottom of the tree, that's cool
    if(!root){
        return true
    }else if(max != null && root.val >= max || min != null && root.val <= min){
        return false
    } else {
        // So far, so good, continue the recursion on left and right
        return validate(root.left, min, root.val) && validate(root.right, root.val, max)
    }
}


```

### 3-2: Count of smaller numbers after self
#### Question
https://leetcode.com/problems/count-of-smaller-numbers-after-self/

#### Solution
TBD

### 3-3: Construct Binary Tree from Preorder and Inorder Traversal
#### Question
https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/

#### Solution
TBD

## Assignment 6: HackerRank
### 3-1: Is This a Binary Search Tree?
#### Question
https://www.hackerrank.com/challenges/is-binary-search-tree/
### Solution
TBD

### 3-2: Queue using two stacks
#### Question
https://www.hackerrank.com/challenges/queue-using-two-stacks/

### Solution
TBD

### 3-3: Cycle detection
#### Question
https://www.hackerrank.com/challenges/detect-whether-a-linked-list-contains-
a-cycle/problem

### Solution
TBD


### Extra: Tree practice
#### Maximum depth of binary tree
https://leetcode.com/problems/maximum-depth-of-binary-tree/submissions/

### Solution
**Recursive solution**: Use recursion to increment the count of levels. The idea is that if there's no child node, the level is 0. Otherwise, we'd increment the level by 1.

```javascript
const maxDepth(root){
    if(!root){
        return 0
    }

    return 1 + Math.max(
        maxDepth(root.left),
        maxDepth(root.right)
    )
}
```

**Iterative approach using BFS**: Here traverse the tree and for each node, I store the current node in a variable, delete it from the queue and add the left and right nodes using a loof of length 2 at most. All that's left to do is increment the level at every iteration of the outer loop (tree traversal).


```javascript
const maxDepth = function (root){
    if(!root){
        return 0
    }

    let level = 0
    let stack = [root]
    
    
    while(stack.length > 0){
        
        for(let i = 0; i < stack.length; i++){
            let node = stack.shift()
            if(node.left != null){
                stack.push(node.left)
            }

            if(node.right != null){
                stack.push(node.right)
            }
        }
        
        level++

    }
    
    return level
}
```

**Iterative approach using DFS**: Here we use a 2D stack that associates the node with the current depth. At every iteration, you get rid of the previous node and try to add one or two child nodes. You update the overall depth variable by taking the max value of node right or left.

```javascript
const maxDepth = function (root){
    if(!root){
        return 0
    }

    let level = 1
    let stack = [[root, level]]

while (stack.length > 0){
        let node, depth;
        [node, depth] = stack.pop()

        if(node != null){
            level =  Math.max(depth, level)
            stack.push([node.left, depth + 1])
            stack.push([node.right, depth + 1])
        }
    }

    return level
}
```
