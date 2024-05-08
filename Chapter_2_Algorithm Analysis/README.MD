# Chapter 2: Algorithm Analysis

## Assigment 1: Program Analysis
### 2-1
#### Question
What value is returned by the following function? Express your answer as a
function of n. Give the worst-case running time using the Big Oh notation.

```plaintext
function mystery(n)
    r := 0
    for i := 1 to n − 1 do
        for j := i + 1 to n do
            for k := 1 to j do
                r := r + 1
    return(r)
```

#### Solution
The returned value would be:

```plaintext
n * (n-1) * (n-1)
    = n * ( (n-1)^2 )
    = n * ( n^2 - 2n + 1)
    = n^3 - 2n^2 + n
```
The worst-case running time would be `O(n^3)`, a cubic time complexity.

### 2-2
#### Question
What value is returned by the following function? Express your answer as a
function of n. Give the worst-case running time using Big Oh notation.

```plaintext
function pesky(n)
    r := 0
    for i := 1 to n do
        for j := 1 to i do
            for k := j to i + j do
                r := r + 1
    return(r)
```

#### Solution
The returned value would be:
```plaintext
(n-1) * n * n
    =  n^3 - n^2
```

The worst-case running time would be `O(n^3)`, a cubic complexity.

### 2-3
#### Question
What value is returned by the following function? Express your answer as a function of n. Give the worst-case running time using Big Oh notation.

```plaintext
function prestiferous(n)
    r := 0
    for i := 1 to n do
        for j := 1 to i do
            for k := j to i + j do
                for l := 1 to i + j − k do
                    r := r + 1
    return(r)
```

#### Solution
The returned value would be:
```plaintext
(n-1) * n * 2n * (2n - n)
    =  (n^2 - n) * (2n * n)
    =  (n^2 - n) * (2n^2)
    =  2n^4 - 2n^3
```

The worst-case running time would be `O(n^4)`, an exponentially big time complexity.

### 2-4
#### Question
What value is returned by the following function? Express your answer as a function of n. Give the worst-case running time using Big Oh notation.

```plaintext
function conundrum(n)
    r := 0
    for i := 1 to n do
        for j := i + 1 to n do
            for k := i + j − 1 to n do
                r := r + 1
    return(r)

```

#### Solution
The returned value would be:
```plaintext
(n-1) * (n-2) * ( n - ( (n-1) + (n-2) ) - 1 ) )
    = (n-1) * (n-2) * ( n - n - 1 + n - 2 - 1 )
    = (n-1) * (n-2) * (n-4)
    = (n^2 - 2n -n + 2) * (n-4)
    = n^3 - 2n^2 -n^2 + 2n - 4n^2 + 8n  + 4n + 8
    = n^3 + 7n^2  + 14n + 8
```

The worst-case running time would be `O(n^3)`, a cubic time complexity.

## Assigment 2: Big Oh
### 2-8
#### Question
For each of the following pairs of functions, either f (n) is in O(g(n)), f (n) is
in Ω(g(n)), or f (n) = Θ(g(n)). Determine which relationship is correct and briefly
explain why.

- (a) f (n) = log n2; g(n) = log n + 5
- (b) f (n) = √n; g(n) = log n2
- (c) f (n) = log2 n; g(n) = log n
- (d) f (n) = n; g(n) = log2 n
- (e) f (n) = n log n + n; g(n) = log n
- (f) f (n) = 10; g(n) = log 10
- (g) f (n) = 2n; g(n) = 10n2
- (h) f (n) = 2n; g(n) = 3n

#### Solution
TBD

### 2-9
#### Question
For each of the following pairs of functions f (n) and g(n), determine whether
f (n) = O(g(n)), g(n) = O(f (n)), or both.
- (a) f (n) = (n2 − n)/2, g(n) = 6n
- (b) f (n) = n + 2√n, g(n) = n2
- (c) f (n) = n log n, g(n) = n√n/2
- (d) f (n) = n + log n, g(n) = √n
- (e) f (n) = 2(log n)2, g(n) = log n + 1
- (f) f (n) = 4n log n + n, g(n) = (n2 − n)/2

#### Solution
TBD

### 2-12
#### Question
For each of the following pairs of functions f (n) and g(n), give an appropriate
positive constant c such that f (n) ≤ c · g(n) for all n > 1.
- (a) f (n) = n2 + n + 1, g(n) = 2n3
- (b) f (n) = n√n + n2, g(n) = n2
- (c) f (n) = n2 − n + 1, g(n) = n2/2

#### Solution
TBD

## Assigment 3: Summation
### 2-37
#### Question
When you first learned to multiply numbers, you were told that x × y means
adding x a total of y times, so 5×4 = 5+5+5+5 = 20. What is the time complexity
of multiplying two n-digit numbers in base b (people work in base 10, of course,
while computers work in base 2) using the repeated addition method, as a function
of n and b. Assume that single-digit by single-digit addition or multiplication takes
O(1) time. (Hint: how big can y be as a function of n and b?)

#### Solution
TBD

## Assigment 4: Interview questions
### 2-49
#### Question
Suppose we start with n companies that eventually merge into one big company.
How many different ways are there for them to merge?

#### Solution
TBD

### 2-51
#### Question
Six pirates must divide $300 dollars among themselves. The division is to proceed
as follows. The senior pirate proposes a way to divide the money. Then the pirates
vote. If the senior pirate gets at least half the votes he wins, and that division
remains. If he doesn’t, he is killed and then the next senior-most pirate gets a
chance to do the division. Now you have to tell what will happen and why (i.e.
, how many pirates survive and how the division is done)? All the pirates are
intelligent and the first priority is to stay alive and the next priority is to get as
much money as possible.

#### Solution
TBD


### 2-52
#### Question
Reconsider the pirate problem above, where only one indivisible dollar is to be
divided. Who gets the dollar and how many are killed?

#### Solution
TBD

## Assigment 5: Programming challenge
### Leet code 2-1: Remove k-digits
#### Question
https://leetcode.com/problems/remove-k-digits/

#### Solution
TBD

### Leeet code 2-2: Counting bits
#### Question
https://leetcode.com/problems/counting-bits/

#### Solution
TBD

### Leet code 2-3: 4 sum
#### Question
https://leetcode.com/problems/4sum/

#### Solution
TBD

### HackerRank 2-1: Pangrams
#### Question
https://www.hackerrank.com/challenges/pangrams/

#### Solution
TBD

### HackerRank 2-2: Power sum
#### Question
https://www.hackerrank.com/challenges/the-power-sum/

#### Solution
TBD

### HackerRank 2-3: Magic square forming
#### Question
https://www.hackerrank.com/challenges/magic-square-forming/

#### Solution
TBD

