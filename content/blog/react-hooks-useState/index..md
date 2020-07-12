---
title: 'React Hooks: UseState'
date: '2020-07-11T11:06:00.000Z'
description: 'Consistent, easy and automatic code formatting for you and your team'
---

The `useState` hook allows you to manage the state of your React component without having to write a class. Here's a simple class based example that we're going to convert to it's functional equivalent with `useState`:

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      currentCount: 0
    };
  }

  render() {
      return (
          <div>
            <p>Current Count: {this.state.currentCount}</p>
            <button onClick={() => this.setState({ currentCount: this.state.currentCount + 1 })}>
                Increment Counter
            </button>
          <div>)
  }
```

<br/>

When we convert this to a functional component it will look something like this:

```jsx
import React, { useState } from 'react';

const Counter = () => {
    const [currentCount, setCurrentCount] = useState(0);

    return (
        <div>
            <p>Current Count: {currentCount}</p>
            <button onClick={() => setCurrentCount(currentCount + 1)}>
                Increment Counter
            </button>
          <div>
    )
}
```

<br/>

There's quite a big difference between these two components. First of all the way in which we declare our state is different. In our class we are handling this within the constructor but in our functional component we no longer have a constructor. So instead use our `useState` hook to both declare and initialize our state.

When it comes to accessing and updating our state we handle this through the two `const` variables declared within the square brackets. The first which we've called `currentCount` is the equivalent of `this.state.currentCount` in the class component and is used for reading state. The second which we've called `setCurrentCount` is used to update our state.

What if we were to have multiple state values to manage? Well in our class component we would just add another value to our state object and manage it through `this.state` and `this.setState`. However in our functional component we would just initialize another instance of our hook. Here's a quick example of what that might look like:

```jsx
import React, { useState } from 'react';

const DoubleCounter = () => {
    const [countOne, setCountOne] = useState(0);
    const [countTwo, setCountTwo] = useState(0);

    return (
        <div>
            <p>Count One: {countOne}</p>
            <p>Count Two: {countTwo}</p>
            <button onClick={() => setCountOne(countOne + 1)}>
                Increment Count One
            </button>
            <button onClick={() => setCountTwo(countTwo + 1)}>
                Increment Count Two
            </button>
          <div>
    )
}
```

</br>
