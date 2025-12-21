---
title: react fiber
date: 2023-01-12
tags: ["react.js"]
subtitle: react fiber is a game-changing addition to react, designed to boost performance by optimizing the rendering process.
coverImage: "react-fiber.webp"
draft: false
category: "software engineering"
---

# An Overview of Fiber Trees and Reconciliation

![blog image](react-fiber.webp)

## Unlocking the Power of Web Scraping for Data Collection and Analysis

React Fiber is a revolutionary feature in the React library that aims to significantly enhance the performance and rendering efficiency of React applications.
At the heart of Fiber lies the reconciliation process, a powerful mechanism that efficiently updates the user interface based on changes in application state.
In this blog, we will delve into the concept of Fiber trees and explore how the reconciliation process works.

## Reconciliation Stack

Before the release of React 16, React employed a stack-based reconciliation algorithm known as the "stack reconciler" to compare the old and new virtual trees
and update the DOM accordingly. While suitable for simpler scenarios, the stack reconciler faced challenges as applications grew in complexity.

The synchronous nature of the stack reconciler caused updates to block the main thread, leading to janky and unresponsive user interfaces, especially with large
virtual trees or slower devices. Additionally, changes to the virtual tree were delayed until the reconciler completed its work, affecting overall performance
and responsiveness.

## The Fiber Reconciler

To address these challenges and improve React's performance, React 16 introduced the Fiber reconciler, a complete rewrite of the previous stack-based algorithm
with several significant benefits.

## How React Fiber Works

When a React application undergoes an update triggered by user interactions or events, the reconciliation process is initiated. Its goal is to efficiently
determine the parts of the user interface that require updating and apply these changes to the real DOM.

## _Fiber Trees - Current and Work in Progress_

The reconciliation process involves two sets of virtual DOM trees: the "current" tree and the "work in progress" tree, also known as the Fiber tree. The
"current" tree represents the existing state of the virtual DOM, while the "work in progress" tree is a replica that incorporates the updates to be performed.

## Render Phase

The reconciliation process begins with the render phase, where React traverses the component tree and creates fiber nodes, special data structures representing
different portions of the virtual DOM.

During the render phase, React compares the fiber nodes in the "current" and "work in progress" trees to identify parts of the virtual DOM requiring updates.
Leveraging a work loop, React breaks rendering work into smaller units that can be interrupted and resumed, prioritizing important updates to maintain a
responsive user interface.

## Commit Phase

After completing the render phase and applying the necessary updates to the "work in progress" tree, React enters the commit phase. Here, React takes the
updates from the "work in progress" tree and applies them to the real DOM, making the changes visible to users.

React optimizes the performance by batching updates during the commit phase, reducing unnecessary reflows and repaints for a smoother user experience.

## A New Horizon for Concurrency and Batching

React Fiber, the new reconciliation architecture introduced in React 16, not only improves rendering efficiency but also unlocks powerful features for
concurrency and batching. This allows React to break free from the limitations of synchronous updates and enables the library to handle complex user
interactions more intelligently.

| Concurrency and Batching

In traditional synchronous rendering, React updates the entire component tree before reflecting changes in the real DOM. This approach can lead to unnecessary
processing, causing performance bottlenecks and affecting user experience. React Fiber introduces the concept of concurrency, which enables asynchronous
rendering and prioritization of tasks.

With concurrency, React can pause, resume, or abort rendering work as needed, and even divide the rendering process into smaller, more manageable chunks. This
fine-grained control empowers React to prioritize essential updates and respond faster to user interactions, making the user interface feel more responsive and
fluid

## New Functionality in React Fiber

To leverage the benefits of concurrency and batching, React introduces several new functionalities:

```js
useDeferredValue;
```

The useDeferredValue hook allows developers to defer the processing of non-essential updates, optimizing performance by prioritizing high-priority work. For
example, in a search input, we may want to defer the rendering of search results until the user pauses typing. This way, React can focus on more critical tasks
like handling user input, ensuring a smoother experience.

```javascript
import { useDeferredValue } from "react";

const Search = () => {
    const [query, setQuery] = useState("");

    // Defer the processing of non-essential updates
    const deferredQuery = useDeferredValue(query);

    const handleChange = (e) => {
        setQuery(e.target.value);
    };

    // Rest of the component logic
};
```

```js
useTransition;
```

The useTransition hook allows developers to create smoother transitions during rendering updates. It helps to manage complex interactions by defining specific
points in the rendering process where React should wait for a transition to complete before displaying the changes.

```javascript
import { useTransition, useEffect, useState } from "react";

const ExpensiveComponent = () => {
    const [isPending, startTransition] = useTransition();

    // Simulate a time-consuming rendering process
    useEffect(() => {
        startTransition(() => {
            // Code to render the expensive component
        });
    }, []);

    if (isPending) {
        return <p>Loading...</p>;
    }

    // Return the fully rendered component
    return <div>Expensive Component Content</div>;
};
```

## Suspense Component

The Suspense component is a powerful tool that allows developers to handle loading states and fallback UIs in an elegant and straightforward manner. It is
especially useful when dealing with asynchronous data fetching or code-splitting.

```javascript
import { Suspense } from "react";

const MyComponent = () => {
    return (
        <Suspense fallback={<p>Loading...</p>}>
            {/* Asynchronously load and render the lazy component */}
            <LazyComponent />
        </Suspense>
    );
};
```

## Conclusion

React Fiber's reconciliation process, powered by the concept of Fiber trees, plays a pivotal role in driving React's remarkable performance. By intelligently
managing virtual DOM updates and efficiently applying them to the real DOM, React ensures that user interfaces remain snappy and responsive, making React a
popular and powerful choice for building modern web applications. The introduction of React Fiber marks a significant milestone in React's evolution, paving the
way for even more efficient and responsive applications.

Thanks for reading ❤️
