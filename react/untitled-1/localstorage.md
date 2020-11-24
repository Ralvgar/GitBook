# LocalStorage

Local storage is used to save info into the native local storage of the browser.

```javascript
// setter
localStorage.setItem('myData', data);
 
// getter
localStorage.getItem('myData');
 
// remove
localStorage.removeItem('myData');
 
// remove all
localStorage.clear();
```

You can also use the cache get again the data, getting it before the first set.

```javascript
const cachedHits = localStorage.getItem(device);
        if (cachedHits) {
            setDevice(cachedHits);
          }
        localStorage.setItem('localStorageKey', device);
```

I also created a custom hook to manage our local storage.

```javascript
import { useState, useEffect } from 'react';

export const useStateWithLocalStorage = (localStorageKey: string): [string, (state: string) => void] => {
    const [value, setValue] = useState(
        localStorage.getItem(localStorageKey) || ''
    );

    useEffect(() => {
        localStorage.setItem(localStorageKey, value);
    }, [value, localStorageKey]);

    return [value, setValue];
};
```

[https://www.robinwieruch.de/local-storage-react](https://www.robinwieruch.de/local-storage-react)

