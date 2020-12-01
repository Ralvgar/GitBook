# Styled Components

{% embed url="https://styled-components.com/" %}

styled-components utilises tagged template literals to style your components.

```javascript
// Create a Title component that'll render an <h1> tag with some styles
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`;

// Create a Wrapper component that'll render a <section> tag with some styles
const Wrapper = styled.section`
  padding: 4em;
  background: papayawhip;
`;

// Use Title and Wrapper like any other React component – except they're styled!
render(
  <Wrapper>
    <Title>
      Hello World!
    </Title>
  </Wrapper>
);
```

You can pass a function \("interpolations"\) to a styled component's template literal to adapt it based on its props.

```javascript
const Button = styled.button`
  /* Adapt the colors based on primary prop */
  background: ${props => props.primary ? "palevioletred" : "white"};
  color: ${props => props.primary ? "white" : "palevioletred"};
  font-size: 1em;
  border-radius: 3px;
`;

render(
  <div>
    <Button>Normal</Button>
    <Button primary>Primary</Button>
  </div>
);
```

To easily make a new component that inherits the styling of another, just wrap it in the styled\(\) constructor.

```javascript
// The Button from the last section without the interpolations
const Button = styled.button`
  color: palevioletred;
  font-size: 1em;
`;

// A new component based on Button, but with some override styles
const TomatoButton = styled(Button)`
  color: tomato;
  border-color: tomato;
`;

render(
  <div>
    <Button>Normal Button</Button>
    <TomatoButton>Tomato Button</TomatoButton>
  </div>
);
```

you can change which tag or component a styled component renders.  You can use the ["as" polymorphic prop](https://styled-components.com/docs/api#as-polymorphic-prop) to dynamically swap out the element that receives the styles you wrote. 

```javascript
const Button = styled.button`
  display: inline-block;
  color: palevioletred;
`;

const TomatoButton = styled(Button)`
  color: tomato;
  border-color: tomato;
`;

render(
  <div>
  // this is a button.
    <Button>Normal Button</Button>
    // these are hyperlinks thx to "as" polymorphic prop.
    <Button as="a" href="/">Link with Button styles</Button>
    <TomatoButton as="a" href="/">Link with Tomato Button styles</TomatoButton>
  </div>
);
```

["as" polymorphic](https://styled-components.com/docs/api#as-polymorphic-prop) works with custom components too.

```javascript
const Button = styled.button`
  display: inline-block;
  color: palevioletred;
`;

const ReversedButton = props => 
<Button {...props} children={props.children.split('').reverse()} />

render(
  <div>
    <Button>Normal Button</Button>
    <Button as={ReversedButton}>Custom Button with Normal Button styles</Button>
  </div>
);
```

The styled method works perfectly on all of your own component, you need to pass className prop to a DOM element.

```javascript
// This could be react-router-dom's Link for example
const Link = ({ className, children }) => (
  <a className={className}>
    {children}
  </a>
);

const StyledLink = styled(Link)`
  color: palevioletred;
  font-weight: bold;
`;

render(
  <div>
    <Link>Unstyled Link</Link>
    <br />
    <StyledLink>Styled Link</StyledLink>
  </div>
);
```

If the styled target is a simple element, tyled-components passes through any known HTML attribute to the DOM. If it is a custom React component, styled-components passes through all props.

#### Pseudoelements, pseudoselectors, and nesting

The ampersand \(&\) can be used to refer back to the main component. If you put selectors in without the ampersand, they will refer to children of the component. Finally, the ampersand can be used to increase the specificity of rules on the componen.

```javascript
const Thing = styled.div.attrs((/* props */) => ({ tabIndex: 0 }))`
  color: blue;

  &:hover {
    color: red; // <Thing> when hovered
  }

  & ~ & {
    background: tomato; // 
    <Thing> as a sibling of <Thing>, but maybe not directly next to it
  }

  & + & {
    background: lime; // 
    <Thing> next to <Thing>
  }

  &.something {
    background: orange; // 
    <Thing> tagged with an additional CSS class ".something"
  }

  .something-else & {
    border: 1px solid; // 
    <Thing> inside another element labeled ".something-else"
  }
`

