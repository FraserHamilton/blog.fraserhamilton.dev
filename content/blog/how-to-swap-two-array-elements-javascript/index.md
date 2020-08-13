---
title: How to swap two array elements in JavaScript
date: '2020-08-13T09:43:00.000Z'
description: 'Swapping array elements without needing a temporary variable'
---

Take a look at this example array of five numbers, with values representative of their original starting indexes:

```javascript
const numbers = [0, 1, 2, 3, 4]
```

<br/>

How would we go about swapping the element at index 0 and the element at index 4? Well could achieve this by using a temporary variable like so:

```javascript
const numbers = [0, 1, 2, 3, 4]

const temporary = numbers[0]
numbers[0] = numbers[4]
numbers[4] = temporary

console.log(numbers)

// [4, 1, 2, 3, 0]
```

<br/>

Although this works I find it far more readable and succinct to instead take advantage of the ES6 feature that allows for multiple assignment to switch the elements. Using that syntax our code would resemble this:

```javascript
const numbers = [0, 1, 2, 3, 4]

;[numbers[0], numbers[4]] = [numbers[4], numbers[0]]

console.log(numbers)

// [4, 1, 2, 3, 0]
```
