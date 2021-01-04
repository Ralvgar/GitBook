# useMemo

### What Is Memoization? <a id="what-is-memoization"></a>

Memoization is essentially just caching. Imagine a complex function that is slow to run which takes `a` as an argument. In order to speed up this function, you can cache the results of running the function so that when the function is run with the same inputs you can use the cached value instead of recomputing the value. 

### `useMemo` <a id="usememo"></a>

The most basic form of memoization in React is the `useMemo` hook. The syntax for this hook is actually the exact same as `useEffect` since they both work in a similar way. The first argument of `useMemo` is a function that does the complex calculation you want to memoize, and the second argument is an array of all dependencies for that memoization.

```text
const result = useMemo(() => {
  return slowFunction(a)
}, [a])
```

If  we want to memoize `slowFunction` which depends on `a`we wrap the `slowFunction` in our `useMemo` function and used the argument `a` in the array of dependencies. Since as long as `a` stays the same the `slowFunction` will not be re-run and instead the cached value will be used.  This is the most common way `useMemo` is used.

### Referential Equality

 Referential equality is important when it comes to dependency arrays, for example in `useEffect`.

```text
function Component({ param1, param2 }) {
  const params = { param1, param2, param3: 5 }

  useEffect(() => {
    callApi(params)
  }, [params])
}
```

May seem this `useEffect` works properly, but since the `params` object is created as a new object each render this is actually going to cause the effect to run every render since the reference of `params` changes each render. `useMemo` can fix this, though.

```text
function Component({ param1, param2 }) {
  const params = useMemo(() => {
    return { param1, param2, param3: 5 }
  }, [param1, param2])

  useEffect(() => {
    callApi(params)
  }, [params])
}
```

 Now if `param1` and `param2` do not change the `params` variable will be set to the cached version of `params` which means the reference for `params` will only change if `param1`, or `param2` change. 

