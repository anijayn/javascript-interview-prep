# React Questions

## Fundamentals
### What is React?

React is an open-source JavaScript library developed by Facebook (now Meta) for building user interfaces. It's particularly effective for single-page applications where user interactions are frequent and dynamic content updates are necessary.

### What is DOM?

DOM (Document Object Model) is a programming interface for web documents. It represents the structure of HTML and XML documents as a tree of objects, where each object corresponds to a part of the document (like elements, attributes, and text).

The DOM provides a way for programs (particularly JavaScript) to:
- Access the structure of a web page
- Manipulate the content, structure, and style of the page

Key characteristics of the DOM:

- **Tree Structure**: The DOM represents documents as a hierarchical tree of nodes.
- **Live Object**: Changes to the DOM are reflected immediately in the browser's rendering.
- **Platform/Language-Independent**: The DOM is designed to be used with any programming language, though it's most commonly used with JavaScript in web browsers.

Example of DOM manipulation with JavaScript:

```javascript
// Creating a new element
const newParagraph = document.createElement('p');
newParagraph.textContent = 'This is a new paragraph.';

// Adding it to the document
document.body.appendChild(newParagraph);

// Modifying an existing element
const heading = document.querySelector('h1');
heading.style.color = 'blue';

// Removing an element
const elementToRemove = document.getElementById('old-element');
elementToRemove.parentNode.removeChild(elementToRemove);
```

### What are the features of React?

React comes with several powerful features that make it a popular choice for building modern web applications:

- **JSX (JavaScript XML)**: A syntax extension that allows writing HTML-like code in JavaScript, making component structure more readable and intuitive.

- **Virtual DOM**: React maintains a lightweight copy of the real DOM in memory, allowing it to compute differences and update only the necessary parts of the actual DOM, resulting in better performance.

- **One-way Data Binding**: Data flows in a single direction, from parent to child components, making applications more predictable and easier to debug.

- **Component-Based Architecture**: UI is broken down into independent, reusable components that maintain their own state, promoting code reusability and separation of concerns.

- **React Hooks**: Functions that let you use state and other React features in functional components without writing classes.

- **React Native**: Extends React's paradigm to mobile app development, allowing developers to use the same component concepts to build native mobile applications.

- **Large Ecosystem**: Rich ecosystem of libraries, tools, and extensions (Redux, React Router, Material-UI, etc.) that enhance React's capabilities.

- **Strong Community Support**: Backed by Facebook and a large community of developers, ensuring continuous improvements and resources.

- **Developer Tools**: Excellent developer tools for debugging and inspecting component hierarchies, props, and state.

### What is JSX?

JSX, or JavaScript XML, is a syntax extension for JavaScript that lets you write HTML-like code in JavaScript.

Key aspects of JSX:

- **HTML-like Syntax in JavaScript**: JSX allows you to write HTML structures directly in your JavaScript code.

```jsx
const element = <h1>Hello, world!</h1>;
```

- **Expressions in JSX**: You can embed JavaScript expressions within JSX by using curly braces.

```jsx
const name = 'John';
const element = <h1>Hello, {name}!</h1>;
```

