---
title: How to throw an exception in JavaScript
date: '2020-07-04T12:11:00.000Z'
description: 'Generating custom error messages using throw'
---

The `throw` statement allows you to throw your own custom exception. When it is thrown the statements that come after it won't be executed and control will be passed to the first `catch` block in the call stack. In JavaScript, all exceptions are just objects which means we can throw pretty much anything. Here's a simple example with a string:

```javascript
throw 'Invalid email supplied for user'
```

<br/>

And here's a simple example where we're throwing an object:

```javascript
function UserException(message) {
  this.message = message
  this.name = 'UserException'
}

throw new UserException('Invalid email supplied for user')

throw new UserException('Invalid phone number supplied for user)

```

<br/>

Because our `UserException` is just an object it's also possible to modify it to include metadata that would help us with debugging such as the offending variable.

```javascript
function UserException(message, invalid) {
  this.message = message
  this.invalid = invalid
  this.name = 'UserException'
}

throw new UserException('Invalid email supplied for user', user.email)

throw new UserException('Invalid phone number supplied for user', user.phone)
```

<br/>

This metadata can then be accessed when we catch our exception and either logged or shown to the user.
