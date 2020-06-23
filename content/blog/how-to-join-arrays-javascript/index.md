---
title: How to join two arrays in JavaScript
date: '2020-06-16T15:34:00.000Z'
description: 'Learn how to combine two arrays into a new array'
---

There are 2 easy ways to combine two arrays into one in JavaScript. You can use the spread operator introduced in ES6 and combine them like so:

```javascript
const boys = ['brian', 'james', 'rory']
const girls = ['karen', 'emily', 'louisa']

const boysAndGirls = [...boys, ...girls]

console.log(boysAndGirls)

// ['brian', 'james', 'rory', 'karen', 'emily', 'louisa']
```

<br/>

It's worth nothing that the order in which you spread the arrays inside of the new array will reflect the order of the combined array. So because we spread boys both before girls they come first in our result.

If you need to support older browsers you can also use concat to join two arrays:

```javascript
const boys = ['brian', 'james', 'rory']
const girls = ['karen', 'emily', 'louisa']

const boysAndGirls = [].concat(boys, girls)

console.log(boysAndGirls)

// ['brian', 'james', 'rory', 'karen', 'emily', 'louisa']
```

<br/>