- **JSX Attributes**: HTML attributes can be specified using either HTML attribute naming convention or camelCase (React's preferred style).

```jsx
// HTML style
const element = <div class="container">Content</div>;

// React style (preferred)
const element = <div className="container">Content</div>;
```

- **JSX Represents Objects**: JSX is transpiled to regular JavaScript function calls. The above examples are transformed into:

```javascript
// This is what JSX becomes after transpilation
const element = React.createElement('h1', null, 'Hello, world!');
```

- **JSX Prevents Injection Attacks**: React DOM escapes any values embedded in JSX before rendering them, helping to prevent cross-site scripting (XSS) attacks.

- **JSX is Not Required**: While JSX makes React code more readable and writable, it's not required. You can use React without JSX, but the code becomes more verbose:

```javascript
// With JSX
const element = (
  <button className="btn" onClick={handleClick}>
    Click me
  </button>
);

// Without JSX
const element = React.createElement(
  'button',
  { className: 'btn', onClick: handleClick },
  'Click me'
);
```

- **JSX Requires Transpilation**: Browsers don't understand JSX directly, so it needs to be transpiled to regular JavaScript using tools like Babel before being served to browsers.

### What is the DOM?
DOM (Document Object Model) is a programming interface for web documents. It represents the structure of HTML and XML documents as a tree of objects, where each object corresponds to a part of the document (like elements, attributes, and text).

The DOM provides a way for programs (particularly JavaScript) to:
- Access the structure of a web page
- Manipulate the content, structure, and style of the page

Key characteristics of the DOM:

- **Tree Structure**: The DOM represents documents as a hierarchical tree of nodes.
- **Live Object**: Changes to the DOM are reflected immediately in the browser's rendering.
- **Platform/Language-Independent**: The DOM is designed to be used with any programming language, though it's most commonly used with JavaScript in web browsers.

Example of DOM manipulation with JavaScript:

```javascript
// Creating a new element
const newParagraph = document.createElement('p');
newParagraph.textContent = 'This is a new paragraph.';

// Adding it to the document
document.body.appendChild(newParagraph);

// Modifying an existing element
const heading = document.querySelector('h1');
heading.style.color = 'blue';

// Removing an element
const elementToRemove = document.getElementById('old-element');
elementToRemove.parentNode.removeChild(elementToRemove);
```

### What is the virtual DOM?

The Virtual DOM is a programming concept where an ideal, or "virtual", representation of a UI is kept in memory (a lightweight JavaScript object that mirrors the structure of the actual DOM tree) and synced with the "real" DOM by a library such as ReactDOM.  This process is called reconciliation.


How the Virtual DOM works:

1. **Initial Render**: React creates a Virtual DOM tree from your components.
2. **State Change**: When state or props change, React creates a new Virtual DOM tree.
3. **Diffing**: React compares the new Virtual DOM with the previous one (diffing).
4. **Reconciliation**: React calculates the minimal set of changes needed to update the real DOM.
5. **Batch Update**: React applies all the necessary changes to the real DOM in a single batch.

Example of how Virtual DOM improves performance:

```jsx
function UserList({ users }) {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

If only one user's name changes in a list of 1000 users:
- Without Virtual DOM: The entire list might be re-rendered.
- With Virtual DOM: React identifies only the specific `<li>` element that changed and updates only that part of the real DOM.

### What are the differences between package.json and package-lock.json?
- package.json is the main configuration file for a Node.js project. It contains metadata about the project, including its name, version, dependencies, scripts, and more.
- package-lock.json is a file that records the exact version of each dependency that was installed in the node_modules directory. It is used to ensure that the same version of a dependency is installed across different environments.

### What are the differences between client-side and server-side rendering?

**Client-Side Rendering (CSR):**
- **Initial Load**: Slower, as the browser downloads and executes JavaScript.
- **Interactivity**: High, as updates happen without full page reloads.
- **SEO**: Challenging, as content is rendered on the client side.
- **Server Load**: Lower, as rendering is offloaded to the client's browser

**Server-Side Rendering (SSR):**
- **Initial Load**: Faster, as the server sends fully rendered HTML.
- **Interactivity**: Lower initially, but can be enhanced with JavaScript.
- **SEO**: Better, as content is rendered on the server.
- **Server Load**: Higher, as the server handles rendering for each request.

## Component Basics
### What is state in React?
he state object is where you store property values that belong to the component. When the state object changes, the component re-renders. It is managed within the component and can be updated using `setState` in class components or the `useState` hook in functional components.

### What are props?
Props is a special keyword in React that stands for properties and is used for passing data from one component to another. Data with props are passed in a unidirectional flow from parent to child.

### What are the differences between state and props in React?
- **State**: Managed within the component, mutable, used for dynamic data.
- **Props**: Passed from parent to child, immutable, used for passing data.

### What is the component lifecycle of a React class component?
The lifecycle includes:
- **Mounting**: `constructor()`, `componentDidMount()`
- **Updating**: `shouldComponentUpdate()`, `componentDidUpdate()`
- **Unmounting**: `componentWillUnmount()`

### What are fragments in React?
Fragments let you group multiple elements without adding extra nodes to the DOM. Use `<React.Fragment>` or the shorthand `<>`.

### What are keys in React?
Keys are unique identifiers for elements in a list, helping React identify which items have changed, are added, or removed. Example: `<li key={item.id}>`.

### What are synthetic events in React?
Synthetic events are React's cross-browser wrapper around the browser's native event system, providing a consistent API.

Example:
```jsx
function handleClick(e) {
  console.log(e.type); // Here e is the synthetic event
}
<button onClick={handleClick}>Click me</button>
```

### What are the differences between controlled and uncontrolled components?
- **Controlled**: 
    - The component is under control of the component’s state.
- **Uncontrolled**: 
    - Components are under the control of DOM.

### What is Strict Mode in React?
Strict Mode enables extra development-only checks for the entire component tree inside the <StrictMode> component. These checks help you find common bugs in your components early in the development process. To enable Strict Mode for your entire app, wrap your root component with <StrictMode>

## Component Communication
### What is props drilling?
Props drilling is a pattern where props are passed from a higher-level component to lower-level components, even if intermediate components don't need the props. It can make the code harder to maintain and is considered an anti-pattern.

Example:
```jsx
function ParentComponent() {
  const [value, setValue] = useState('');

  return (
    <ChildComponent value={value} setValue={setValue} />
  );
}

function ChildComponent({ value, setValue }) {
  return (
    <GrandChildComponent value={value} setValue={setValue} />
  );
}

function GrandChildComponent({ value, setValue }) {
  return (
    <input value={value} onChange={(e) => setValue(e.target.value)} />
  );
}
```
To avoid props drilling, you can use React Context or custom hooks for more complex scenarios.

### What are the disadvantages of props drilling, and how can we avoid it?
- **Complexity**: Passing props through multiple levels can make the code harder to read and maintain.
- **Coupling**: Intermediate components become dependent on the structure of the parent-child relationship.

### What is context in React?
Context provides a way to pass data through the component tree without having to pass props down manually at every level. It's useful for sharing data that is needed by many components at different levels of the component tree.

### Give an example of Context API usage.
Example of using the Context API to pass a theme to nested components:

```jsx
const ThemeContext = React.createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return (
    <ThemedButton />
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme }}>Click me</button>;
}
```

### What are the different ways to pass data from a child component to a parent component in React?
- **Callback Functions**: Pass a function as a prop from the parent to the child component, which the child can call to send data back.
- **UseRef**: Use the useRef hook to create a mutable object that persists across renders, allowing the child to update a value that the parent can access.
- **Context API**: If the parent and child components are not directly connected, you can use the Context API to share data between them.
- **State Management Libraries**: Use state management libraries like Redux or MobX to manage shared state across components.

### How to send data from child to parent using callback functions?
Example of passing a callback function from the parent to the child component:

```jsx
function ParentComponent() {
  const handleData = (data) => console.log(data);
  return <ChildComponent sendData={handleData} />
}

