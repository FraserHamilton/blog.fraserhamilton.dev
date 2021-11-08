---
title: How to combine an array into a string in JavaScript
date: '2021-11-08T13:00:00.000Z'
description: 'Learn how to use Array.join() to generate string from an array'
---

The Array.join() method allows you to combine an array into a single string. By default each element from the array will be separated by a comma in the returned string. Here's a very simple example of it's usage.

```javascript
const names = ['Bill', 'Ben', 'Beth']

console.log(names.join())
// Bill,Ben,Beth
```

<br/>

It's also possible to pass the `join` method a parameter to override the delimiter. For example if we wanted to instead have each element separated by an empty space we could do the following.

```javascript
const names = ['Bill', 'Ben', 'Beth']

console.log(names.join(' '))
// Bill Ben Beth
```

<br/>

If there are no elements in the array `join` will return an empty string.

```javascript
const names = []

const joined = names.join()

// joined = ''
```

<br/>
