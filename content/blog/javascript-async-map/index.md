---
title: How to call an async function with Array.map
date: '2021-11-02T13:00:00.000Z'
description: 'Learn how and when to use the Nullish Coalescing Operator ??'
---

The Javascript Array.prototype.map() method creates a new array by calling a function that you specify on each element in the original array.

The map concept is simple but exteremly powerful but what if the function that we want to call on our elements is asynchronous? To call async functions from a map we need to wrap everything in a Promise.all which will resolve once all of it's child promises are resolved.

```javascript
const list = [1, 2, 3, 4, 5]

const allData = await Promise.all(list.map(i => asyncFunction(i)))
```

<br/>

The example above won't actually run as the `asyncFunction` is not defined anywhere however it will give you an idea of the general syntax. Here's a real world example taken from a project I worked on previously in which I was making an API call for each element to create a new entry in a CMS but wanted to build a list of inserted Ids. I've modified the code to keep the length reasonable.

```javascript
const articlesToBeAdded = [
  {
    _type: 'article',
    title: 'Firestone Walker 25th Anniversary Ale',
    description:
      'Winemakers are masters in the art of blending, which is why Firestone Walker invites...',
  },
  {
    _type: 'article',
    title: 'Shinola Middle Child Detrola Watch',
    description:
      "Understated but immediately noticeable — that's the philosophy behind the Shinola Middle Child Detrola watch...",
  },
  {
    _type: 'article',
    title: 'The Reserve Society From The Bruery',
    description:
      'The Bruery pushes the boundaries of what beer can be with innovative, inspired, taste-forward beer...',
  },
]

const results = await Promise.all(
  articlesToBeAdded.map(a =>
    axios.post('https://imaginary-cms.org/api', {
      data: a,
    })
  )
)

const insertedIds = results.map(r => r.data.id)

console.log(insertedIds)
```

</br>
