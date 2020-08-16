---
title: Introduction to JavaScript Scheduling
date: '2020-08-16T09:30:00.000Z'
description: 'Using setTimeout and setInterval to control the execution of code at specified time intervals'
---

At some point when working with JavaScript you're going to want to delay the execution of a piece of code until a specified time. The `window` object has two methods that allow you to do this `setTimeout` and `setInterval`. These methods can be used in all browsers and are even supported in node and deno.

## setTimeout

Calls a function or evaluates an expression after a specified number of milliseconds.

```javascript
const hello = () => {
  console.log('Hello World!')
}

setTimeout(hello, 1000)

// waits 1000 ms or 1 seconds

// Hello World!
```

<br/>

We can even pass parameters to our timeout function.

```javascript
const hello = name => {
  console.log(`Hello ${name}!`)
}

setTimeout(hello, 1000, 'Fraser')

// waits 1000 ms or 1 seconds

// Hello Fraser!
```

<br/>

Having a declared function just for the purpose of saying hello seems a little heavy, we can just use an arrow function directly in our setTimeout instead.

```javascript
setTimeout(() => console.log('Hello World!'), 1000)

// waits 1000 ms or 1 seconds

// Hello World!
```

<br/>

When we call `setTimeout` we get a timer identifer back which we can then use to cancel the execution by passing it to `clearTimeout`

```javascript
const timerId = setTimeout(() => console.log('Hello World!'), 1000)

clearTimeout(timerId)

// Never executes
```

## setInterval

Works exactly the same as setTimeout but instead of running the function or expression only once it instead does so repeatedly after a specified interval.

```javascript
const hello = name => {
  console.log(`Hello ${name}!`)
}

setInterval(hello, 1000, 'Fraser')

// waits 1000 ms or 1 seconds

// Hello Fraser!

// waits 1000 ms or 1 seconds

// Hello Fraser!

// ...
```

<br/>

And to cancel we instead call `clearInterval`

```javascript
const hello = name => {
  console.log(`Hello ${name}!`)
}

const intervalId = setInterval(hello, 1000, 'Fraser')

setTimeout(() => {
  clearInterval(intervalId)
  console.log(`Cancelled Interval`)
}, 2500)

// waits 1000 ms or 1 seconds

// Hello Fraser!

// waits 1000 ms or 1 seconds

// Hello Fraser!

// waits 500 ms or half a second

// Cancelled Interval
```

<br/>
