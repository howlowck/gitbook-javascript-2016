# Redux Actions

## Action
Actions are just plain objects with a `type` property on it.
The `type` property should have a string that's the name of the action.

On the Action object, there can be other properties which acts as payload.

## Action Creator
Action Creators are convenience functions that outputs an Action.

Like almost everything else in redux, action creators should be **pure functions**.

Here is an example of an action creator
```js
const exercise = (durationInMinutes) => ({
  type: 'EXERCISE',
  durationInMinutes
})
```
