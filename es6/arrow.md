# Arrow Functions

An arrow function is an anonymous functions that is without a context.  

An arrow function looks like this:

```js
var double = (x) => (x + x)
double(5) // will return 10

// OR 

var greet = (name) => {
  return 'Hi ' + name + '!!!'
}
greet('Ross') // will return 'Hi Ross!!!'
```

Notice there are two ways to define the body of the arrow function, with parenthesis, the function assumes you want to return the one statement.  With curly braces, the function will execute multiple statements but you need to put `return` in order to return a value.

> _**Note:**_ Arrow function body can even be declared without parenthesis! It will have the same effect as if were wrapped with parenthesis.

## No context

While it looks like that arrow functions are just syntactic sugar to anonymous function, and the `this` keywork still works inside of an arrow function.  It's important to remember that arrow functions have no context, and `this` keyword only works because it looks up `this` in its outer scope. 

> _**Note:**_ Not only does the arrow function not have `this`, it also doesn't have its own `arguments` and `super`.  All are getting from its outer scope.

This might seem like a unnecessary technical detail, it might [lead to confusion](https://twitter.com/jeffrey_way/status/717003578842415105).

## Resources
* [es6-features](http://es6-features.org/#ExpressionBodies)
* [Explaination of arrow functions and `this`](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20%26%20beyond/ch2.md#not-just-shorter-syntax-but-this)
