# useContext

### What Is The Context API? <a id="what-is-the-context-api"></a>

React uses state to store data and props to pass data between components. This works well for handling local state and for passing simple props between parent/child components. This system breaks down when you start to have global state or props that need to be passed to deeply nested components. With just props and state you end up having to resort to prop drilling which is when you pass down props through a bunch of different components so they can get to one single component far down the hierarchy.

With the context API you can specify certain pieces of data that will be available to all components nested inside the context with no need to pass this data through each component. It is essentially semi-global state that is available anywhere inside the context.

```javascript
//Basic template for context

import React, { useContext, useState } from 'react';


const ThemeContext = React.createContext()
const ThemeUpdateContext = React.createContext()

export function useTheme() {
    return useContext(ThemeContext)
}

export function useThemeUpdate() {
    return useContext(ThemeUpdateContext)
}

export function ThemeProvider ({children}) {
    const [darkTheme, setDarkTheme] = useState(true)
    
    function toggleTheme() {
        setDarkTheme( prevDarkTheme => !prevDarkTheme)
    }

    return (
        <ThemeContext.Provider value={darkTheme}>
            <ThemeUpdateContext.Provider value={toggleTheme}>
                {children}
            </ThemeUpdateContext.Provider>
        </ThemeContext.Provider>
    )
}
```

```javascript
// Main screen

import FunctionContextComponent from './FunctionContextComponent'
import { ThemeProvider } from './ThemeContext'

function App() {
    return (
    <ThemeProvider>
        <FunctionCOntextComponent />
    </ThemeProvider>
    )
}
```

```javascript
// inside components

import React from 'react';
import { useTheme, useThemeUpdate } from './ThemeContext';

export default function FunctionContextComponent() {
    const darkTheme = useTheme()
    const toggleTheme = useThemeUpdate()
    const themeStyles = {
        backgroundColor: darkTheme ? '#333' : '#CCC',
        color: darkTheme ? '#CCC' :'#333',
    }

    return (
        <>
            <button onClick={toggleTheme}>Toggle Theme</button>
            <div style={themeStyles}>Function Theme</div>
        </>
    )
}
```

Context works just like a normal function where you call the context and it will give you the values inside of it for you to use later in the code.



