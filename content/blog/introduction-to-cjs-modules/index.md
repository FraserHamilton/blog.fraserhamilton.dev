---
title: Introduction to CommonJS Modules
date: '2020-06-29T12:42:00.000Z'
description: 'Getting to grips with the ECMAScript module system'
---

Despite the ECMAScript Module system being the official standard for modules in JavaScript, Node.js continues to use CommonJS by default. You can use the ES Module System in your Node projects by compiling your js with something like Babel but it's worth learning the CJS syntax as well.

Before we deep-dive the syntax we first need to define what a module is in JavaScript:

> A module is a JavaScript file that exports one or more values (objects, functions or variables), using the export keyword.

In order to import one of these modules we use `require`. Let's take a look at a simple example:

```javascript
const package = require('module-name')
```

<br/>

And to export something from a module we add it to the exports like so:

```javascript
// add.js

exports.add = (x, y) => x + y
```

<br/>

This is just a simple function that takes two numbers, adds them together and returns the result.

Here's how we would import and use our shiny new **add** module:

```javascript
const addModule = require('./add.js')

addModule.add(1, 2) // returns 3
addModule.add(2, 2) // returns 4

// This add module can actually also be used to concatenate strings
addModule.add('Hello ', 'World') // returns Hello World
```

<br/>

You can also export more than one value like this:

```javascript
// math.js

exports.add = (x, y) => x + y
exports.subtract = (x, y) => x - y
exports.multiply = (x, y) => x * y
exports.divide = (x, y) => x / y
```

<br/>

Then we can import these exports individually by leveraging the destructuring syntax.

```javascript
const { add, subtract, multiply, divide } = require('./math.js')

add(1, 2) // returns 3
subtract(2, 1) // returns 1
multiply(3, 3) // returns 9
divide(4, 2) // returns 2
```

<br/>

It's even possible to export just a single value for a module, similar to how default exports work in ES Modules.

```javascript
// math.js

const add = (x, y) => x + y

module.exports = add
```

<br/>

and then import it like this:

```javascript
const add = require('./math.js')

add(1, 2) // returns 3
```

<br/>
