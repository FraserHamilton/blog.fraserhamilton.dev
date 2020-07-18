---
title: How to redirect to another page using JavaScript
date: '2020-07-18T09:06:00.000Z'
description: 'Redirecting to pages programmatically using window.location'
---

There's a quite a few different ways to achieve this in JavaScript. To simulate similar behaviour to clicking on a link we can simply use:

```javascript
window.location.href = 'https://blog.fraserhamilton.dev/'
```

<br/>

This will redirect the user and create a new entry in your browsers history stack, meaning you can go back to the previous page using the back button. If you wish to instead simulate a http redirect we can use **replace**:

```javascript
window.location.replace('https://blog.fraserhamilton.dev/')
```

<br/>

We can also use the **window.history** methods to navigate across the browsers history stack:

```javascript
window.history.forward()
window.history.back()

window.history.go(1)
window.history.go(-2)
```

<br/>
