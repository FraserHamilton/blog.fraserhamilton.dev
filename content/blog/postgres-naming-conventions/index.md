---
title: 'Postgres Naming Conventions'
date: '2020-07-13T09:06:00.000Z'
description: 'What convention should be used when naming databases, tables, and fields?'
---

| Item         | Case                      | Example           |
| ------------ | ------------------------- | ----------------- |
| SQL Keywords | UPPER CASE                | INNER JOIN        |
| Databases    | snake_case                | example_db        |
| Tables       | snake_case                | availability_rule |
| JOIN tables  | snake_case (alphabetical) | booking_person    |
| Fields       | snake_case                | first_name        |

There isn't a formal manual on when it comes to naming conventions in Postgres but there is a widespread convention that I find it useful to follow. It's primarily driven by how Postgres deals with identifiers.

The first rule is that all identifiers are case-folded to lower case.

```SQL
UPDATE MY_EXAMPLE SET A = 5;
UPDATE my_examPLE SET A = 5;
UPDATE my_example SET A = 5;
```

<br/>

This means that all 3 of the above evaluate to this the lowercase equivalent:

```SQL
UPDATE my_example SET A = 5;
```

<br/>

The second is that if you wish to use camelCase, PascalCase you would need to wrap all identifiers in "Double Quotes".
So say you have a table that you've named "myExample" you would have to access it like this:

```SQL
UPDATE "myExample" SET A = 5;
```

<br/>

You can also double quote keywords if you wish to use them as identifiers, I do not recommend this as it can be both confusing and catastrophic.

It's worth noting that in some cases it may be useful to create views where you alias your identifiers to an alternate case. For example recently I've been using [Hasura](https://hasura.io/) in one of my projects and used this method so that when I consume my graphQL on the client it's in camelCase.
