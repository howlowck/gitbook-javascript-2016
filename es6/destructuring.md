# Destructuring Assignment

It allows variables to be quickly assigned by the names of the properties on an object.

The idea is similar to the PHP function, [`list()`](http://php.net/manual/en/function.list.php), where variables are assigned in the order of the array element.  But destructuring in javascript not only can assign variable in an array, it can also assign variables by an object's property name.

Example:

```js
var vince = {
  firstName: 'Vince',
  gender: 'male'
}

var { firstName } = vince

console.log( firstName ) //would log `Vince`
```

## Uses in React
De-structuring assignment is used extensively in React, where we can set variables quickly out of the `props` of a component.  For example:
```js
class Task extends Component {
  render() {
    let {name, completed} = this.props // name and completed are properties on this.props
    return <Task taskName={name} isCompleted={completed} />
  }
}
```

## Resources
* [Array matching on es6-features](http://es6-features.org/#ArrayMatching)
