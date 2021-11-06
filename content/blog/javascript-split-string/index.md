---
title: How to split a string in JavaScript
date: '2021-11-05T13:00:00.000Z'
description: 'Learn how to split a string into an array of substrings'
---

In Javascirpt the `split` method can be used to divide a stirng into an array of substrings. The split will be performed based on a separtor that is passed to the function.

Here's a classic example of how to split a comma spearated list of values using the `,` character as a separator.

```javascript
const list = '1, 3, 5, 6'

const split = list.split(',')

console.log(split)

// ['1', ' 3', ' 5', ' 6']
```

</br>

However we're not limited to splitting only on a single character we can also do so based on a substring or regular expression. The regular expression used in the second example below matches capital letters.

```javascript
const intro = 'Hello There My Name Is Fraser Hamilton'

const split = intro.split('am')

console.log(split)

// ['Hello There My N', 'e Is Fraser H', 'ilton']

const splitReg = intro.split(/(?=[A-Z])/)

console.log(splitReg)

// ['Hello ', 'There ', 'My ', 'Name ', 'Is ', 'Fraser ', 'Hamilton']
```

</br>
