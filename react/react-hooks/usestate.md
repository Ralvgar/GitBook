# useState

`useState` hook takes the initial state as an argument.

```text
useState(initialState)
```

The `useState` hook also returns an array with two entries. The first entry in the array is the current state while the second entry is the method which allows us to update the state.

```text
const [state, setState] = useState(initialState)
```

### Updating State

We use the second value of our state to set the state.

```text
setCount(prevCount => prevCount + amount)
```

```text
function Counter() {
  const [count, setCount] = useState(0)

  function changeCount(amount) {
    setCount(prevCount => prevCount + amount)  }

  function resetCount() {
    setCount(0)  }

  return (
    <>
      <span>{count}</span>
      <button onClick={() => changeCount(1)}>+</button>
      <button onClick={() => changeCount(-1)}>-</button>
      <button onClick={() => resetCount()}>Reset</button>
    </>
  )
}
```

### Updating State Objects

Most of the time you will use single values with `useState`, but there are some cases where using an object makes more sense.

```text
const [preferences, setPreferences] = useState({
  theme: 'light',
  fontSize: 'normal'
})
```

to change a single value state you would need to combine the old state with the new state manually.

```text
setPreferences(prevPreferences => {
  return { ...prevPreferences, theme: 'dark' }
})
```

### Initial State Computation

In function components the initial state computation is declared in the render function and happens every render. Having a slow initial state computation can slow down an entire application significantly because of this.

```text
useState(/* Slow computation */)
```

 `useState` can also take a function as the argument instead of a value, and that function will only be run the very first time a component is rendered. Using this function version of `useState` you will no longer run the slow computation each render, but only once on the first render of the component

```text
useState(() => {
  /* Slow computation */
})
```

