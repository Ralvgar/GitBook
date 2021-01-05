# useReducer

 `useReducer` is the best solution in React for handling complex state interactions and sharing state globally.

 Similar to `useState`, `useReducer` takes an initial state as one of its arguments and returns to us the current state and a way to update that state. `useReducer` also re-renders a component when the state changes just like `useState`. The only major difference is that we also need to pass a reducer function to `useReducer` which contains all the logic for modifying our state.

```javascript
const [count, dispatch] = useReducer(reducer, 0)
```

In that example, default state is 0, passed as the second argument and the count is returned as the first element just like with useState. Instead of having a `setCount` we have a `dispatch` function which allows us to call the reducer fuction we pass as the first argument. 

```javascript
function reducer(count, action) {
  switch (action.type) {
    case 'increment':
      return count + 1
    default:
      return count
  }
}

const [count, dispatch] = useReducer(reducer, 0)
```

Reducer function takes in a current state as well as an action to perform on the state and it returns the new state.

```javascript
function reducer(count, action) {
  switch (action.type) {
    case 'increment':
      return count + 1
    case 'decrement':
      return count - 1
    case 'reset':
      return 0
    default:
      return count
  }
}

function Counter() {
  const [count, dispatch] = useReducer(reducer, 0)

  return (
    <>
      <span>{count}</span>
      <button onClick={() => dispatch({ type: 'increment' })}>
        +
      </button>
      <button onClick={() => dispatch({ type: 'decrement' })}>
        -
      </button>
      <button onClick={() => dispatch({ type: 'reset' })}>
        Reset
      </button>
    </>
  )
}
```

With `useReducer` the component just tells our reducer what actions to perform and the reducer should handle all the complex logic.

To pass data to our reducer the common practice is to put all our data inside a property called `payload`  \(payload is a name convention you can use what you want\) on our object, then create a new section in our reducer to handle this and dispatch to call that action and modify our reducer object.

That's an example of useRedurer from my [codos-app-client](https://github.com/mallorcabootcamp/codos-app-client):

```javascript
export const initialState = {
  ismenuActived: false,
  currentCo2: 0,
  currentTemperature: 0,
  currentHumidity: 0,
  co2Data: [],
  deviceList: [],
  isError: false,
  isLoading: false,
};

export enum IAction {
  setMenuActived = "setMenuActived",
  setCurrentCo2 = "setCurrentCo2",
  setCurrentTemperature = "setCurrentTemperature",
  setCurrentHumidity = "setCurrentHumidity",
  setCo2Data = "setCo2Data",
  setDeviceList = "setDeviceList",
  setIsError = "setIsError",
  setIsLoading = "setIsLoading",
}

export const reducer = (
  state: any,
  { type, value }: { type: string; value: any }
) => {
  switch (type) {
    case IAction.setMenuActived:
      return { ...state, isMenuActived: value };
    case IAction.setCurrentCo2:
      return { ...state, currentCo2: value };
    case IAction.setCurrentTemperature:
      return { ...state, currentTemperature: value };
    case IAction.setCurrentHumidity:
      return { ...state, currentHumidity: value };
    case IAction.setCo2Data:
      return { ...state, co2Data: value };
    case IAction.setDeviceList:
      return { ...state, deviceList: value };
    case IAction.setIsError:
      return { ...state, isError: value };
    case IAction.setIsLoading:
      return { ...state, isLoading: value };
  }
};
```

```javascript
import { reducer, IAction, initialState } from "./State";


const [state, dispatch] = useReducer(reducer, initialState);

//... a lot of code ...

          {
            dispatch({ type: IAction.setIsLoading, value: false });
            dispatch({
              type: IAction.setCurrentCo2,
              value: currentCo2Response[0].value,
            });
            dispatch({
              type: IAction.setCurrentTemperature,
              value: currentTemperatureResponse[0].value,
            });
            dispatch({
              type: IAction.setCurrentHumidity,
              value: currentHumidityResponse[0].value,
            });
            dispatch({ type: IAction.setCo2Data, value: periodCo2Response });
          }
        )
        .catch(() => dispatch({ type: IAction.setIsError, value: true }));
    }
  }, [selectedDevice]);
  
  // ... a lot of code ...
  
  <p
      className="mb-0 d-inline"
      onClick={() =>
      dispatch({ type: IAction.setMenuActived, value: true })
      }
    >
    <FontAwesomeIcon icon={faBars} size="lg" />
  </p>
```



