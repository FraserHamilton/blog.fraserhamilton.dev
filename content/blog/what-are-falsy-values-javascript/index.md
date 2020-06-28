---
title: What are Falsy values in JavaScript?
date: '2020-06-28T13:10:00.000Z'
description: 'A brief look at what evaluates to false in JavaScript'
---

In JavaScript falsy values are values that when encountered in a Boolean context are considered to be false. They aren't necessarily equal to each other but will evaluate to false when coerced to a Boolean. There are a total of 8 falsy values:

```javascript
const keywordFalse = false
const numberZero = 0
const numberNegativeZero = -0
const bigIntZero = 0n
const emptyString = ''
const nullVal = null
const undefinedVal = undefined
const notANumber = NaN
```

<br/>

If you're unsure if a value evaluates to falsy you can test it using a simple negated if statement like so:

```javascript
if (!valueToTest) {
  console.log('is falsy')
}
```

<br/>

Here's a little extra fun with the logical `&&` operator, if the first object is falsy, it returns that object:

```javascript
if (!valueToTest) {
  false && 'hello world' // false
  '' && 'hello world'
}
```

<br/>
