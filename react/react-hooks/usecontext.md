# useContext

### What Is The Context API? <a id="what-is-the-context-api"></a>

React uses state to store data and props to pass data between components. This works well for handling local state and for passing simple props between parent/child components. This system breaks down when you start to have global state or props that need to be passed to deeply nested components. With just props and state you end up having to resort to prop drilling which is when you pass down props through a bunch of different components so they can get to one single component far down the hierarchy.

With the context API you can specify certain pieces of data that will be available to all components nested inside the context with no need to pass this data through each component. It is essentially semi-global state that is available anywhere inside the context.

```text
const ThemeContext = React.createContext()

function App() {
  const [theme, setTheme] = useState('dark')

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <ChildComponent />
    </ThemeContext.Provider>
  )
}
```

```text
function ChildComponent() {
  return <GrandChildComponent />
}
```

```text
function GrandChildComponent() {
  const { theme, setTheme } = useContext(ThemeContext)
  return (
    <>
      <div>The theme is {theme}</div>
      <button onClick={() => setTheme('light')}>
        Change To Light Theme
      </button>
    </>
  )
}
```

Context works just like a normal function where you call the context and it will give you the values inside of it for you to use later in the code.



