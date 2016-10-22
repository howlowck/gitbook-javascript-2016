# Destructuring Assignment

It allows variables to be quickly assigned by the names of the properties on an object.

The idea is similar to the PHP function, [`list()`](http://php.net/manual/en/function.list.php), where variables are assigned in the order of the array element.  But destructuring in javascript not only can do array order, it can also assign variables by the object's property name.

Example:

```js
var vince = {
  firstName: 'Vince',
  gender: 'male'
}

var { firstName } = vince

console.log( firstName ) //would log `Vince`
```

## Resources
* [Array matching on es6-features](http://es6-features.org/#ArrayMatching)
