# Chapter 1: Introduction

## Assignment 1: Estimation
### 1-21
#### Question
Do all the books you own total at least one million pages? How many total pages are stored in your school library?

#### Solution
I start by estimating the number of books that I own and set a max number: 250.
My next assumption is to estimate the average page number: 350; and round it up to get a max 500.
Then I'll multiply those two and compare with 1*10^6.
( 250 * 500 = 125,000 ) < 10^6.

So the answer is NO.

### 1-22
#### Question
How many words are there in this textbook?

#### Solution
I know that there are usually around 250 to 400 words per page. I'll take 300 as the average.
Since the textbook is around 600 pages (from memory) I'll multiply 300 * 600 = 18,000.

Limitations: the textbook often times has larger line-spacing due to code formatting and also no words at all when there are illustrations.  

### 1-23
#### Question
How many hours are one million seconds? How many days? Answer these questions by doing all the arithmetic in your head.

#### Solution
I know by hear that there are 3600 seconds in an hour.
So I'll estimate that there are around than 2.5 hours in 10,000 seconds. 
Then, I'll multiply 2,5 by 100 and get 250 hours in 1,000,000 seconds.
I'll note that 250 hours are greater than 10 days.
Overall, I'll estimate that one million seconds are around 250 hours or 10 days.
Limitations: the 2,5 hours to 10,000 seconds ratio might be a wrong guess.

### 1-24
#### Question
Estimate how many cities and towns there are in the United States.

#### Solution
In the most southern part of my country, which is around 20% of the territory, I think there are around 25 cities.
So I'll estimate that there are around (15 * 5) = 75 cities in my country.
Since the US has 54 states, I'll assume that there are 75 * (54 but round up that number to 50 for easier mental calculation).
So 75 * 50 = 350 cities approximately. For towns, I'll estimate that each city has 10 towns based on what I know of my own city.
Overall, that would give me 350 cities and 3500 towns in the US.

Limitations: the US has density quite different from my country and the assumation 1 state area = my country area is not correct since states have various areas. 

## Assignment 2: Interview problems

### 1-32
#### Question
Write a function to perform integer division without using either the / or * operators. Find a fast way to do it.

#### Solution
```javascript
function divideWithoutDefaultOperators (dividend, divisor) {
    let quotient = 0

    // No division by 0
    if(divisor === 0 || divisor > dividend){
        return 0
    }

    let remainder = dividend

    // Subtract divisor from dividend until nothing is left
    while( remainder >= divisor ){
        remainder -= divisor
        quotient += 1
    }

    return quotient
}
```

### 1-33
#### Question
There are twenty-five horses. At most, five horses can race together at a time.
You must determine the fastest, second fastest, and third-fastest horses.
Find the minimum number of races in which this can be done.

#### Solution
I'll note that it's a tourament problem. Usually, at most two opponents would face each other and the number of rounds would be a binary-like splitting until there's only one opponent, the winner.
In this case, the splitting would happen by group of 5.
Each group of 5 would compete and the winner of each group would face each other, and that last round would determine the 1st, 2nd, 3rd winners.

In more practical terms it would look like something like that
Race 1 : all 25 horses are split into groups of 5 and compete. The fastest horse moves to the next race. 
Race 2: all top 5 performers of the previous race will compete. We rank them by their time and find the 1st, 2nd, and 3rd best performer.

Overall 2 races would suffice to do that.
### 1-35

#### Question
How many gas stations are there in the United States?

#### Solution
I'll start by estimating the gas stations in my area which is something like 5km2 and note that there are 3.
Now I'll note that the US has 54 states and that  each are usually as large in km2 as my homeland.
Therefore, I'll multiply 3* (350,000 — which is an approximation of the area of my country) * 54.
For simplyfying the computation I'll round down the number of states to 50.
So mentally that gives ( (100 * 350k) / 2 ) * 3 = 52,5 million gas stations.

Limitations: average area per state might be greater than my country and some areas may smaller or higher population density, meaning more gas stations.

## Assignment 3: Coding questions

### Daily temperature
#### Problem
https://leetcode.com/problems/daily-temperatures/

