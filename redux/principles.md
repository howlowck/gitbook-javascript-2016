# Redux Essentials
Much of content here is from the video series created by Dan Abramov on Egghead.io 
[Please watch it]](https://egghead.io/courses/getting-started-with-redux)

## Three Core principles

### 1. Always represent the whole state of your app as a single javascript Object or `State` (State Tree).

Due to the power of react, it's possible to describe all the data and state of your app in one plain javascript object and delegate the changes, validation messages, events to the view layer (React)

This deviates from the original Flux architecture a bit where it describes that each React Component can have its own state.  While you can still have states in your components while using Redux, the single state makes component states unnecessary.

### 2. Only way to change the State is by dispatching an `Action`.

Just like you cannot change your weight willy nilly in real life, you cannot change the state of your app whenever you want.  `actions` are plain javascript objects as well.  The only required property on the object is `type` with a string as the value.

For our weight analogy, an action would be:

```js
{
  type: 'EXERCISE',
  durationInMinutes: 60
}
```

### 3. Write a pure function to describe the state mutation when given an Action.  This function is called the `Reducer` function.

Reducer is a pure function, meaning that they do not have any side-effect when the function is run.  

A function is not pure if it modifies some variable outside the scope of the function OR if its result depends on an variable that's not passed in via its function parameters.

One type of pure functions is deterministic functions.  Deterministic functions outputs the same result every single time when given the same parameters.

> **Notes**: Many people use the term "pure function" interchangeably with "deterministic functions". While the two are very closely related, not all pure functions are deterministic.  a `randomInt()` function is pure, but not deterministic.

This is what a reducer looks like:
```js
(prevState, action) => {
  if (action.type === 'EXERCISE') {
    const prevWeight = prevState.weight
    return {
      ...prevState,
      weight: prevWeight - 1
    }
  }
  return {
    ...prevState
  }
}

```
