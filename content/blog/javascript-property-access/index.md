---
title: JavaScript Property Access
date: '2020-08-06T09:00:00.000Z'
description: 'Dot notation versus brackets, which is preferable and why?'
---

When it comes to accessing an objects properties in JavaScript we have two options, we can use the dot notation or the square bracket notation. Here's a simple example illustrating the usage of both.

```javascript
const obj = { foo: 'bar' }

const x = obj.foo

console.log(x)

// bar

const y = obj['foo']

console.log(y)

//bar
```

<br/>

So which should we be using? Dot notation is in my opinion faster to write and cleaner to read. So I would recommend using it wherever you can. There are some situations in which dot notation cannot be used due to special characters in the object's property names.

```javascript
const obj = { 'foo[]': bar, 'foo.foo': bar }

const x = obj.foo[] // invalid syntax

const x = obj['foo[]']

console.log(x)

// bar

const y = obj.foo.foo // invalid syntax

const y = obj['foo.foo']

console.log(y)

//bar
```

<br/>

The square bracket can also sometimes be preferable when dealing with property names that vary in a predictable way:

```javascript
for (let i = 0; i < 5; i++) {
  someFunction(myForm['control' + i])
}
```

<br/>
