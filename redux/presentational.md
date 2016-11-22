# Presentational Components

Presentational Components are what some people call "dumb" components.

Presentational components are not aware of the state at all.

They are only aware of the `props` that they are given, and present the view based on the props.
In other words, when the same set of data is passed to `props`, the view should ALWAYS display the same view.

> **Note** sometimes they are also called pure components.


## To Create or Define a Presentational Component

A presentational component definition looks like so:
```js
import react, {Component} from 'react'

class Greet extends Component {
  render() {
     const {name} = this.props;
     return (
       <div>
          <p> Hello! {name} </p>
       </div>
       )
  }
}

export default Greet

```

Presentational components can also be expressed in arrow Functions
```js
import react from 'react'

const Greet = ({name}) => (
  <div>
    <p> Hello! {name} </p>
  </div>
)

```

These two ways achieve the same view:

* The first way allows you to add more to the object since it's a bonafide Component object. 

* The component written in the second, more concise, way is called a **Functional Stateless Component**.
> **Note** Functional Stateless Components was introduced in [React 0.14](https://medium.com/@joshblack/stateless-components-in-react-0-14-f9798f8b992d#.f5fnk1rat)

## To Use a Presentational Component

No matter how you define a presentational component (either with Component class inheritance or arrow functions), using it is all the same.

```js
import Greet from 'components/Greet'

const App = (props) => (
  <div>
    <h1>props.appName</h1>
    <Greet name='Vince' />
  </div>
)

```
