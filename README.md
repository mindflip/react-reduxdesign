# React redux store design

practice redux middleware, and store design

## What I learned

redux middleware, and store design

### redux middleware

`Action Creator` -> `Action` -> `dispatch` -> **`Middleware`** -> `Reducers` -> `State`

- Function that gets called with every action we dispatch
- Has the ability to **STOP, MODIFY**, or otherwise mess around with actions
- Tons of open source middleware exist
- Most popular use of middleware is for dealing with async actions

### redux thunk

- Middleware to help us make requests in a redux app
- needs on API requests part
- Reason why we need redux-thunk
  - Action creator must return plain JS objects with at type property (async-await doesn't make it)
  - by the time our action gets to a reducer, we won't have fetched out data
- Action creators can return action object or `functions`
  - if an action is `function`
  - function invoked with 'dispatch'
  - wait for request to finish
  - dispatch action manually
  - New Action

### Store design

- Rules of Reducers
  - Must return any value besides 'undefined'
  - Produces 'state', or data to be used inside of your app using only previous state and the action
  - Must not return reach 'out of itself' to decide what value to return (reducers are pure)
  - Must not mutate its input 'state' argument

```js
// Removing an element from an array
state.filter(element => element !== "hi")

// Adding an element to an array
[...state, "hi"]

// Replacing an element in an array
state.map(el => el === "hi" ? "bye" : el)

// same process on object
```

### fetch problem

- firstly get posts
- get userId using a Set from posts
- make users state using the Set
