# LocalStorage

Local storage is used to save info into the native local storage of the browser.

```text
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

```text
const cachedHits = localStorage.getItem(device);
        if (cachedHits) {
            setDevice(cachedHits);
          }
        localStorage.setItem('localStorageKey', device);
```

[https://www.robinwieruch.de/local-storage-react](https://www.robinwieruch.de/local-storage-react)

