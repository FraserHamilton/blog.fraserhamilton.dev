---
title: How to flatten an array in JavaScript
date: '2020-06-17T13:06:00.000Z'
description: 'Learn how to flatten an array in JavaScript'
---

Previously flattening an array in JavaScript could have you reaching for utility libraries like lodash or underscore but the language is constantly evolving and we can now use Array.prototype.flat() to achieve the same result in vanilla JavaScript. Here's a simple example with a depth of 1:

```javascript
const colors = [
  ['red', 'blue'],
  ['green', 'pink'],
]

const flatColors = colors.flat()

console.log(flatColors)

// ["red", "blue", "green", "pink"]
```

<br/>

What if we wanted to flatten an array with a depth greater than 1? Luckily for us the flat method accepts a depth argument. Here's how to flatten an array with a depth of 3:

```javascript
const colors = [
  ['red', ['blue', 'yellow']],
  ['green', ['pink', ['orange', 'brown']]],
]

const flatColors = colors.flat(3)

console.log(flatColors)

// ["red", "blue", "yellow", "green", "pink", "orange", "brown"]
```

<br/>

This is great as long as you know the depth but what can we do if we're unsure? We can pass **Infinity** as the depth argument. Here's an example using that:

```javascript
const colors = [
  ['red', ['blue']],
  ['green', ['pink', ['orange', ['brown']]]],
]

const flatColors = colors.flat(Infinity)

console.log(flatColors)

// ["red", "blue", "green", "pink", "orange", "brown"]
```

<br/>

If you need to support internet explorer you won't be able to use this method so we need another solution. Using **concat** and the **spread operator** we can recreate the result like so:

```javascript
const colors = [
  ['red', 'blue'],
  ['green', 'pink'],
]
const flatten = arr => [].concat(...arr)

const flatColors = flatten(colors)

console.log(flatColors)

// ["red", "blue", "green", "pink"]
```

<br/>
