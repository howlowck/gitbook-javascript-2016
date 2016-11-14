# State

The state is probably the most important and distinctive feature from other Flux implementations.

While other Flux implementations allow multiple states that handle different parts of the application, Redux advocates for one source-of-truth state that represents the entire state of your application (no matter how big)

The state of your app doesn't necessarily directly describe your user interface.  That's React's job.

For example if you have a sign up form, your state can be:
```js
{
  userName: '12**%#'
}
```

Then your `Input` React Component does the validation and shows an error message of `alphanumeric values please`.

Now, if Chris (our boss) says "we don't want validation errors in the input anymore, we want all the errors on the top of the page" OR "errors now is a separate modal."  We can easily implement a separate component that looks at this same state and render out the validation errors.

We cannot easily do that if the state looks like this:
```js
{
  usernameTextInput: {
    color: 'red',
    label: 'username',
    errorMessage: 'alphanumeric values please!',
    value: '12**%#'
  }
}
```
