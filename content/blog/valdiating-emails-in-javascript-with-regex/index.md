---
title: How to validate an email address in JavaScript
date: '2020-07-20T12:10:00.000Z'
description: 'Learn how to use regular expressions to validate an email address'
---

Regular expressions are patterns used to match character combinations in strings. They're pretty powerful and are commonly used for anything from validating form fields to searching large text documents. Here's how you could use a JavaScript regular expression to validate an email address:

```javascript
const emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

const pass = 'fraser@webuilddigital.co.uk'
console.log(emailRegex.test(String(pass).toLowerCase()))

// true

const fail = 'fraser hamilton'
console.log(emailRegex.test(String(fail).toLowerCase()))

// false
```

<br/>

If you want to be able to accept unicode you should use this regex instead:

```javascript
const unicodeRegex = /^(([^<>()\[\]\.,;:\s@\"]+(\.[^<>()\[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i

const email = 'Dörte@example.com'

console.log(unicodeRegex.test(String(email).toLowerCase()))

// true
```

<br/>
