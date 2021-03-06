# Notes

- `classname` attributes reflects the standard `class` attribute in HTML
- element is a plain object describing a component instance or DOM node and its desired properties
    - an element is an immutable description object with two fields: `type: (string | ReactClass)` and `props: Object`
- When `ReactDOM.render()` is called, React starts a process called reconciliation which will gradually "refine" its understanding of the component tree in terms of simple primitives (objects)
    - React will ask each element with a function or class type what element it is referring to and will repeat this process for each nested component

### ReactDOM
`ReactDOM.render()` uses a DOM node in the HTML to replace it with JSX, takes two arguments: the first is either JSX syntax, a React component, or an entire application, the second argument specifies where in te HTML the React application hooks into the HTML

### Immutability with React.js
[Immutability in React/JS](https://daveceddia.com/react-redux-immutability-guide/#react-prefers-immutability)

- React elements are immutable, onece you create an element, you can't change its children or attributes. 
- React only updates when it's necessary
    - React DOM compares the element and its children to the previous one, and only applies the DOm updates necessary to bring the DOM to the desired state


Components can be tuned for performance by inheriting from `React.PureComponent` or manually by implementing `shouldComponentUpdate`, PureComponents only update when `this.state`  or its props have changed 
In React, to modify state always use `this.setState` otherwise with PureComponents, the change in state may not be registered and the component may not rerender
Pros 
- Data changes are more explicit
- Data changes leave a paper trail of previous state of data
- Predictability with data changes with pure functions
- Swapping old object references with new object references is optimized by Javascripts -> performant
Cons
- Less performant than a mutable approach with small datasets

### Random notes 
- Any time you change component state, the `render()` method of your component will run again

- React has **unidirectional data flow**. Components initialize the state which is used in rendering the View, state can then be changed by using the setState method which alters the state.

- **Binding** - class methods don't automatically bind `this` to the class instance. If you want to access `this`/`this.state` in your class method, you have to bind your class methods to `this` in the component constructor.
    i.e. (in the Component constructor)
``` this.myMethod = this.myMethod.bind(this)```

- Use ****higher order functions** with event handlers to pass arguments to the function that is handling the event

- Use **synthetic events** in React to access event payloads  

- **ES6 destructuring**:  
```
const user = {
    firstname: 'Robin',
    lastname: 'Wieruch',
};
const { firstname, lastname } = user;
console.log(firstname + ' '  + lastname)
```

- **Controlled components**

- Use functional stateless components when you don't need local state or component lifecycle methods

- **ES6 spread operator** allows you to copy every value from an array or object to a new array or object, i.e.:
``` 
const userNames = { firstname: 'John', lastname: 'Smith' };
const userAge = { age: 28 };
const user = {...userNames, ...userAge };
```


#### Lifecycle methods
- React mounting process has 4 lifecycle methods which are invoked in the following order:  
`constructor(props)` -- Called when component gets initialized; set inital component state and bind class methods  
`componentwillMount()`  
`render()` -- Mandatory lifecycle method and returns the elements as an output of the component; should not modify component state  
`componentDidMount()` -- Called only once when the component gets mounted; good time to do an asynchronous request to fetch data  

- When state or the props change for a component the following methods are invoked:  
`componentWillReceiveProps(nextProps)` -- Called during an update lifecycle, as input you get the next props which can be diff'd with the previous props  
`shouldComponentUpdate()` -- Always called when the compoent updates due to state or prop changes; used for performance optimizations  
`render()`  
`componentDidUpdate(prevProps, prevState)` -- Invoked right after `render()` is called; usually used to perform DOM operations or to perform further asynchronous requests

- Called before you destroy your component  
`componentWillUnmount()`

- `componentDidCatch(error, into)` -- used to catch errors in components



