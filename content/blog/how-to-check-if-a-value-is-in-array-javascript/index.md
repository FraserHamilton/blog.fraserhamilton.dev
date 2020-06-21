---
title: How to check if a value is in an array in JavaScript
date: '2020-06-20T11:21:00.000Z'
description: 'Learn how to check if a value is in an array using includes()'
---

By using the JavaScript **Array.prototype** function **includes** we can quickly determine if an array contains a certain element. Here's a simple example:

```javascript
const animals = ['dog', 'cat', 'cow', 'goose', 'bear']

const containsGoose = animals.includes('goose')

console.log(containsGoose)

// true
```

<br/>

If the value isn't in the array the method will return false like so:

```javascript
const animals = ['dog', 'cat', 'cow', 'goose', 'bear']

const containsHorse = animals.includes('horse')

console.log(containsHorse)

// false
```

<br/>

But what if you need to check that an object inside the array contains an attribute with a given value? Well that becomes slightly more complex. Let's try it using just **includes** first:

```javascript
const animals = [
  { name: 'dog', age: 7 },
  { name: 'cat', age: 2 },
  { name: 'cow', age: 16 },
  { name: 'goose', age: 10 },
  { name: 'bear', age: 19 },
]

const hasAge10 = animals.includes(t => t.age === 10)

console.log(hasAge10)

// false
```

<br/>

No bueno, Sadly we can't compare objects directly so **includes** won't work here. We're going to need to look for an alternative, luckily there's a very similar method that we can pass a function to **some**. Let's try it with that:

```javascript
const animals = [
  { name: 'dog', age: 7 },
  { name: 'cat', age: 2 },
  { name: 'cow', age: 16 },
  { name: 'goose', age: 10 },
  { name: 'bear', age: 19 },
]

const hasAge10 = animals.some(t => t.age === 10)

console.log(hasAge10)

// true
```

<br/>

Et voila, now our code behaves as expected. It's worth noting that **includes** is not supported by internet explorer and you may have to either use a polyfill or fall back on **some**.
