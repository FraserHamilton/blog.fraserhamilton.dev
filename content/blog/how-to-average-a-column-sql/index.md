---
title: How to get the average of a column in SQL
date: '2020-08-07T09:00:00.000Z'
description: 'Using the AVG aggregate function in SQL to get average of the values of a column'
---

Let's say we have a database table named orders with columns: id, name, and cost.

| id  | name        | cost   |
| --- | ----------- | ------ |
| 1   | John Doe    | 134.00 |
| 2   | Eve Marcus  | 146.00 |
| 3   | Lucy Tomlin | 20.00  |
| 4   | Bill Carson | 118.00 |
| 5   | John Doe    | 102.00 |
| 6   | Lucy Tomlin | 90.00  |
| 7   | Lucy Tomlin | 34.00  |
| 8   | Bill Carson | 122.00 |

In our application we might want to find the average cost of all orders, this is a perfect use case for the AVG aggregate function. Here's what our query would look like:

```SQL
SELECT AVG(cost) as average_cost FROM orders
```

<br/>

And here's the result:

| average_cost |
| ------------ |
| 95.75        |

But we can take this even further, what if we wanted to get an average of each persons orders? We can alter our select to include the order name and then grouping on it. So our new query looks like this:

```SQL
SELECT name, AVG(cost) as average_cost FROM orders GROUP BY name;
```

<br/>

And this is our result:

| name        | average_cost |
| ----------- | ------------ |
| John Doe    | 118.00       |
| Eve Marcus  | 146.00       |
| Lucy Tomlin | 48.00        |
| Bill Carson | 120.00       |
