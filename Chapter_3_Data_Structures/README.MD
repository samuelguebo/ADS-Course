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
TBD

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
Recursive solution

```javascript
const maxDepth(root){
    if(!root){
        return 0
    }

    return Math.max(
        maxDepth(root.left),
        maxDepth(root.right)
    )
}
```

Iterative approach using DFS

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