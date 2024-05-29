# Chapter 3: Data structures

## Course material
- Lectures: [Elementary Data Structures](https://www.youtube.com/watch?v=vg2u8Hbb6lE&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=4), [ Dictionaries](https://www.youtube.com/watch?v=27jDhSEJ1ag&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=5), [ Hashing](https://www.youtube.com/watch?v=cGv8J2DBFPk&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=6)
- Reading: Chapter 3 (Data Structures) from "The Algorithm Design Manual"

## Assignment 1: Stacks, Queues, and Lists
### 3-1
#### Question
A common problem for compilers and text editors is determining whether the parentheses in a string are balanced and properly nested. For example, the string ((())())() contains properly nested pairs of parentheses, while the strings )()( and ()) do not. Give an algorithm that returns true if a string contains properly nested and balanced parentheses, and false if otherwise. For full credit, identify the position of the first offending parenthesis if the string is not properly nested and balanced.

#### Solution
**Thought process**: Build a map of closing parenthesis, use a stack to add opening parenthesis and pop the latest opening parenthesis. The approach is generic to brackets and accolades.

```javascript
var isValid = function(s) {
    let stack = []
    let pairs = {
       ')':'(',
       '}': '{',
       ']':'['
    }

    for (let char of s){
      // push opening char to stack
      if(['(', '[', '{'].includes(char)){
        stack.push(char)
      }else{
        let openingChar = stack.pop()
        if(openingChar !== pairs[char]){
          return false
        }
      }
    }

    return stack.length < 1
};
```

### 3-3
#### Question
Give an algorithm to reverse the direction of a given singly linked list. In other words, after the reversal all pointers should now point backwards. Your algorithm should take linear time.

#### Solution
**Thought process**: Use pointers, keep track of head, tail. Detach and attach nodes so as head becomes tails

```javascript
var reverseLinkedList = function(head) {
    let tail = null
    let headNode = head


    while (headNode != null){
        // prepare prevNode, if there is any
        let nextHeadNode = headNode.next

        // re-configure headNode connection
        headNode.next = tail

        // set head as tail
        tail = headNode

        // move to next headNode
        headNode = nextHeadNode

    }

    return tail
};
```

### 3-5
#### Question
Tic-tac-toe is a game played on an n × n board (typically n = 3) where two players take consecutive turns placing “O” and “X” marks onto the board cells. The game is won if n consecutive “O” or ‘X” marks are placed in a row, column, or diagonal. Create a data structure with O(n) space that accepts a sequence of moves, and reports in constant time whether the last move won the game.

#### Solution
TBD


## Assignment 2: Applications of Tree Structures
### 3-12
#### Question
The maximum depth of a binary tree is the number of nodes on the path from the root down to the most distant leaf node. Give an O(n) algorithm to find the maximum depth of a binary tree with n nodes.

#### Solution
**Thought process**: 3 possible ways, recursion, BFS or DFS. Increment the level variable and keep track of it using a 1D stack and inner loop of length 2 or use a 2D stack (BFS).

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

### 3-17
#### Question
Give an O(n) algorithm that determines whether a given n-node binary tree is height-balanced (see Problem 3-15).

#### Solution
**Though process**: Use a helper function to calculate the depth of each subtree while checking if the difference in depths exceeds 1, setting a flag `isBal` to false if it does. Return the isBal flag after completing the depth calculation for the entire tree.

```javascript
var isBalanced = function(root) {
    let isBal = true
    function depth(root){
        if(!root){
            return 0
        }

        let leftDepth = depth(root.left)
        let rightDepth = depth(root.right)

        if (Math.abs( leftDepth - rightDepth )  > 1) {
            isBal = false
        }

        return Math.max(leftDepth, rightDepth) + 1 
    }
    depth(root)
    return isBal
};
```

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
**Thought process**: I map indices of values in the inorder array, then recursively build the tree using the preorder and inorder arrays, returning the root node. `preIndex` keeps track of the current root node in the preorder traversal, and the helper function recursively constructs the left and right subtrees by adjusting the indices appropriately.

```javascript
/**
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
var buildTree = function(preorder, inorder) {
    // build index of inorder indices
    let inMap = {}

    // track index of root in preorder tree
    let preIndex = 0
    inorder.forEach((value, index) => { inMap[value] = index})

    function build(inStart, inEnd){

        // base case of recursion
        if( inStart > inEnd) {
            return null
        }

        // get rootVal using its index in preorder
        let rootVal = preorder[preIndex]

        // increments preOrder index for next recursive call
        preIndex++

        let inIndex = inMap[rootVal]

        // build node, add child leaves using recursion
        let root = new TreeNode(rootVal)
        root.left = build(inStart, inIndex -1)
        root.right = build(inIndex +1, inEnd)

        return root
    }


    return build(0, inorder.length -1)
};
```

## Assignment 6: HackerRank
### 3-1: Is This a Binary Search Tree?
#### Question
https://www.hackerrank.com/challenges/is-binary-search-tree/
### Solution
**Thought Process**: Check recursively whether any node violates max and min of its parent, and return false; otherwise, keep checking the left and right subtrees.
```javascript
function processData(input) {
    return validate(input, null, null)
}

var validate = function (root, min, max){
    if(!root){
        return true
    }
    if( (min !=null && root.data <= min)
       || (max != null && root.data >= max)) {
        return false
    }
    return validate(root.left, min, root.data) && validate(root.right, root.data, max)
}
```

### 3-2: Queue using two stacks
#### Question
https://www.hackerrank.com/challenges/queue-using-two-stacks/

### Solution
TBD

### 3-3: Cycle detection
#### Question
https://www.hackerrank.com/challenges/detect-whether-a-linked-list-contains-a-cycle/problem

### Solution
**Thought process**: Use a set and track nodes that were already encountered. If we ever come across something we've seen before return `true`.

```javascript
/**
 * @param {ListNode} head
 * @return {boolean}
 */
const hasCycle = function(head) {

    // track duplicates with a set
    let set = new Set()
    let currNode = head

    // traverse the linkedlist in search of a duplicate
    while(currNode != null){
        // add whole node to the set
        if(set.has(currNode)){
            return true
        }else{
           set.add(currNode)
            // move on to next Node
        }
        currNode = currNode.next

    }
    // no duplicates were found
    return false
};
```
