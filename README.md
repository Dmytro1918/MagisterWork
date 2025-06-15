# REACT-PQM

Welcome to REACT-PQM, a powerful tool designed to optimize the rendering performance of React applications by implementing a Priority Queue Manager (PQM). This utility helps reduce unnecessary re-renders, prioritize component updates based on visibility and importance, and provide detailed performance metrics. Built with TypeScript and React, this project is ideal for developers looking to enhance the efficiency of complex React-based web applications.

**Last Updated:** June 15, 2025
**Author:** Dmytro Kamenev
**Affiliation:** Kharkiv National University of Radio Electronics
**License:** MIT

---

## Table of Contents

* [Overview](#overview)
* [Features](#features)
* [Installation](#installation)
* [Usage](#usage)
* [API Documentation](#api-documentation)
* [Performance Metrics](#performance-metrics)
* [Contributing](#contributing)
* [License](#license)
* [Acknowledgments](#acknowledgments)
* [Contact](#contact)

---

## Overview

REACT-PQM addresses the common challenge of excessive re-rendering in React applications, which can degrade performance, especially in projects with numerous components. By leveraging a priority queue system integrated with React's rendering lifecycle, PQM intelligently manages when and how components are updated. It uses the IntersectionObserver API to detect component visibility and optimizes rendering based on priority levels, reducing resource usage and improving user experience.

This project was developed as part of a master's thesis at Kharkiv National University of Radio Electronics, focusing on researching rendering issues in React frameworks and proposing effective solutions.

## Features

* **Dynamic Priority Management:** Assign priorities to components and update them based on visibility and importance.
* **Visibility Tracking:** Utilizes IntersectionObserver to detect when components enter or leave the viewport.
* **Performance Monitoring:** Tracks rendering time, render count, and memory usage with detailed metrics.
* **Integration with React DevTools:** Provides optional notifications to React Developer Tools for debugging (if installed).
* **TypeScript Support:** Fully typed codebase for better developer experience and maintainability.
* **Customizable:** Allows adjustment of priority levels and component configurations.

## Installation

To get started with REACT-PQM, follow these steps:

### Clone the Repository:

```bash
git clone [https://github.com/yourusername/react-pqm.git](https://github.com/yourusername/react-pqm.git)
cd react-pqm
```

Install Dependencies:
Ensure you have Node.js (>=18.0) and npm installed. Then run:
```bash
npm install
```

Set Up Environment:
No additional environment variables are required, but ensure a modern browser (Chrome, Firefox, Edge) is available for testing.
Optionally, install the React Developer Tools extension for enhanced debugging.

Start the Development Server:
```bash
npm start
```

Usage
Example: Optimizing a Component
Here’s a basic example of how to integrate PQM into a React component:
```bash
import React, { useRef } from 'react';
import { usePQMComponent, logMetrics } from './pqm';

const MyComponent = () => {
  const ref = useRef<HTMLDivElement>(null); // Explicitly type the ref
  usePQMComponent('my-component', 10, () => {
    // Component rendering logic
    console.log('Rendering MyComponent');
  }, ref); // Pass the ref to usePQMComponent

  return <div ref={ref}>This is an optimized component!</div>;
};

export default MyComponent;
```

Note: I've slightly adjusted usePQMComponent usage in the example above. If your usePQMComponent hook takes the ref as a separate argument, ensure the example matches your actual implementation. If it returns the ref, then the original example was correct.

Steps:
        Import the usePQMComponent hook and pass a unique id, priority (lower value = higher priority), and a renderFn callback.
        Use the returned ref to attach the hook to your component.
        Call logMetrics() to view performance metrics in the console.

        
Testing with Many Components
The included AppWithManyForms.tsx demonstrates a scenario with 50 components. Run the app and observe the optimization in action:
        Open the browser console to see real-time metrics.
        Adjust component priorities in the code to experiment with different configurations.
        API Documentation
        usePQMComponent(id: string, priority: number, renderFn: () => void, ref: React.RefObject<HTMLElement>): void
        Description: A custom hook to integrate a component with the PQM system.


Parameters:
        id: A unique identifier for the component.
        priority: A number indicating the rendering priority (0-100, lower is higher priority).
        renderFn: A function to execute when the component is rendered.
        ref: A React.RefObject<HTMLElement> to attach to the component's DOM element for visibility tracking.
        Returns: Void (the hook manages the component's lifecycle and rendering internally).
        Note: I've adjusted the usePQMComponent signature here to include the ref as a parameter and changed the return type to void, based on common patterns for hooks that manage an external ref. If your hook returns the ref, please adjust this section accordingly.
        useViewportObserver(ref: React.RefObject<HTMLElement | null>): boolean


Description: 
        A hook to track the visibility of a component using IntersectionObserver.

Parameters:
        ref: A reference to the DOM element to observe.
        Returns: A boolean indicating whether the component is visible.
        logMetrics(unit?: MemoryUnit = 'MB'): void
        Description: Logs performance metrics to the console.


Parameters:
unit: The memory unit for reporting ('MB', 'KB', or 'Bytes', default is 'MB').
Returns: Void (logs to console).
pqm.getMetrics(): Record<string, Metrics>
Description: Retrieves the current performance metrics for all tracked components.
Returns: An object mapping component IDs to their metrics.


Performance Metrics
REACT-PQM provides the following metrics for each component:
        renderTime: Time taken to render the component (in milliseconds).
        renderCount: Number of times the component has been rendered.
        memoryUsed: Estimated memory usage (in the specified unit, if performance.memory is available).
        

Example output:
```bash
[PQM Metrics (MB)] {
  "my-component": { renderTime: 12.5, renderCount: 3, memoryUsed: 0.015 }
}
```


Reporting Issues
If you encounter bugs or have feature requests, please open an issue on the GitHub Issues page.

License
This project is licensed under the MIT License. Feel free to use, modify, and distribute it as per the license terms.

Acknowledgments
Kharkiv National University of Radio Electronics: For supporting the development of this project as part of a master's thesis.
React Community: For providing the robust ecosystem that made this optimization possible.
Open Source Contributors: For tools like TypeScript and IntersectionObserver.

Contact
Author: Dmytro Kameniev

Email: kamenevdv1997@gmail.com
