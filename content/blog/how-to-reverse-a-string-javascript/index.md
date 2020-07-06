---
title: How to reverse a string in JavaScript
date: '2020-07-06T13:11:00.000Z'
description: 'Learn how to reverse a string in Javascript using the Array.prototype methods'
---

By leveraging JavaScript's built in methods we can reverse a string in 3 easy steps. First we use `split` to turn our string into an array so we can use those handy `Array.protoype` methods.

```javascript
const foo = 'Hello World!'

const bar = foo.split('')

console.log(bar)

// ["H", "e", "l", "l", "o", " ", "W", "o", "r", "l", "d", "!"]
```

<br/>

Then we can use the `reverse` method to reverse our array.

```javascript
const foo = 'Hello World!'

const bar = foo.split('').reverse()

console.log(bar)

// ["!", "d", "l", "r", "o", "W", " ", "o", "l", "l", "e", "H"]
```

<br/>

And finally use `join` to reassemble our string from the reversed array.

```javascript
const foo = 'Hello World!'

const bar = foo
  .split('')
  .reverse()
  .join('')

console.log(bar)

// !dlroW olleH
```

<br/>

Although we've reached the desired result it might be nicer to have this as a little utility function you can reuse around your project.

```javascript
const reverseStr = str => {
  return str
    .split('')
    .reverse()
    .join('')
}

const foo = 'Hello World!'

const bar = reverseStr(foo)

console.log(bar)

// !dlroW olleH
```

<br/>

You could even extend JavaScript's existing `String.prototype` with your shiny new method although doing so isn't always a good idea, when you extend an object you change it's behaviour and this can cause bugs.
