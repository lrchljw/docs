---
title: Debugging Methods
---

Methods for debugging code

<!-- truncate -->

## Try in the following order

### 1. Read Through the Code

> to understand the logic

:::tip
Write comments when reading the code may help you understand the logic better.
:::

> and to find simple mistakes

Ask yourself the following questions when reading each line of code:

- Is there any typo such as write `==` as `=`?
- When access `array[i]`, is `i` within the bounds of the array?
- When access `map[key]`, is `key` present in the map?
- When increase/decrease/multiply a variable, will the value exceed the limit? (e.g. overflow) or When divide a variable, will the value be zero? (e.g. divide by zero)

### 2a. Manual Simulation

> Simulate sample inputs and trace the code manually to check for mistakes.

For example, to simulate the logic of the code below:

```js
/**
 * getScore generates 6 random scores that sum up to the totalScore,
 * and ensures that each score is between 1 and 50.
 * @param {number} totalScore
 * @param {number[]} result
 * @return {number[]}
 */
function getScore(totalScore, result) {
  if (totalScore == 0) {
    return result;
  }

  var resultLeft = 6 - result.length;
  var scoreMax = Math.min(totalScore - (resultLeft - 1) * 1, 50);
  var scoreMin = Math.max(totalScore - (resultLeft - 1) * 50, 1);

  var randomScore = Math.ceil(Math.random() * (scoreMax - scoreMin)) + scoreMin;
  result.push(randomScore);

  return getScore(totalScore - randomScore, result);
}

console.log(getScore(200, []));
```

You can use a piece of paper and a pen to write down the values of the variables and the results of each step.

```csv
totalScore, resultLeft, scoreMin, scoreMax, randomScore, result

200,        6,          1,        50,       26,          [26]
174,        5,          1,        50,       11,          [26, 11]
163,        4,          13,       50,       43,          [26, 11, 43]
120,        3,          20,       50,       32,          [26, 11, 43, 32]
88,         2,          38,       50,       46,          [26, 11, 43, 32, 46]
42,         1,          42,       42,       42,          [26, 11, 43, 32, 46, 42]

200,        6,          1,        50,       50,          [50]
150,        5,          1,        50,       50,          [50, 50]
100,        4,          1,        50,       50,          [50, 50, 50]
50,         3,          1,        48,       48,          [50, 50, 50, 48]
2,          2,          1,        1,        1,           [50, 50, 50, 48, 1]
1,          1,          1,        1,        1,           [50, 50, 50, 48, 1, 1]
```

### 2b. Print Intermediate Results (Logging)

> Insert print statements or log messages in the code to output intermediate results and track down issues.

### 3. Step-by-Step Debugging (IDE)

:::tip
Not recommended, unless you are debugging a complex issue with so many states that manual simulation is not feasible, and logging is too cumbersome.
:::

## The Best Way to Debug is to Avoid Errors

### 1. Static Analysis During Coding

> Perform static analysis techniques while writing the code to identify and prevent errors early.

### 2. Modularization

> Break down the code into smaller functions and modules to make it easier to understand and locate the issue. Many bugs occurs in a single module or function.
