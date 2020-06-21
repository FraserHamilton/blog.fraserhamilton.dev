---
title: How to partition an array based on a condition in JavaScript
date: '2020-06-21T12:30:00.000Z'
description: 'Create a utility function to partition an array based on a condition in vanilla JS'
---

Although not all that common of a situation it is possible to find yourself needing to partition an array in JavaScript. Utility libraries such as lodash and underscore offers ways to do this but it's actually perfectly possible in vanilla JavaScript and it's not even that complex.

Say we have an array of numbers and we want to get the array of all numbers that over 10? Well that's easy enough we can just use **filter**:

```javascript
const numbers = [1, 7, 32, 24, 3, 55, 137, 8]

const over10 = numbers.filter(n => n > 10)

console.log(over10)

// [32, 24, 55, 137]
```

<br/>

But what if we want to also get an array of the values we've filtered out? We could run another **filter** over the array using the opposite condition:

```javascript
const numbers = [1, 7, 32, 24, 3, 55, 137, 8]

const over10 = numbers.filter(n => n > 10)

const notOver10 = numbers.filter(n => !(n > 10))

console.log(over10)

// [32, 24, 55, 137]

console.log(notOver10)

// [1, 7, 3, 8]
```

<br/>

Although it works this isn't a particularly efficient solution to the problem as we need to iterate over the array twice with **filter**. Through clever use of destructuring and **reduce** we can actually implement a better version.

```javascript
const numbers = [1, 7, 32, 24, 3, 55, 137, 8]

const [over10, notOver10] = numbers.reduce(
  (result, element) => {
    result[element > 10 ? 0 : 1].push(element)
    return result
  },
  [[], []]
)

console.log(over10)

// [32, 24, 55, 137]

console.log(notOver10)

// [1, 7, 3, 8]
```

</br>

Exact same result but we've only iterated through the array once! We could even split this code out and make a handy little utility function to be reused across our project if we so wished.
