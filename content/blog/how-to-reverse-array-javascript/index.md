---
title: How to reverse an array in JavaScript
date: '2020-06-16T21:58:00.000Z'
description: 'Learn how to reverse an array in Javascript using the Array.prototype method'
---

Reversing an array in JavaScript couldn't be any easier thanks to Array.prototype.reverse() method. You can use it on any array like this:

```javascript
const cities = ['paris', 'london', 'new york', 'rome']

const reversed = cities.reverse()

console.log(reversed)

// ['rome', 'new york', 'london', 'paris']
```

<br/>

This method reversing the array using an [in place](https://en.wikipedia.org/wiki/In-place_algorithm) method.

What if we wanted to reverse the array without using this method? Well we could create our own function that does it for us.

```javascript
const reverseArray = arr => {
  let rev = new Array()
  for (let i = arr.length - 1; i >= 0; i--) {
    rev.push(arr[i])
  }
  return rev
}

const cities = ['paris', 'london', 'new york', 'rome']

const reversed = reverseArray(cities)

console.log(reversed)

// ['rome', 'new york', 'london', 'paris']
```

<br/>