function ChildComponent({ sendData }) {
  const handleClick = () => sendData('Data from child');
  return <button onClick={handleClick}>Send Data</button>;
}
```

### How to send data from a child component to a parent using useRef?
Example of using useRef to send data from a child to a parent component:

```jsx
function ParentComponent() {
  const dataRef = useRef(null);
  const handleData = () => {
    console.log(dataRef.current);
  };
  return (
    <div>
      <ChildComponent dataRef={dataRef} />
      <button onClick={handleData}>Get Data from Child</button>
    </div>
  );
}

function ChildComponent({ dataRef }) {
  const handleClick = () => {
    dataRef.current = 'Data from child'; // Set data in the ref
  };
  return <button onClick={handleClick}>Send Data to Parent</button>;
}
```
Here we use a ref to store the data in the child component, which can be accessed by the parent component.

## Advanced Component Patterns
### What are pure components in React?

In React, pure components are components that render the same output given the same props and state. These components implement a shallow comparison for both props and state, and if there is no change, they will not re-render, making them more performant than regular components.

You can create a pure component by using React.PureComponent or by using React.memo for functional components.

Example with Class Component:
```jsx
class MyComponent extends React.PureComponent {
  render() {
    return <div>{this.props.text}</div>;
  }
}
```

Example with Functional Component:
```jsx
const MyComponent = React.memo(function MyComponent({ text }) {
  return <div>{text}</div>;
});
In both cases, React will avoid re-rendering the component if the text prop does not change.

### What are refs in React?
Refs (short for references) in React provide a way to interact with DOM elements or class component instances directly. They are used when you need to access or manipulate elements outside the React rendering cycle, such as:
- Managing focus, text selection, or media playback.
- Triggering imperative animations or integrating with third-party DOM libraries.
- Accessing child components to call methods or access their properties.
The useRef hook is commonly used to create refs in functional components, while the createRef method is used in class components. 
Using Refs in Class Components
```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.inputRef = React.createRef(); // Create a ref
  }
  focusInput = () => {
    this.inputRef.current.focus(); // Access the DOM element
  };
  render() {
    return (
      <div>
        <input type="text" ref={this.inputRef} />
        <button onClick={this.focusInput}>Focus Input</button>
      </div>
    );
  }
}
```

Using Refs in Functional Components
```jsx
function MyComponent() {
  const inputRef = useRef(null); // Create a ref
  const focusInput = () => {
    inputRef.current.focus(); // Access the DOM element
  };
  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}
```

