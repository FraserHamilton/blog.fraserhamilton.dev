---
title: How to generate an array from 0 to N in JavaScript
date: '2020-06-19T13:06:00.000Z'
description: 'Generate an array of values that you can then manipulate with map, forEach etc'
---

Sometimes to we need to generate an array of numbers of a specific length in JavaScript that we can use our favourite **Array.prototype** functions on. I often find myself doing exactly that when I'm generating test data to populate my database with. Here's a simple example using the **from** and **keys** methods:

```javascript
const array = Array.from(Array(10).keys())

console.log(array)

// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br/>

With the introduction the spread operator in ES6 we can actually make this snippet even shorter like so:

```javascript
const array = [...Array(10).keys()]

console.log(array)

// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br/>
