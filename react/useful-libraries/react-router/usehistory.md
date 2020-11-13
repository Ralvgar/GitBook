---
description: it gives acces to the history and can be used to navigate through your app
---

# useHistory\(\)

```text
Import { useHistory } from "react-router-dom";

function HomeButton() {
  let history = useHistory();

  return (
    <button type="button" onClick={() => history.goBack()}>
      Go home
    </button>
  );
}
```

