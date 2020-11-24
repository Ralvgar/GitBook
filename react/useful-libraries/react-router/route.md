# Route

Its to render the UI when the path matches the current URL.

```javascript
import React from 'react';
import { HashRouter, Switch, Route  } from "react-router-dom";

function App() {

 return (
    <HashRouter>
      <Switch>
        <Route path='/history'>
          <ScrollToTop>
            <History />
          </ScrollToTop>
        </Route>
    </HashRouter>
  );
}
```

It can also handle diferent routes to for the same component

```javascript
<Route path={['/', '/main']} exact>
   <ScrollToTop>
      <Main />
   </ScrollToTop>
</Route>
```

the component can also gived with the compoment prop

```javascript
 <Route path="/unexpected-error/:route" component={UnexpectedError} />
```

