---
title: Loops in JavaScript
date: '2020-07-10T09:00:00.000Z'
description: 'Loops explained: for loops, while loops, control flow'
---

Loops allow you to repeatedly run a block of code until a certain condition is met. There are many different types of loops and each offers a unique way to specify start and end points. By picking the right loop for a situation you can make your code more digestible and potentially more performant.

## for

Similar to `for` loops in other languages, the `for` loop repeats until a condition evaluates to `false`.

```javascript
for (i = 0; i < 5; i++) {
  console.log('The number is ' + i)
}

/* 
    The number is 0
    The number is 1
    The number is 2
    The number is 3
    The number is 4
*/
```

<br/>

The for loop above consists of 3 parts:

1. The initializing expression `i = 0` in the above example, initializes the loop counter to 0
2. The condition expression comes next `i < 5`, when this expression evaluates to `false` the loop will terminate.
3. The increment expression `i++`, executes last modifying the loop counter

Here's a slightly more complex example looping over an array:

```javascript
const cities = ['paris', 'london', 'new york', 'rome']

for (i = 0; i < cities.length; i++) {
  console.log(cities[i])
}

/* 
    paris
    london
    new york
    rome
*/
```

## for in

The for in loop allows you to loop through the properties of an object.

```javascript
const city = { name: 'paris', population: 5.2, country: 'france' }

for (const item in city) {
  console.log(city[item])
}

/*
    paris
    5.2
    france
*/
```

## for of

The JavaScript for of loop allows you to loop through the values of iterable objects e.g. Arrays, Maps, Strings

```javascript
const cities = ['paris', 'london', 'new york', 'rome']

for (const city of cities) {
  console.log(city)
}

/*
    paris
    london
    new york
    rome
*/
```

## while

The while loop is a simple one, it will continue to execute until the condition evaluates to `false`. The condition check is carried out before the loop is executed.

```javascript
let i = 0

while (i < 5) {
  console.log(i)
  i++
}

/*
    0
    1
    2
    3
    4
*/
```

## do while

Similar to the while loop except the condition check is carried out after the code block is executed. This guarantees that the code block will be executed at least once.

```javascript
let i = 0

do {
  console.log(i)
  i++
} while (i < 5)

/*
    0
    1
    2
    3
    4
*/

do {
  console.log('Hello World')
} while (false)

// Hello World
```

## break

The break keyword will terminate the execution of a loop.

```javascript
const cities = ['paris', 'london', 'new york', 'rome']

for (i = 0; i < cities.length; i++) {
  if (cities[i] === 'new york') {
    break
  }
  console.log(cities[i])
}

// paris
// london
```

## continue

The continue keyword will terminate the execution of one iteration of a loop and continue with the next iteration.

```javascript
const cities = ['paris', 'london', 'new york', 'rome']

for (i = 0; i < cities.length; i++) {
  if (cities[i] === 'new york') {
    continue
  }
  console.log(cities[i])
}

// paris
// london
//rome
```

<br/>
