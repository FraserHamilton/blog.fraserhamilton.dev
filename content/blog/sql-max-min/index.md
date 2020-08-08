---
title: Max and Min in PostgreSQL
date: '2020-08-08T09:00:00.000Z'
description: 'Getting to grips with the max and min aggregate functions in Postgres'
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

In our application we might want to find the most expensive order, this is a perfect use case for the MAX aggregate function. Here's what our query would look like:

```SQL
SELECT MAX(cost) as most_expensive FROM orders
```

<br/>

And here's the result:

| most_expensive |
| -------------- |
| 146.00         |

We can also find the least expensive order, by altering our query to this:

```SQL
SELECT MIN(cost) as least_expensive FROM orders
```

<br/>

And here's the result:

| least_expensive |
| --------------- |
| 20.00           |

But we can take this even further, what if we wanted find the most expensive order for each person? We can alter our original query to include the order name and then group on it. So our new query looks like this:

```SQL
SELECT name, MAX(cost) as most_expensive FROM orders GROUP BY name;
```

<br/>

And this is our result:

| name        | most_expensive |
| ----------- | -------------- |
| John Doe    | 134.00         |
| Eve Marcus  | 146.00         |
| Lucy Tomlin | 90.00          |
| Bill Carson | 122.00         |
