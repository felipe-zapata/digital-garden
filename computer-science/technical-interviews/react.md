# React

## General

* **Is react a library or a framework?**
* **What type of data binding react uses?**
* **What is the virtual DOM and why is it useful?**
* **What is the difference between virtual DOM and shadow DOM?**
* **What are the advantages of React?**
* **What are the disadvantages of React?**
* **What is JSX?**
* **What is a functional component?**
* **What is a class component?**
* **What are props?**
*   **How to pass parameters to an event handler?**

    We could add an anonymous arrow function to call the event handler passing the parameter. Like:

```jsx
return (
   <div>
      <button onClick={() => handleClick('John Doe')}>Click Me</button>
   </div>
)
```

* **Why is the key prop needed on a rendered list?**
* **What memo does?**

## Hooks

*   **What are hooks and what are the most commonly used?**

    Hooks are a way to allow functional components to have a state (and other features) without writing a class.
* **What are the rules of hooks?**
  * Only call hooks at the top level.
  * Only call hooks from react functions
*   **How and why is used useEffect?**

    useEffect hooks allow to perform side effects in the components, like data fetching, DOM updates, timers, etc. This hook accepts two arguments, setup function and dependencies. The dependencies allow control when the setup function is executed. The setup function may also optionally return a cleanup function. After every re-render with changed dependencies, React will first run the cleanup function (if you provided it) with the old values, and then run your setup function with the new values. After your component is removed from the DOM, React will run your cleanup function. If there are no dependencies, the useEffect will re-run the setup function after every re-render of the component. If an empty array is passed as a second parameter the setup function will only run after the initial render.
* **How does the useEffect hook could act as the previous lifecycle methods?**

```jsx
// componentDidMount

useEffect(() => {
  // Inside this callback function we perform our side effects.
});

// componentDidUpdate

useEffect(() => {
  // Inside this callback function we perform our side effects.
}, [dependency]);

// componentWillUnmount

useEffect(() => {
  window.addEventListener("mousemove", () => {});
  return () => {
    window.removeEventListener("mousemove", () => {})
  }
}, []);
```

*   **Are there variations of useEffect?**

    Yes, _useLayoutEffect_ (fires before the browser repaints the screen, you can measure layout here) and _useInsertionEffect_ (fires before React makes changes to the DOM, libraries can insert dynamic CSS here).&#x20;
*   **How and why is used useMemo?**

    Is used to skip calculations and unnecessary re-rendering. _useMemo_ lets you cache the result of an expensive calculation. React will call the function on the first parameter on the first render , and on the following renders only if the dependencies have changed since the last execution. Caching return values like this is also known as _memoization_, which is why this Hooks is called _useMemo_.\
    \
    How to use it?

```jsx
function TodoList({ todos, tab }) {
  const visibleTodos = useMemo(
    () => filterTodos(todos, tab), // Calculate value, pure function without arguments
    [todos, tab] // Dependencies
  );
  // ...
}
```

*   **How and why is used useCallback?**

    Is used to skip calculations and unnecessary re-rendering. _useCallback_ lets you cache a function definition before passing it down to an optimized component. React will return (not call) your function back to you during the initial render. On next renders, React will give you the same function again if the dependencies have not changed since the last render. Otherwise, it will give you the function that you have passed during the current render, and store it in case it can be reused later. It can be used in tandem with _memo_ to avoid re-renders.\
    \
    How to use it?

```jsx
import { useCallback } from 'react';

function ProductPage({ productId, referrer, theme }) {
  const handleSubmit = useCallback((orderDetails) => { 
    // First parameter is the function
    post('/product/' + productId + '/buy', {
      referrer,
      orderDetails,
    });
  }, [productId, referrer]); // Dependencies
  // ...
```

* **Are there any other performance-focused hooks?**
  * **useTransition:** Lets you mark a state transition as non-blocking and allow other updates to interrupt it. It returns an array with two items, the _isPending_ flag that tells you whether there is a pending transition, and the _startTransition_ function that lets you mark a state update as a transition. Useful for transitions like tab changes.
  * **useDeferredValue:** Lets you defer updating a non-critical part of the UI and let other parts update first. During the initial render, the returned deferred value will be the same as the value you provided. During updates, React will first attempt a re-render with the old value (so it will return the old value), and then try another re-render in the background with the new value (so it will return the updated value). Useful for loading pages. Eg.

```jsx
import { useState, useDeferredValue } from 'react';

function SearchPage() {
  const [query, setQuery] = useState('');
  const deferredQuery = useDeferredValue(query);
  // ...
}
```

