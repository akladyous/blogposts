---
title: batching in react
date: 2023-06-24
pubDate: 2023-06-24
tags: ["react.js", "concurrency"]
description: Discover React's Batching, Enhancing UI Performance with Update Batching.
---

# Optimizing UI Updates for Performance

![Alt text](/images/batching-in-react.png)

# Introduction

React is known for its efficient rendering process, and one of the key techniques it utilizes is batching. Batching refers to the process of combining multiple
updates into a single update, minimizing the number of times the real DOM needs to be updated..

In this article, we will explore how batching works under the hood in React and its impact on performance. We will also provide examples to demonstrate the
concept.

# Understanding Batching

When React renders a component, it doesn’t immediately apply every change to the real DOM. Instead, it batches the updates together and performs them all at
once, resulting in better performance and a smoother user experience. React achieves batching through a technique called “transaction,” which groups related
operations and executes them as a single unit of work.

| Example: Updating State with Batching:

Let’s consider an example where a component updates its state multiple times in quick succession. Without batching, React would update the real DOM for each
state change separately, even if the actual value changed only once. This approach would be inefficient.

However, due to batching, React combines these updates into a single transaction. As a result, the real DOM is updated only once after all the state changes
have been processed. This reduces unnecessary DOM updates and improves performance.

To demonstrate this, let’s modify the example code to log the current transaction state:

```js
import React from "react";

function Example() {
    const [count, setCount] = useState(0);

    const handleClick = () => {
        console.log("before ", React.__SECRET_INTERNALS_DO_NOT_USE_OR_YOU_WILL_BE_FIRED.ReactCurrentOwner.currentDispatcher);
        setCount(count + 1);
        setCount(count + 1);
        setCount(count + 1);

        console.log("after ", React.__SECRET_INTERNALS_DO_NOT_USE_OR_YOU_WILL_BE_FIRED.ReactCurrentOwner.currentDispatcher);
    };

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={handleClick}>Increment</button>
        </div>
    );
}
```

In this modified example, we log the current transaction state before and after the state updates. By observing the logs, we can see that React batches the
updates together into a single transaction.

Common Pitfall: Event Handlers and Batching: React’s batching behavior can sometimes lead to confusion, especially when dealing with event handlers. Consider an
example where a component updates its state and logs the count immediately after the state update. Due to batching, the logged count will always be one less
than the actual value at that moment.

This happens because React schedules a batch of updates to the real DOM, deferring the actual application of changes. Therefore, when the log statement is
executed, the state update might not have been processed yet.

## Fiber Architecture and Incremental Updates

React Fiber, introduced in React 16, is a re-implemented rendering engine that offers enhanced efficiency and flexibility. It introduces incremental updates to
the virtual DOM, enabling the browser to handle user input and other events without blocking the UI.

With React Fiber, updates are broken down into smaller chunks, allowing for prioritization and interleaving of different tasks. This approach enhances
responsiveness and ensures that the user interface remains interactive even during intense rendering processes.

## Conclusion

Batching is a fundamental mechanism in React that optimizes UI updates for improved performance. By combining multiple updates into a single transaction, React
minimizes the number of DOM manipulations and delivers a smoother user experience. Understanding batching and its impact on event handling and performance is
crucial for developing efficient React applications.

In this article, we discussed the concept of batching in React, its implementation through transactions, and its benefits in terms of performance. We provided
examples to illustrate how batching works and explained the significance of React Fiber’s incremental updates. By leveraging batching effectively, developers
can build highly performant and responsive React applications.

[For a Deeper Dive, Check the Original Post 🔗](https://medium.com/@akladyous/batching-in-react-cc0c323b3a1c)

Thank you for reading! ❤️
