---
title: How to get a timestamp in JavaScript
date: '2020-07-21T10:10:00.000Z'
description: 'Get a number that represents a point in time by the number of ms that have passed since the Unix Epoch'
---

When working with dates and times it's often useful to be able to represent your point in time as a single number. A good example of this in practice is [Unix Timestamps](https://en.wikipedia.org/wiki/Unix_time), where it is represented as the number of seconds that have passed since the Unix epoch; 00:00:00 UTC on 1 January 1970.

In JavaScript we can achieve something similar by leveraging the native Date object. By using `Date.now()` we can get the UTC timestamp in milliseconds.

```javascript
console.log(Date.now())

// 1595331292901
```

<br/>

It's also possible to use this short hand that uses a unary operator to trigger the valueOf method on our Date object.

```javascript
console.log(+new Date())

// 1595331292901
```

<br/>

If you wanted to then convert these to seconds to match the Unix Epoch Time you would just do this:

```javascript
Math.floor(Date.now() / 1000)

// 1595331292
```

<br/>
