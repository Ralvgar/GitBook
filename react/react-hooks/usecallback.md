# useCallback

`useCallback` is very similar to useMemo but instead to returning `return` from our function it returns the entire function. Its a very important hook when we need to worry about referential equality and avoid unnecesary renders, its also important when you have to create a function that is really slow you would want to use `useCallback` to only create that function when you need to and not recreate it every single time you render.

```text
const handleReset = useCallback(() => {
  return doSomething(a, b)
}, [a, b])
```