#### Solution
```javascript
/**
 * @param {number[]} temperatures
 * @return {number[]}
 */
function dailyTemperatures(temperatures) {
    let answer = []
    let smallerValuesStack = []

    // Set all values to 0 by default
    answer = temperatures.map(() => 0)

    for (let i = 0; i < temperatures.length; i++) {

        // Compare temperature[i] against smaller values in stack.
        // Do it in reverse order, hence the stack pattern
        // and update answer's relevant indice

        while( smallerValuesStack.length > 0
            && temperatures[i] > temperatures[smallerValuesStack[smallerValuesStack.length - 1]] ) {

            let warmTemperatureIndex = smallerValuesStack.pop(i)
            let coldTemperatureStreak = i - warmTemperatureIndex ;
            answer[warmTemperatureIndex] = coldTemperatureStreak

        }

        // Track this value because it's smaller than temperature[i-1]
        smallerValuesStack.push(i)
    }

    return answer
}
```

### Rotate List
#### Problem
https://leetcode.com/problems/rotate-list/submissions/1250339333/

#### Solution
```javascript
function rotateRight(head, k) {
    // Check for edge cases where the list is empty or rotation count is zero
    if (!head || k === 0) return head;

    let length = 1; // Variable to store the length of the list
    let tail = head; // Variable to store the tail of the list

    // Traverse the list to find its length and locate the tail node
    while (tail.next) {
        tail = tail.next;
        length++;
    }

    k = k % length; // Adjust k to avoid unnecessary rotations
    if (k === 0) return head; // If k is a multiple of the list length, no rotation needed

    let stepsToNewHead = length - k - 1; // Calculate the number of steps to the new head
    let newTail = head; // Initialize a pointer to find the new tail

    // Move the new tail pointer to the node just before the new head
    for (let i = 0; i < stepsToNewHead; i++) {
        newTail = newTail.next;
    }

    // Perform the rotation
    tail.next = head; // Connect the original tail with the original head to form a loop
    head = newTail.next; // The node next to newTail becomes the new head
    newTail.next = null; // Break the loop at newTail

    return head; // Return the new head of the rotated list
}
```

### Kangaroo
#### Problem
https://www.hackerrank.com/challenges/kangaroo/

#### Solution
```javascript
function kangaroo(x1, v1, x2, v2) {
    /**
     * If the second kangaroo is as fast or faster, they'll never meet  
     */
    if (v1 <= v2) {
        return "NO";
    }

    const position_diff = x2 - x1
    const speed_diff = v1 - v2

    /**
     * Check that dividing the distance by the speed difference returns an integer
     * A decimal means kangaroos will only overlap at partial positions but won't meet
     */
    if (position_diff % speed_diff == 0) {
        return "YES"
    } else{
        return "NO"
    }
}
```

### The 3n + 1 problem
#### Problem
https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=29&page=show_problem&problem=36

#### Solution
```javascript
/**
 * Implementation of the cycle length
 * algorithm basd on the pseudo code in the exercice.
 * @param n {number}
 * @returns {number}
 */
function integerCycleLength(n){
    let cycleLength = 0;

    while (n > 1) {

        if(n % 2 == 0){
            n = n / 2
        // If n is odd make it 3n +1
        } else {
            n = 3*n + 1
        }
        // Increment cycl
        cycleLength += 1
    }

    if (n == 1){
        cycleLength += 1;
        return cycleLength;
    }

    return cycleLength
}

/**
 * Ussing the function above, this utiliy
 * traverses the tuple to find the largest cycleLength
 * @param x
 * @param y
 * @returns {string}
 */
function findLargestCycleLength(x, y){
    let largestCycleLength = 0;

    for (var i = x; i <= y ; i++) {
        let cycleLength = integerCycleLength(i)
        largestCycleLength = Math.max(cycleLength, largestCycleLength)
    }

    return `${x} ${y} ${largestCycleLength}`
}

findLargestCycleLength(201,210) // output 201 210 89
findLargestCycleLength(900,1000) // output 900 1000 174
```