*   **How and why is used useState?**

    useState is a store that enables the use of state variables in functional components. It's a great way to manage small amounts of state that only affects a single component.\
    You can pass the initial state to this function and it returns a variable containing the current state value and a function to update the value. It can be used as follows:

```jsx
const [count, setCount] = useState(0);
```

*   **How and why is used useReducer?**

    useReducer is designed to handle complex state logic that may require multiple actions to be performed on the state. Can be used to manage state across multiple components. It can be combined with useContext to provide a powerful solution for state management that can be used across an entire application.\
    \
    Differences with Redux:\
    \- useReducer is easier to implement than Redux.\
    \- Redux provides global state management across multiple components by storing all of its data in a single store object - rather than individual components like useReducer does.\
    \- Redux ensures immutability when manipulating data.\
    \- Redux is better for larger projects or systems with complex states given its default capabilities.\
    \
    You can use it the following way:

```jsx
const initialState = { count: 0 }

// Reducer is a reducer function like
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 }
    case 'decrement':
      return { count: state.count - 1 }
    default:
      throw new Error()
  }
}

const [state, dispatch] = useReducer(reducer, initialState)
```

*   **How and why is used useContext?**

    Context lets a component receive information from distant parents without passing it as props. The useContext hook allows reading and subscription to a context. We can use Context to pass an object to set multiple values. \
    \
    In larger apps, it is common to combine context with a reducer to extract the logic related to some state out of components. We can see an example [here](https://react.dev/learn/scaling-up-with-reducer-and-context).\
    \
    What is the usage?

```jsx
// To create and use a context

const ThemeContext = createContext(null);

export default function MyApp() {
  return (
    <ThemeContext.Provider value="dark">
      <Form />
    </ThemeContext.Provider>
  )
}

// To subscribe to a context

function Panel({ title, children }) {
  const theme = useContext(ThemeContext); // Theme is going to have value "dark"
}

// To update data passed via context we have to use a state

function MyPage() {
  const [theme, setTheme] = useState('dark');
  return (
    <ThemeContext.Provider value={theme}>
      <Form />
      <Button onClick={() => {
        setTheme('light');
      }}>
        Switch to light theme
      </Button>
    </ThemeContext.Provider>
  );
}

```

*   **How and why is used useRef?**

    _Refs_ let a component hold some information that isn't used for rendering, like a DOM node or a timeout ID. Updating a ref does not re-render your component. Refs are useful when you need to work with non-React systems, such as the built-in browser APIs. \
    \
    Do not write or read _ref.current_ during rendering. React expects that the body of your component behaves like a pure function. You should put it on a useEffect or in an event handler.\
    \
    How can you use it?

```jsx
import { useRef } from 'react';

function MyComponent() {
  const intervalRef = useRef(0); // Passing an initial value
  const inputRef = useRef(null);
  // ...
  
  useEffect(() => {
    const intervalId = setInterval(() => {
      // ...
    }, 1000);
    intervalRef.current = intervalId;
  }, []);
  
  // ...
  return <input ref={inputRef} />;
```

* **What are resource hooks?**
*   **What are custom hooks and why are they useful?**

    Custom hooks are functions to encapsulate and share reusable logic in functional components. Allows to abstract complex or repetitive logic into standalone functions that can be used across multiple components. Always start with the word _use_ followed by a capital letter. Custom hooks allow sharing stateful logic, not state itself, and can use built-in or custom hooks.
*

## **Context**



## Portals

* **What are portals?**

## Redux

* **What are the differences between useReducer and Redux?**
  * **State management complexity:** _Redux_ has more powerful features for handling complex state management, such as middleware and the ability to combine reducers.
  * **Scalability:** Redux can be easier to maintain and modify as your application grows and evolves.
  * **Performance:** In most cases, _useReducer_ will have better performance than similar third-party state management libraries. _useReducer_ allows for more granular updates of state, avoiding unnecessary re-renders. _Redux_ requires more overhead to manage its state, such as creating a store and dispatching actions. _Redux_ has selectors to prevent unnecessary re-renders by allowing components to subscribe only to specific parts of the _Redux_ store.
  * **Ecosystem:** Redux has a larger ecosystem of tools and libraries that can be used alongside it, like middleware and dev tools.
* **What are the hooks used for interacting with data on Redux?**

## Sources

* [https://www.freecodecamp.org/news/react-interview-questions-and-answers/](https://www.freecodecamp.org/news/react-interview-questions-and-answers/)
* [https://react.dev/reference/react](https://react.dev/reference/react)
* [https://www.frontendmag.com/tutorials/usereducer-vs-redux/](https://www.frontendmag.com/tutorials/usereducer-vs-redux/)
