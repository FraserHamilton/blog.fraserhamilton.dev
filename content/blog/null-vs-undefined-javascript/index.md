---
title: JavaScript undefined vs null
date: '2020-07-09T09:00:00.000Z'
description: 'The difference between undefined and null in JavaScript'
---

In JavaScript both `undefined` and `null` primitive types.

```javascript
let foo

console.log(foo)

// undefined
```

<br/>

A variable is `undefined` when it has been declared but not assigned a value.

```javascript
let bar = null

console.log(bar)

// null
```

<br/>

For a variable to be `null` it must be directly assigned the value.

You can check for equality for both primitives using `===` like so:

```javascript
let foo
let bar = null

console.log(foo === undefined)

//true

console.log(bar === null)

//true
```

<br/>

And as they are both falsy values they will be false when coalesced to a boolean.

```javascript
let foo
if (!foo) {
  console.log('foo is False')
}

// Foo is False

let bar = null
if (!bar) {
  console.log('bar is False')
}

// bar is False
```

<br/>

However there's some slightly unexpected behaviour when we use the `typeof` operator.

```javascript
let foo
typeof foo

// undefined

let bar = null
typeof bar

// object
```

<br/>

Despite being a primitive type `null` evaluates to an object.
