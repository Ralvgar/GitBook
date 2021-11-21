# useCallback

`useCallback` is very similar to `useMemo `but instead to`return` values from our function it returns the entire function.

To understand the differences between them here is a quick example where both will return the same value.

```
useCallback(() => {
  return a + b
}, [a, b])

useMemo(() => {
  return () => a + b
}, [a, b])
```

&#x20;Its a very important hook when we need to worry about referential equality and avoid unnecesary renders.

```
function Parent() {
  const [items, setItems] = useState([])
  const handleLoad = (res) => setItems(res)

  return <Child onLoad={handleLoad} />
}

function Child({ onLoad }) {
  useEffect(() => {
    callApi(onLoad)
  }, [onLoad])
}
```

In the above example the `handleLoad` function is re-created every time the `Parent` component is rendered. This means that the `Child` component’s `useEffect` will re-run ever render since the `onLoad` function has a different referential equality each render. To fix this we need to wrap the `handleLoad` in a `useCallback`.

```
function Parent() {
  const [items, setItems] = useState([])
  const handleLoad = useCallback((res) => setItems(res), [])
  return <Child onLoad={handleLoad} />
}

function Child({ onLoad }) {
  useEffect(() => {
    callApi(onLoad)
  }, [onLoad])
}
```

Now the `handleLoad` function will never change, thus the `useEffect` in the `Child` component will not be called on each re-render.

&#x20;`useCallback` also can be used when you have to create a function that is really slow you would want to use `useCallback` to only create that function when you need to and not recreate it every single time you render. But `useMemo` it's probably better option to handle this situations.



