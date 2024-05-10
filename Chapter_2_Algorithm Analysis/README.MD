# Chapter 2: Algorithm Analysis

## Assignment 1: Program Analysis
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
(n-1) * (n-2) * ( n - ( (n-1) + (n-2) ) - 1 )
    = (n-1) * (n-2) * ( n - n - 1 + n - 2 - 1 )
    = (n-1) * (n-2) * (n-4)
    = (n^2 - 2n -n + 2) * (n-4)
    = n^3 - 2n^2 -n^2 + 2n - 4n^2 + 8n  + 4n + 8
    = n^3 + 7n^2  + 14n + 8
```

The worst-case running time would be `O(n^3)`, a cubic time complexity.

## Assignment 2: Big Oh
### 2-8
#### Question
(a) Is 2^(n+1) = O(2^n)?
(b) Is 2^(2n) = O(2^n)?

#### Solution
a - No, it's just O(n)
b - No, it's just O(n)

### 2-9
#### Question
For each of the following pairs of functions, f (n) is in O(g(n)), Ω(g(n)), or Θ(g(n)). Determine which relationships are correct and briefly explain why.

- (a) f (n) = log n2; g(n) = log n + 5
- (b) f (n) = √n; g(n) = log n2
- (c) f (n) = log2 n; g(n) = log n
- (d) f (n) = n; g(n) = log2 n
- (e) f (n) = n log n + n; g(n) = log n
- (f) f (n) = 10; g(n) = log 10
- (g) f (n) = 2n; g(n) = 10n2
- (h) f (n) = 2n; g(n) = 3^n

#### Solution
- (a) f(n) is only in Θ(logn) as the worst case scenario and the best can both be expressed as 
- (b) f(n) is in Ω(n) and O(logn) but not in Θ(g(n)) since their growth rates are different.
- (c) f(n) is in Ω(logn) and O(logn) but not in Θ(g(n)) since their growth rates are different.
- (d) f(n) is in Ω(n) and O(n) but not in Θ(g(n)) because their growth rates are different.
- (e) f(n) is in Ω(nlogn) and O(nlog⁡n) but not in Θ(g(n)) because their growth rates are different.
- (f) f(n) is in Ω(1), O(1), and Θ(1) because it's a constant function.
- (g) f(n) is in Ω(2n) and O(2n) but not in Θ(g(n)) because their growth rates are different.
- (h) f(n) is in Ω(2n) and O(3n) but not in Θ(g(n)) because their growth rates are different.

### 2-12
#### Question
Prove that n^3 − 3n^2 − n + 1 = Θ(n^3).

#### Solution
- The worst case (upper bound) scenario is that the function takes n^3 time to complete, which partially satisifies `Θ(n^3)`.
- For the lower bound, we need to find a constant C > 0 that's large enough and and help prove that `(n^3 − 3n^2 − n + 1) >= C*n^3`. [TBD]

## Assignment 3: Summation
### 2-37
#### Question
Find an expression for the sum of the ith row of the following triangle, and prove its correctness. Each entry is the sum of the three entries directly above it. All non-existing entries are considered 0.

```
                1
            1   1   1
        1   2   3   2   1
    1   3   6   7   6   3   1
1   4   10  16  19  16  10  4   1
```

#### Solution
```plaintext
let the triangle be S
the sum of Sith row = 1 + sum(S[i-1]) row if i > 0
```

## Assignment 4: Interview questions
### 2-49
#### Question
Suppose we start with n companies that eventually merge into one big company. How many different ways are there for them to merge?

#### Solution
If ultimately the have to merge into one big company, there is only one way for that to happen.


### 2-51
#### Question
Six pirates must divide $300 dollars among themselves. The division is to proceed as follows. The senior pirate proposes a way to divide the money. Then the pirates vote. If the senior pirate gets at least half the votes he wins, and that division remains. If he doesn’t, he is killed and then the next senior-most pirate gets a chance to do the division. Now you have to tell what will happen and why (i.e., how many pirates survive and how the division is done)? All the pirates are intelligent and the first priority is to stay alive and the next priority is to get as much money as possible.

#### Solution
```plaintext
The likelihood of not getting enough vote and being killed is high because other pirates have an incentive to have less crew members alive as it means a larger share of the $300. All pirates will survive and share the money in equal parts: 300/6 = $50.
```


### 2-52
#### Question
Reconsider the pirate problem above, where only one indivisible dollar is to be divided. Who gets the dollar and how many are killed?

#### Solution
Since their priority is to stay alive, only 1 person will get the dollar and no crew member will be killed.

## Assignment 5: Programming challenge
### Leet code 2-1: Remove k-digits
#### Question
https://leetcode.com/problems/remove-k-digits/

#### Solution
```javascript
/**
 * @param {string} num
 * @param {number} k
 * @return {string}
 */
const removeKdigits = (num, k) => {
    const stack = []

    for(let digit of num){

        // At every iteration, re-arrange stack if `digit` < stack's head
        while( k> 0 && stack.length && digit < stack[stack.length -1] ){
            stack.pop()
            k--;
        }

        stack.push(digit)
    }

    // Deal with digits that the k limit did not allow to remove
    while( k> 0){
        stack.pop()
        k--;
    }

    result = stack.join('')

    // Turn stack into string and deal with leading zeros
    result = result.replace(/^0+/, '')

    return result === '' ? '0' : result
};
```

### Leeet code 2-2: Counting bits
#### Question
https://leetcode.com/problems/counting-bits/

#### Solution
```javascript
/**
 * @param {number} n
 * @return {number[]}
 */
const countBits = (n) => {
    let ans = []

    for(let i = 0; i <= n; i++){
        let remainder = i;
        let counter = 0;

        while (remainder != 0) {

            // Increment counter when remainder = 1
            counter += remainder % 2;

            // Get the remainder by flooring the division
            remainder = Math.floor(remainder / 2);
        }

        ans[i] = counter

    }

    return ans;
};
```

### Leet code 2-3: 4 sum
#### Question
https://leetcode.com/problems/4sum/

#### Solution
TBD

### HackerRank 2-1: Pangrams
#### Question
https://www.hackerrank.com/challenges/pangrams/

#### Solution
```javascript
function pangrams(s) {
    let counter = {}

    // Get rid of all spaces
    s = s.toLowerCase().replaceAll(' ', '');

    for(let char of s){
        let key = char
        if(key.length > 0){
            counter[key] = key;
        }
    }

    return Object.keys(counter).length == 26 ? 'pangram': 'not pangram'
}
```

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