### What is meant by forward ref?
Forwarding refs is a technique in React that allows a parent component to pass a ref to a child component. This is useful when you want to expose a child component's DOM element to its parent. By default, refs do not pass down to child components. To enable this behavior, React provides forwardRef.

```jsx
// Child component that receives the ref
const InputComponent = forwardRef((props, ref) => {
  return <input type="text" ref={ref} {...props} />;
});

function ParentComponent() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus(); // Access the input element in child
  };

  return (
    <div>
      <InputComponent ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}
```

### What are error boundaries?
Error boundaries are a feature in React that catches and handles errors while rendering the UI. They are just React components that:
1. Catch JavaScript errors in the child component tree.
2. Log those errors.
3. Display a fallback UI instead of crashing the entire component tree.
Error boundaries are just like the catch {} block in JavaScript, but for React components. They only catch errors in the components below them in the tree and do not catch errors in:
1. Event handlers
2. Asynchronous code
3. Server-side rendering
4. Errors thrown in the error boundary itself

To create an error boundary, you might need these two lifecycle methods:
1. static getDerivedStateFromError(error): This lifecycle method is used to render a fallback UI.
2. componentDidCatch(error, info): This lifecycle method is used to log the error information.

Here is a simple example of an Error boundary:
```jsx
class ErrorBoundary extends React.Component {
constructor(props){
    super(props);
    this.state ={hasError: false}
}
static getDerivedStateFromError(error){
    return {hasError: true} // Update state so the next render will show the fallback UI
}
componentDidCatch(error, info){
    console.log(error, info); // Logging the Error
}
render(){
    if(this.state.hasError) return <h1>Something has gone wrong.</h1>
    return this.props.children;
}
}
```
You would use it by wrapping components hat might error:
```jsx
<ErrorBoundary>
    <MyComponent />
</ErrorBoundary>
```

### What are higher-order components in React?
Higher Order Components in React are functions that take a component and return a new component with additional functionality. They follow this pattern:
```jsx
const EnhancedComponent = hocFunction(MyComponent);
```
Key characteristics:
1. Pure functions with no side effects
2. Return a new component that renders the original one with additional props/behavior
3. Don't modify the input component

Common uses:
1. Reusing component logic
2. Handling cross-cutting concerns like authentication, logging, etc.

Example of a Higher Order Component:
```jsx
function withLogger(Component) {
  return function(props) {
    console.log(`Rendering ${Component.name}`);
    return <Component {...props} />;
  };
}
```
Usage:
```jsx
const EnhancedComponent = withLogger(MyComponent);
```

### What are portals in React?
Portals in React provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. This allows you to render content at a different place in the DOM tree, such as modals, popovers, or tooltips.
To create a portal, you use the ReactDOM.createPortal() method, passing the child elements and the target container where the children should be rendered.
Example:
```jsx
function Modal({ children }) {
  return ReactDOM.createPortal(
    children,
    document.getElementById('modal-root')
  );
}
```
In this example, the children of the Modal component will be rendered inside the DOM element with the ID 'modal-root', which can be located anywhere in the HTML document.

## Hooks
### Which lifecycle hooks in class components are replaced with useEffect in functional components?
- **componentDidMount**: useEffect with an empty dependency array [].
- **componentDidUpdate**: useEffect with a dependency array containing the variables that trigger the update.
- **componentWillUnmount**: useEffect with a cleanup function returned from the effect.

### What is the purpose of a callback function as an argument of setState()?
The callback function passed to setState() is called after the state has been updated and the component has been re-rendered. It's useful when you need to perform some action after the state update is complete, such as logging, making API calls, or updating the DOM based on the new state.
Example:
```jsx
this.setState({ count: this.state.count + 1 }, () => {
  console.log('State updated:', this.state.count);
});
```

### What is useCallback?
useCallback is a hook in React that returns a memoized version of the callback function that only changes if one of the dependencies has changed. It's useful for optimizing performance by preventing unnecessary re-renders of components that rely on the callback function.
Example:
```jsx
export function UseCallBack() {
  const [count, setCount] = useState(0);
  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]); // Only recreate handleClick when count changes
  return (
    <div>
      <p>Count: {count}</p>
      <ChildComponent onClick={handleClick} />
    </div>
  );
}
function ChildComponent({ onClick }) {
  return <button onClick={onClick}>Increment</button>;
}
```
Here handleClick will only be recreated when the count state changes, preventing unnecessary re-renders of ChildComponent.

