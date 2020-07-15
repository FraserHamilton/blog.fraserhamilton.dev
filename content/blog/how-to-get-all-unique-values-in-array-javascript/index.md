---
title: How to get all unique values in a JavaScript Array
date: '2020-07-15T09:06:00.000Z'
description: 'Removing duplicates for a JavaScript Array with ES6 Set'
---

It can sometimes be useful to be able to remove repeated elements from an Array. Before the introduction of ES6 the best method in which to do this would be using `Array.prototype.filter` like this:

```javascript
const numbers = [8, 6, 8, 6, 4, 1]

const uniqueNumbers = numbers.filter((value, index, self) => {
  return self.indexOf(value) === index
})

console.log(uniqueNumbers)

// [8, 6, 4, 1]
```

<br/>

But with ES6 we can now use the native object `Set` to store unique values and then leverage the spread operator to transform the set back into an array:

```javascript
const numbers = [8, 6, 8, 6, 4, 1]

const uniqueNumbers = [...new Set(list)]

console.log(uniqueNumbers)

// [8, 6, 4, 1]
```

<br/>

It's worth noting that this will only work for primitive values. In JavaScript that's pretty much anything that isn't an object. So we would be able to use this for strings, numbers, booleans etc but not for a `Date` object.
