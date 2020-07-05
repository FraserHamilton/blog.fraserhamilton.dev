---
title: Understanding the JavaScript this keyword
date: '2020-07-05T17:27:00.000Z'
description: 'Demystifying how the value of this is assigned in different contexts'
---

In JavaScript the value that the `this` keyword refers to changes depending on the current execution context. The execution context is the environment in which a line is being executed, the JavaScript interpreter maintains a stack of these contexts and updates the object that `this` references to keep it current.

## Global Execution Context

Outside of any function, this refers to the global object. In web browsers, the window object is also the global object. In
a Node.js environment it will refer to a special object called `global`.

```javascript
console.log(this === window)

// true
```

## Function Execution Context

When you use `this` inside of a function it's value will depend on how you are calling that function.

```javascript
function foo() {
  console.log(this === window)
}

foo()

// true
```

<br/>

Immediately invoked function expressions behave the exact same.

```javascript
;(function foo() {
  console.log(this === window)
})()

// true
```

<br/>

If strict mode is enabled for any function, then the value of `this` will be `undefined`.

```javascript
function foo() {
  'use strict'
  console.log(this === window)
  console.log(this === undefined)
}

foo()

// false (this !== window)
// true (this === undefined)
```

<br/>

Every function in JavaScript has `call`, `bind` and `apply` methods that can be used to set a custom value for `this`.

```javascript
const custom = { message: 'Hello Universe!' }

const message = 'Hello World!'

function logThisMessage() {
  console.log(this.message)
}

logThisMessage()
// Hello World!

logThisMessage.call(custom)
// Hello Universe!

logThisMessage.apply(custom)
// Hello Universe!
```

<br/>

You may have noticed that both call and apply are doing the same thing in the above example, the difference between them is how you would pass additional arguments to function.

```javascript
const custom = { message: 'Hello Universe!' }

const message = 'Hello World!'

function logThisMessage(arg1, arg2) {
  console.log(`${this.message} total: ${this.arg1 + this.arg2}`)
}

logThisMessage(3, 2)
// Hello World! total: 5

logThisMessage.call(custom, 3, 2)
// Hello Universe! total: 5

logThisMessage.apply(custom, [3, 2])
// Hello Universe! total: 5
```

<br/>

Bind behaves a little bit differently, it creates a new function with the same body and scope as the function you're calling it on but where `this` occurs in original function, it is now permanently bound to the first argument of bind.

```javascript
function logThisMessage() {
  console.log(this.message)
}

const helloWorld = logThisMessage.bind({ message: 'Hello Universe!' })
helloWorld()
// Hello Universe!

const myObj = {
  message: 'Hello World!',
  logThisMessage: logThisMessage,
  helloWorld: helloWorld,
}

console.log(myObj.a)
// Hello World!

myObj.logThisMessage()
// Hello World!

myObj.helloWorld()
// Hello Universe!
```

<br/>

With arrow functions the value of this doesn't change and instead keeps referencing the object for the enclosing lexical context.

```javascript
const foo = () => console.log(this === window)

foo()

// true
```

<br/>

In this example the enclosing lexical context remains the global context meaning this references the window object.

## Class Execution Context

When we create a new instance of our class using the `new` keyword, `this` refers to the newly created instance.

```javascript
class Car {
  constructor(make, model) {
    this.make = make
    this.model = model
  }

  displayMakeModel() {
    console.log(`Make: ${this.make}, Model: ${this.model}`)
  }
}

const car = new Car('Ford', 'Focus')
car.displayMakeModel()

// Make: Ford, Model: Focus

const anotherCar = new Car('Fiat', 'Punto')
anotherCar.displayMakeModel()

// Make: Fiat, Model: Punto
```

<br/>

Because JavaScript classes are really just functions under the hood you can use the `call`, `bind` and `apply` methods on them as well.
