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

* **How and why is used useMemo?**
* **How and why is used useCallback?**
*   **How and why is used useState?**

    useState is a store that enables the use of state variables in functional components. You can pass the initial state to this function and it returns a variable containing the current state value and a function to update the value. It can be used as follows:

```jsx
const [count, setCount] = useState(0);
```

* **How and why is used useReducer?**
* **How and why is used useContext?**
* **How and why is used useRef?**
* **What are resource hooks?**
*   **What are custom hooks and why are they useful?**

    Custom hooks are functions to encapsulate and share reusable logic in functional components. Allows to abstract complex or repetitive logic into standalone functions that can be used across multiple components. Always start with the word _use_ followed by a capital letter. Custom hooks allow sharing stateful logic, not state itself, and can use built-in or custom hooks.
*

## **Context**



## Portals

* **What are portals?**

## Sources

* [https://www.freecodecamp.org/news/react-interview-questions-and-answers/](https://www.freecodecamp.org/news/react-interview-questions-and-answers/)
* [https://react.dev/reference/react](https://react.dev/reference/react)
