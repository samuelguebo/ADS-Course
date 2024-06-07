# Chapter 4: Sorting Algorithms

## Course material
- Lectures: [Heapsort](https://www.youtube.com/watch?v=VTxEAMHtZsc&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=7), [ Merge sort + Quick Sort](https://www.youtube.com/watch?v=jUf-UQ3a0kg&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=8), [ Linear sorting](https://www.youtube.com/watch?v=0ksyQKmre84&list=PLOtl7M3yp-DX6ic0HGT0PUX_wiNmkWkXx&index=9)
- Reading: Chapter 4 (Sorting) from "The Algorithm Design Manual"

## Assignment 1: Sorting
### 1-1
#### Question
We are given a set of S containing n real numbers and a real number x, and seek efficient algorithms to determine whether two elements of S exist whose sum is exactly x. (a) Assume that S is unsorted. Give an O(n log n) algorithm for the problem. (b) Assume that S is sorted. Give an O(n) algorithm for the problem.
#### Solution
**Thought process**: Use the two-sum II approach but sort S first. The sorting will be O(nlogn) and use the two-pointer search in a sorted array would be O(n) in worst case scenario. In case the array is already sorted, just run the two-pointer search.

```javascript
function findPairInUnsortedArray(s, target){
    // sort s
    s = s.sort((a, b) => a-b)

    // search with two pointers
    l = 0
    r = s.length -1
    while( l < r){
        let sum = s[l] + s[r]
        if(sum === target){
            return [l,r]
        }else if(sum < target){
            l++
        }else{
            r--
        }
    }
}

```

### 1-2
#### Question
Devise an algorithm for finding the k smallest elements of an unsorted set of n integers in O(n + k log n).

#### Solution
**Thought process**: Let's sort the array in ascending order and iterate k times to add the elements found in a subset array, then return the subset array. 

```javascript
// TBD
```

### 1-3
#### Question
Give an efficient algorithm to rearrange an array of n keys so that all the negative keys precede all the non-negative keys. Your algorithm must be in-place, meaning you cannot allocate another array to temporarily hold the items. How fast is your algorithm? 

#### Solution
**Thought process**: TBD
```javascript
// TBD
```

## Assignment 2: LeetCode
### 4-1: Sort list
#### Question
https://leetcode.com/problems/sort-list/

#### Solution
**Thought process**: TBD

```javascript
// TBD
```

### 4-2: Queue reconstruction
#### Question
https://leetcode.com/problems/queue-reconstruction-by-height/ 

#### Solution
**Thought process**: TBD

```javascript
// TBD
```

### 4-3: Merged k-sorted list
#### Question
https://leetcode.com/problems/merge-k-sorted-lists/ 

#### Solution
**Thought process**: TBD

```javascript
// TBD
```
### 4-4: Find k-pair with smallest sums
#### Question
https://leetcode.com/problems/find-k-pairs-with-smallest-sums/ 

#### Solution
**Thought process**: TBD

```javascript
// TBD
```

## Assignment 3: HackerRank
### 4-1: Quicksort 3
#### Question
https://www.hackerrank.com/challenges/quicksort3/ 

#### Solution
**Thought process**: TBD

```javascript
// TBD
```

### 4-2: Mark and Toys
#### Question
https://www.hackerrank.com/challenges/mark-and-toys/

#### Solution
**Thought process**: TBD

```javascript
// TBD
```

### 4-3: Container of balls
#### Question
https://www.hackerrank.com/challenges/organizing-containers-of-balls/ 

#### Solution
**Thought process**: TBD

```javascript
// TBD
```
