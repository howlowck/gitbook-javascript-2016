# Object Shorthands

Object shorthands are kind of like the reverse of de-structuring assignments.

Example:

```js
var firstName = 'Chris'
var gender = 'male'

// with shorthands
var chris = {
  firstName,
  gender
}

// chris variable now has:
// {
//   firstName: 'Chris',
//   gender: 'male'
// }
```

This is pretty straight forward.  There is also a simpler way to define method properties.  See [es6-features on that](http://es6-features.org/#MethodProperties)
