---
title: String interpolation in JavaScript
date: '2020-07-01T12:53:00.000Z'
description: 'How to perform string interpolation using template literals'
---

No matter what you're doing in JavaScript you're going to have to deal with strings at some point. String interpolation makes working with them a hell of a lot easier so it's a great tool to get a handle on.

There's a few different ways that we can create string literals, with single quotes `'`:

```javascript
const normalSingle = 'Hello World!'
```

</br>

with double quotes `"`:

```javascript
const normalDouble = 'The Quick Brown Fox'
```

</br>

and finally with a backtick, this is the one we're going to be focusing on in this article.

```javascript
const templateLiteral = `The Quick Brown Fox`
```

## Multi-line strings

When we enclose our string with backticks we refer to it as a template literal, added in ES6 they bring a lot to the table. For example using a normal string you would need to use this syntax to get a new line:

```javascript
const normal = `The Quick Brown Fox /n jumped over the lazy dog`
```

</br>

You could achieve the same in a template literal like this:

```javascript
const templateLiteral = `The Quick Brown Fox
                         jumped over the lazy dog`
```

## Expression interpolation

This is where you'll really start to see the power of this feature, embedding an expression inside a normal string might look like this:

```javascript
const a = 7
const b = 2

const result = 'The result is ' + (a + b) + '.'
// The result is 9
```

</br>

Whereas with template literals we can make it more readable:

```javascript
const a = 7
const b = 2

const result = `The result is ${a + b}.`
// The result is 9
```

</br>

It's even possible to nest these template literals but we'll save that for a future article.
