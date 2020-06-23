---
title: How to get n elements randomly from an array in JavaScript
date: '2020-06-23T11:19:00.000Z'
description: 'Learn how to get a random sample of n elements from an array'
---

In a previous blog post we covered how to randomly select a value from an array which can be a great utility if you need to generate test data or populate your database. Recently though I found myself in a situation where I wanted to select not one but multiple items randomly. Luckily for me doing this was relatively simple:

```javascript
const tags = ['Web', 'C#', 'Node.js', 'JavaScript', 'Java', 'PHP']

// Jumble array
const jumbledTags = tags.sort(() => 0.5 - Math.random())

// Get sub-array of first n elements after jumbled
const randomTags = jumbledTags.slice(0, 3)

console.log(randomTags)

//  ['C#', 'Web', 'JavaScript']
```

<br/>

This method isn't particularly efficient nor is it truly random but it is perfectly suitable for most situations. If you plan on using this random function a lot throughout one of your projects you can add it to **Array.prototype** like so:

```javascript
Array.prototype.sampleSize = function(n) {
  const jumbled = this.sort(() => 0.5 - Math.random())
  return jumbled.slice(0, n)
}

const tags = ['Web', 'C#', 'Node.js', 'JavaScript', 'Java', 'PHP']

const randomTags = tags.sampleSize(3)

console.log(randomTags)

// ['JavaScript', 'Web', 'PHP']
```

<br/>