### What is useMemo?
useMemo is a hook in React that memoizes the result of a function so that the function is only re-executed when its dependencies change. It's useful for optimizing performance by avoiding expensive calculations on every render.
Example:
```jsx
export function UseMemo() {
  const [count, setCount] = useState(0);
  const expensiveCalculation = useMemo(() => {
    console.log('Calculating...');
    return count * 2;
  }, [count]); // Only re-run the calculation when count changes
  return (
    <div>
      <p>Count: {count}</p>
      <p>Result: {expensiveCalculation}</p>
    </div>
  );
}
```
In this example, the expensiveCalculation function will only be re-executed when the count state changes, preventing unnecessary recalculations.

### What are the differences between useMemo and useCallback?
- **useMemo**: 
    - Memoizes the result of a function and re-runs the function only when its dependencies change. Useful for optimizing performance by avoiding expensive calculations.
- **useCallback**: Memoizes a callback function and re-creates the function only when its dependencies change. Useful for optimizing performance by preventing unnecessary re-renders of components that rely on the callback function.

### What is the useReducer hook?
useReducer is a hook in React that is used for state management in complex components with multiple sub-values or when the next state depends on the previous one. It's similar to Redux, but it's built into React.
Example:
```jsx
import React, { useReducer } from "react";
// Reducer function
const reducer = (state, action) => {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: 0 };
  }
};
const Counter = () => {
  const initialState = { count: 0 };
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <div>
      <h1>{state.count}</h1>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
    </div>
  );
};
```

### What are custom hooks?
Custom hooks are JavaScript functions whose names start with "use" and can call other hooks. They allow you to extract and reuse logic across multiple components in a React application. Custom hooks can be used to:
- Share logic between components.
- Abstract complex logic into reusable functions.
- Keep components clean and focused on rendering UI.

### Create a custom hook for an increment/decrement counter.
```jsx
import { useState } from "react";
const useCounter = () => {
  const [count, setCount] = useState(0);
  return {
    count: count,
    increment: () => setCount(count + 1),
    decrement: () => setCount(count - 1),
    reset: () => setCount(0),
  };
};
export default useCounter;
```
Usage:
```jsx
import useCounter from "../hooks/useCounter";
const CounterHooked = () => {
  const { count, increment, decrement, reset } = useCounter();
  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={reset}>~</button>
    </div>
  );
};
export default CounterHooked;
```

## Performance Optimization
### What is lazy loading in React?
Lazy loading is a technique in React that allows you to load components only when they are needed, improving the initial loading time of the application. It's useful for optimizing performance by splitting the code into smaller chunks and loading them on demand.
React.Lazy() is a built-in function that lets you dynamically import components and render them only when they are needed. You can use it with Suspense to show a loading indicator while the component is being loaded.
Example:
```jsx
import React, { Suspense, lazy } from "react";
const HeavyComponent = lazy(() => import("./HeavyComponent"));
const LazyComponent: React.FC = () => {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <HeavyComponent />
    </Suspense>
  );
};
export default LazyComponent;
```

Lazy loading with routes:
```jsx
import React, { Suspense, lazy } from "react";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
const Home = lazy(() => import("./Home"));
const App: React.FC = () => {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route path="/" component={Home} />
        </Switch>
      </Suspense>
    </Router>
  );
};
export default App;
```
Here the Home component will be loaded only when the user navigates to the "/" route.

### What is suspense in React? 
Suspense is a React feature that allows components to suspend rendering while waiting for some asynchronous operation to complete, such as data fetching or lazy loading. It's useful for handling loading states and displaying fallback UIs while waiting for the data to be ready.
Suspense is typically used with React.lazy() for code-splitting and React.Suspense for handling loading states.
Example:
```jsx
import React, { Suspense } from "react";
const LazyComponent = React.lazy(() => import("./LazyComponent"));
const App = () => {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
};
export default App;
```
In this example, the "Loading..." message will be displayed while the LazyComponent is being loaded.

### Tools and techniques for debugging React applications
- **Breakpoints and the debugger statement**: Use breakpoints in the browser's developer tools or the debugger statement in your code to pause execution and inspect variables.
- **Error Boundaries**: Catch and handle errors in components using error boundaries.
- **React DevTools**: Browser extension for inspecting React component hierarchies, props, and state.
- **React Profiler**: Measure performance and identify slow components using the React Profiler tool.
- **React Strict Mode**: Enable Strict Mode to catch common mistakes and use development-only features.

### What is Hydration in Server-Side Rendering?
Hydration is the process of attaching event listeners and updating the DOM generated by the server-rendered HTML in a React application. It's necessary for React to take over the server-rendered content and make it interactive on the client side. During hydration, React compares the server-rendered HTML with the client-rendered virtual DOM and attaches event listeners to make the content interactive. This process ensures that the application remains functional and interactive after the initial server-side rendering.