render(
  <React.Fragment>
    <Thing>Hello world!</Thing>
    <Thing>How ya doing?</Thing>
    <Thing className="something">The sun is shining...</Thing>
    <div>Pretty nice day today.</div>
    <Thing>Don't you think?</Thing>
    <div className="something-else">
      <Thing>Splendid.</Thing>
    </div>
  </React.Fragment>
```

### Attaching additional props

 To avoid unnecessary wrappers that just pass on some props to the rendered component, or element, you can use the [.attrs constructor](https://styled-components.com/docs/api#attrs). It allows you to attach additional props \(or "attributes"\) to a component. In this example we get access to our newly created props in the interpolations, and the type attribute is passed down to the element.

```javascript
const Input = styled.input.attrs(props => ({
  // we can define static props
  type: "text",

  // or we can define dynamic ones
  size: props.size || "1em",
}))`
  /* here we use the dynamically computed prop */
  margin: ${props => props.size};
  padding: ${props => props.size};
`;

render(
  <div>
    <Input placeholder="A small text input" />
    <br />
    <Input placeholder="A bigger text input" size="2em" />
  </div>
);
```

.attrs are applied from the innermost styled component to the outermost styled component. So we can  **override** nested uses of .attrs.

```javascript
const Input = styled.input.attrs(props => ({
  type: "text",
  size: props.size || "1em",
}))`
  border: 2px solid palevioletred;
  margin: ${props => props.size};
  padding: ${props => props.size};
`;

// Input's attrs will be applied first, and then this attrs obj
const PasswordInput = styled(Input).attrs({
  type: "password",
})`
  // similarly, border will override Input's border
  border: 2px solid aqua;
`;

render(
  <div>
    <Input placeholder="A text input" size="2em" />
    <br />
    {/* Notice we can still use the size attr from Input */}
    <PasswordInput placeholder="A password input" size="2em" />
  </div>
);
```

### Animations

keyframes helper generate a unique instance that you can use throughout your app

```javascript
// Create the keyframes
const rotate = keyframes`
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
`;

// Here we create a component that will rotate 
// everything we pass in over two seconds
const Rotate = styled.div`
  display: inline-block;
  animation: ${rotate} 2s linear infinite;
  padding: 2rem 1rem;
  font-size: 1.2rem;
`;

render(
  <Rotate>&lt; 💅🏾 &gt;</Rotate>
);
```

 Keyframes are lazily injected when they're used, which is how they can be code-splitted, so you have to use [the css helper](https://styled-components.com/docs/api#css) for shared style fragments:

```javascript
import styled, {css} from 'styled-components';

const rotate = keyframes``
// ❌ This will throw an error!
const styles = `
  animation: ${rotate} 2s linear infinite;
`
// ✅ This will work as intended
const styles = css`
  animation: ${rotate} 2s linear infinite;
`
```

### Theming

Exporting a &lt;ThemeProvider&gt;  wrapper component provides a theme to all React components underneath itself. In the render tree all styled-components will have access to the provided theme, even when they are multiple levels deep.

```javascript
// Define our button, but with the use of props.theme this time
const Button = styled.button`

  /* Color the border and text with theme.main */
  color: ${props => props.theme.main};
  border: 2px solid ${props => props.theme.main};
`;

// We are passing a default theme for Buttons that arent wrapped in the ThemeProvider
Button.defaultProps = {
  theme: {
    main: "palevioletred"
  }
}

// Define what props.theme will look like
const theme = {
  main: "mediumseagreen"
};

render(
  <div>
    <Button>Normal</Button>
    
    <ThemeProvider theme={theme}>
      <Button>Themed</Button>
    </ThemeProvider>
  </div>
);
```

#### Function themes

You can also pass a function for the theme prop. This function will receive the parent theme, that is from another &lt;ThemeProvider&gt;  higher up the tree.

```javascript
// Define our button, but with the use of props.theme this time
const Button = styled.button`
  color: ${props => props.theme.fg};
  border: 2px solid ${props => props.theme.fg};
  background: ${props => props.theme.bg};
`;

// Define our `fg` and `bg` on the theme
const theme = {
  fg: "palevioletred",
  bg: "white"
};

// This theme swaps `fg` and `bg`
const invertTheme = ({ fg, bg }) => ({
  fg: bg,
  bg: fg
});

render(
  <ThemeProvider theme={theme}>
    <div>
      <Button>Default Theme</Button>

      <ThemeProvider theme={invertTheme}>
        <Button>Inverted Theme</Button>
      </ThemeProvider>
    </div>
  </ThemeProvider>
);
```

A theme can also be passed down to a component using the theme prop. This is useful to circumvent a missing ThemeProvider or to override it.

```javascript
// Define our button
const Button = styled.button`

  /* Color the border and text with theme.main */
  color: ${props => props.theme.main};
  border: 2px solid ${props => props.theme.main};
`;

// Define what main theme will look like
const theme = {
  main: "mediumseagreen"
};

render(
  <div>
    <Button theme={{ main: "royalblue" }}>Ad hoc theme</Button>
    <ThemeProvider theme={theme}>
      <div>
        <Button>Themed</Button>
        <Button theme={{ main: "darkorange" }}>Overridden</Button>
      </div>
    </ThemeProvider>
  </div>
);
```

