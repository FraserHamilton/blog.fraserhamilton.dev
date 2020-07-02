---
title: How to check the type of a variable in JavaScript
date: '2020-07-02T11:06:00.000Z'
description: 'Using typeof & instanceof methods to check the type of any variable'
---

Just because you don't have to declare your types in your JavaScript code doesn't mean that they aren't there at runtime. JavaScript is both weakly and dynamically typed which allows for a lot of flexibility in terms of implicit conversions. Let's look at an example:

```javascript
const message = 'Hello World!'

typeof message // "string"
```

</br>

Here we're using the `typeof` operator to get the underlying type for our variable message. In this instance it's returned `'string'` but there's actually a total of 6 values it can return.

```javascript
typeof 'Hello World!' // "string"

typeof 2 // "number"

typeof true // "boolean"

typeof {} // "object"

typeof function() {} // "function"

typeof undeclaredVar // "undefined"
```

</br>

We can use a different method `instanceof` to check if a variable is of the type specified

```javascript
const person = new Person()
person instanceof Person // true
person instanceof String // false
person instanceof Vehicle // false
```

</br>

What it's really doing here is just testing if the provided function's prototype is in the object's prototype chain.
