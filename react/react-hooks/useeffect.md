# useEffect

 In a class component all side effects are handled with life cycle methods. In function components we use the `useEffect` hook to define side effects, each side effect and all of its cleanup is defined in its own `useEffect` hooks.

```text
useEffect(() => {
  console.log('This is a side effect')
})
```

This side effect will now run on every single render of the component.  `UseEffect` takes an optional second parameter which is an array of values. This array of values is compared during each re-render with the previous render’s array values and the side effect will only be run if the values in the array changed since the last render.

If you only want to run a side effect on mount then you can pass an empty array as the second parameter since that will never change between renders.

```text
useEffect(() => {
  console.log('Only run on mount')
}, [])
```

Having this second array parameter is really nice since it allows side effects to be run whenever any value changes. For example if the url from our component changes we can run a side effect

```text
useEffect(() => {
  console.log('Only run on url change')
}, [url])
```

### Cleaning Up Side Effects

 If you return a function from the side effect inside `useEffect` then that function will be run every time the side effect is re-ran.

```text
useEffect(() => {
  console.log('This is my side effect')

  return () => {
    console.log('This is my clean up')
  }
})
```

If we were to mount this component and then re-render it twice and then un-mount it you would get the following output.

```text
// MOUNTED
// This is my side effect

// RE-RENDER 1:
// This is my clean up
// This is my side effect

// RE-RENDER 2:
// This is my clean up
// This is my side effect

// UN-MOUNT:
// This is my clean up
```

The cleanup is run directly before the side effect is run as long as the side effect has occurred at least once. Also, the cleanup is run when a component un-mounts as well.

