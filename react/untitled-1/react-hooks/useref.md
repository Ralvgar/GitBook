# useRef

This hook takes an initial value as the only argument then returns a ref for you to work with.

```javascript
const myRef = useRef(null)
```

 In the above example I have created a ref called `myRef` and set its default value to `null`. This means that `myRef` is now equal to an object that looks like this.

```text
{ current: null }
```

  Ref is always an object with a single `.current` property which is set to the current value of the ref. They are very similarly to state, since they persist between renders, but refs do not cause a component to re-render when changed.

Example: 

```javascript
function State() {
  const [rerenderCount, setRerenderCount] = useState(0);

  useEffect(() => {
    setRerenderCount(prevCount => prevCount + 1);
  });

  return <div>{rerenderCount}</div>;
}
```

```javascript
function Ref() {
  const rerenderCount = useRef(0);

  useEffect(() => {
    rerenderCount.current = rerenderCount.current + 1;
  });

  return <div>{rerenderCount.current}</div>;
}
```

Both of these components will correctly display the number of times a component has been re-rendered, but in the state example the component will infinitely re-render itself since setting the state causes the component to re-render. The ref example on the other hand will only render once since setting the value of a ref does cause any re-renders.

### How To Use Refs <a id="how-to-use-refs"></a>

The most common use case for refs in React is to reference a DOM element. Because of how common this use case is every DOM element has a ref property you can use for setting a ref to that element. For example, if you wanted to focus an input element whenever a button was clicked you could use a ref to do that.

```javascript
function Component() {
  const inputRef = useRef(null)

  const focusInput = () => {
    inputRef.current.focus()
  }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus Input</button>
    </>
  )
}
```

In the code above when we click the button it will call `focusInput` which uses the current value of the `inputRef` variable to set the focus on the input element.

**Dont use** refs to dynamically add and remove elements \(`appendChild`, `removeChild`, etc.\) in a component instead of having React do that for you. This leads to inconsistencies between the actual DOM and the React virtual DOM.

### Using Refs Beyond The DOM <a id="using-refs-beyond-the-dom"></a>

Refs can also be used for any form of storage that is persisted across component renders. A very common use case for this would be storing the previous value of a state variable.

```javascript
function Component() {
  const [name, setName] = useState('Kyle')
  const previousName = useRef(null)

  useEffect(() => {
    previousName.current = name
  }, [name])

  return (
    <>
      <input value={name} onChange={e => setName(e.target.value)} />
      <div>{previousName.current} => {name}</div>
    </>
  )
}
```

 The above code will update the `previousName` ref every time the name changes so that it always has the previous value of the name variable stored in it.

