# Reducer

## Basic
The Reducer function is a pure function that describes the mutation of the State based on the previous `state` and the current `action`

```js
(prevState, action) => {
  switch (action.type) {
    case 'COMPLETE_EXTRA_CREDIT':
      return Object.assign({}, prevState, {
        grade: prevState.grade + 5
      })
    default:
      return state
  }
}
```

Like the `state` in Redux, There is only **one** reducer in an app.

## Default State
When the reducer is run for the first time, Redux will not pass a state into the reducer, so we need to set a default state like so:

```js
const previousState = {
  student: null,
  grade: 100
}

(prevState = previousState, action) => {
  switch (action.type) {
    case 'COMPLETE_EXTRA_CREDIT':
      return Object.assign({}, prevState, {
        grade: prevState.grade + 5
      })
    default:
      return state
  }
}

```

## `combineReducers()`
