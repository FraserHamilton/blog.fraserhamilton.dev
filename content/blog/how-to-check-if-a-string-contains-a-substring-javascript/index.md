---
title: How to check if a string contains a substring in JavaScript
date: '2020-07-19T23:00:00.000Z'
description: 'Using string.prototype.includes to check if a substring exists'
---

With JavaScript ES6 we can leverage the `String.prototype.includes` method to check if a substring exists within a string. Here's an example:

```javascript
const string = 'Hello World!'
const substring = 'World'

console.log(string.includes(substring))

// true
```

<br/>

If you're working with older browsers such as Internet Explorer support for this method can be spotty. We can instead use `String.prototype.indexOf`:

```javascript
var string = 'Hello World!'
var substring = 'World'

console.log(string.indexOf(substring) !== -1)

// true
```

<br/>
