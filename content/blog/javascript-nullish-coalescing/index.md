---
title: Nullish Coalescing in Javascript
date: '2021-11-03T13:00:00.000Z'
description: 'Learn how and when to use the Nullish Coalescing Operator ??'
---

A Javascript operator that can be often overlooked is the Nullish Coalescing Operator represented as `??`. In this article we will take a look at what it does and where it can be used.

It's fairly common to come across javascript code in which the OR opeartor `||` is used to set a default value for a variable as can be seen below.

```javascript
const myGreeting = greeting || 'Hello!'
```

<br/>

Unfortunatley unbeknownst to some using the OR operator for this purpose can actually have unintended consequences as it will fall back to the default value whenever the variable evaluates to something falsy. Let's take a look at an example in which we are setting the default value for a number.

```javascript
const myNumber = number || 12
```

<br/>

If `number = 15` then the code above would evaluate such that `myNumber = 15`. If `number = null` then it will use the default resulting in `myNumber = 12`.

So far so good but what if we set `number = 0` ? We'd run into trouble because although `number` has a value it's a value that when evaluated as boolean is equivalent to `false` so we'd wind up falling back to our default `number = 12`.

This is where the Nullish Coalescing Operator can come in very handy by switching out `||` for `??` we can guarantee the default value will only be used when `number = null` or `number = undefined`.

```javascript
const myNumber = number ?? 12
```

<br/>
