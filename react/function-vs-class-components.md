# Function vs class components

In the world of React, there are two ways of writing a React component. One uses a function and the other uses a class.

### Rendering JSX

 The clear difference is the syntax. Just like in their names, a functional component is just a plain JavaScript function that returns JSX. A class component is a JavaScript class that extends `React.Component` which has a render method.

```text
import React from "react";
 
const FunctionalComponent = () => {
 return <h1>Hello, world</h1>;
};
```

VS

```text
import React from "react";

class ClassComponent extends React.Component {
 render() {
   return <h1>Hello, world</h1>;
 }
}
```

### Passing props

```text
<Component name="Robert" />
```

Inside a functional component, we are passing props as an argument of the function.

```text
const FunctionalComponent = ({ name }) => {
 return <h1>Hello, {name}</h1>;
};
```

Inside a class, you need to use `this` to refer to props.

```text
class ClassComponent extends React.Component {
  render() {
    const { name } = this.props;
    return <h1>Hello, { name }</h1>;
 }
}
```

### Handling state

 To use state variables in a functional component, we need to use `useState` Hook, which takes an argument of initial state. 

```text
const FunctionalComponent = () => {
 const [count, setCount] = React.useState(0);

 return (
   <div>
     <p>count: {count}</p>
     <button onClick={() => setCount(count + 1)}>Click</button>
   </div>
 );
};
```

Class component handles state a bit differently. We define the constructor first. Inside the constructor, you will make a state object with a state key and initial value. And inside JSX, we use `this.state.count` to access the value of the state key we defined in the  constructor to display the count. 

```text
class ClassComponent extends React.Component {
 constructor(props) {
   super(props);
   this.state = {
     count: 0
   };
 }

 render() {
   return (
     <div>
       <p>count: {this.state.count} times</p>
       <button onClick={() => this.setState({ count: this.state.count + 1 })}>
         Click
       </button>
     </div>
   );
 }
}
```

### Lifecycle Methods

#### On Mounting \(componentDidMount\)

 The lifecycle method `componentDidMount` is called right after the first render completes.

```text
const FunctionalComponent = () => {
 React.useEffect(() => {
   console.log("Hello");
 }, []);
 return <h1>Hello, World</h1>;
};
```

 Replacing `componentDidMount`, We use the `useEffect` hook with the second argument of `[]`. The second argument of the `useEffect` hook is normally an array of a state\(s\) that changes, and `useEffect` will be only called on these selected changes. But when it’s an empty array like this example, it will be called once on mounting. This is a perfect replacement for a `componentDidMount`.

```text
class ClassComponent extends React.Component {
 componentDidMount() {
   console.log("Hello");
 }

 render() {
   return <h1>Hello, World</h1>;
 }
}
```

 `componentDidMount` is a lifecycle method that is called once after the first render.

#### On Unmounting \(componentWillUnmount\)

 we can also use a `useEffect` hook for unmounting as well. What you need to do is return a function that runs on unmounting inside the `useEffect` function. This is especially useful when you have to clean up the subscriptions such as a `clearInterval` function, otherwise it can cause a severe memory leak on a bigger project. 

```text
class ClassComponent extends React.Component {
 componentWillUnmount() {
   console.log("Bye");
 }

 render() {
   return <h1>Bye, World</h1>;
 }
}
```

### Conclusion

A functional component is written shorter and simpler, which makes it easier to develop, understand, and test. Class components can also be confusing with so many uses of `this`. Using functional components can easily avoid this kind of mess and keep everything clean.

