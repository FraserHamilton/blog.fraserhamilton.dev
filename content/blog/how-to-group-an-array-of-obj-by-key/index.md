---
title: How to group an array of objects by key in JavaScript
date: '2020-07-07T19:19:00.000Z'
description: 'Learn how to use Array.prototype.reduce to group an array of objects by key'
---

It's often useful to be able to take an array of objects and group them by key. You can reach for utility libraries like lodash or underscore but this task can actually be accomplished with vanilla JavaScript. We can leverage `Array.prototype.reduce` to build our little utility method.

```javascript
const orders = [
  {
    productId: 32,
    customerId: 23,
    quantity: 2,
    placedOn: '2020-07-07',
  },
  {
    productId: 47,
    customerId: 44,
    quantity: 5,
    placedOn: '2020-07-06',
  },
  {
    productId: 32,
    customerId: 64,
    quantity: 3,
    placedOn: '2020-07-07',
  },
  {
    productId: 12,
    customerId: 10,
    quantity: 1,
    placedOn: '2020-07-03',
  },
  {
    productId: 9,
    customerId: 55,
    quantity: 1,
    placedOn: '2020-07-06',
  },
]

const grouped = orders.reduce((r, a) => {
  r[a.placedOn] = [...(r[a.placedOn] || []), a]
  return r
}, {})

console.log(JSON.stringify(grouped))
```

```json
{
  "2020-07-07": [
    {
      "productId": 32,
      "customerId": 23,
      "quantity": 2,
      "placedOn": "2020-07-07"
    },
    {
      "productId": 32,
      "customerId": 64,
      "quantity": 3,
      "placedOn": "2020-07-07"
    }
  ],
  "2020-07-06": [
    {
      "productId": 47,
      "customerId": 44,
      "quantity": 5,
      "placedOn": "2020-07-06"
    },
    {
      "productId": 9,
      "customerId": 55,
      "quantity": 1,
      "placedOn": "2020-07-06"
    }
  ],
  "2020-07-03": [
    {
      "productId": 12,
      "customerId": 10,
      "quantity": 1,
      "placedOn": "2020-07-03"
    }
  ]
}
```

<br/>

It's a simple as that but we can still make some improvements. We want to be able to reuse this code to group any array of objects not just our orders.

```javascript
const orders = [...]

const groupBy = (arr, key) => {
  return arr.reduce((r, x) => {
    r[x[key]] = [...(r[x[key]] || []), x]
    return r
  }, {})
}

const grouped = groupBy(orders, 'placedOn')

console.log(JSON.stringify(grouped))
```

```json
{
  "2020-07-07": [
    {
      "productId": 32,
      "customerId": 23,
      "quantity": 2,
      "placedOn": "2020-07-07"
    },
    {
      "productId": 32,
      "customerId": 64,
      "quantity": 3,
      "placedOn": "2020-07-07"
    }
  ],
  "2020-07-06": [
    {
      "productId": 47,
      "customerId": 44,
      "quantity": 5,
      "placedOn": "2020-07-06"
    },
    {
      "productId": 9,
      "customerId": 55,
      "quantity": 1,
      "placedOn": "2020-07-06"
    }
  ],
  "2020-07-03": [
    {
      "productId": 12,
      "customerId": 10,
      "quantity": 1,
      "placedOn": "2020-07-03"
    }
  ]
}
```

<br/>

And just like that you've avoided importing a bulky utility library all thanks to the handy native array methods.
