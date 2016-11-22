# Components

Components are the divisible units of a react-driven application.

Components can be defined by either extending React's `Component` class or by using arrow functions.
See an example in the [presentational components](../redux/presentational.md) section under Redux.

## Upper-case Component names
A user-defined component MUST start with a upper-case.  This is consistent with pretty much all programming language encouraging class names to start with a upper-case.

## `render` method
If the component is defined by extending the `Component` class, the only required function is `render`.

Then you are able to return whatever html element or other react Components.

## `props`
`props` are probably the most important property (or variable) in your component because it contains all the information that's needed to display your component. 

If your component is a class (extending `Component`), `props` exists on the object and you can access the object by simply using `this.props`

If your component is an arrow function, the first parameter passed into the function is the `props` object.

## `PropTypes`
When you are defining a component, there will be properties on the `props` object that you will be depending on.  
For example, if you are creating a `Greet` component, `name` is probably a required property on the `props` object.

To declare a property as required and a certain type, you create a static property of `propTypes` with the value being an object of the property declarations like so:

```js
class Greet extends Component {
  static propTypes = {
    name: PropTypes.string.isRequired
  }
  render() {
    const {name} = this.props
    return (
      <p> Hello {name} </p>
    )
  }
}
```

If the component is a functional component:
```js
const Greet = ({name}) => (
  <p> Hello {name} </p>
)

Greet.propTypes = {
  name: PropTypes.string.isRequired
}
```
