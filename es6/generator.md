# Generators

Generators are VERY unique functions.  Unlike typical functions that are run-to-completion.  You can pause executions and resume them from outside the generator function.

### Generator Definition
This is how you define a generator.  

Notice two things in the code below: the `*` before the function name, and the `yield` **expression** keyword.

```js
function* countDown() {
  yield 5;
  yield 4;
  yield 3;
  yield 2;
  yield 1;
}
```

The `*` signifies that this function is a generator.

The `yield` keyword is a magical keyword that does a couple of things.  The biggest feature of `yield` is that it pauses the execution of the function, and passes whatever value out of the scope to the scope that created the iterator object from the generator.

### Iterator object
When you call the generator function, you create a special iterator object that has two methods on it: `next` and `throw`.  We will focus on `next` for now

> **Note:** If you read the section on Promise, the methods look eerily similar to `then` and `catch` on a Promise object.  I think it highlights how promises and generators are both trying to solve similar problems of async but has totally different intents.

#### `next` method

The `next` method, when called, returns a result object that has two properties on it: `done` and `value`.

See the countdown example below and note what the next method returns after each call.

```js
let rocketCountDown = countDown() //rocketCountDown is now a iterator object
const five = rocketCountDown.next() // five === {done: false, value: 5}
const four = rocketCountDown.next() // four === {done: false, value: 4}
const three = rocketCountDown.next() // three === {done: false, value: 3}
const two = rocketCountDown.next() // two === {done: false, value: 2}
const one = rocketCountDown.next() // one === {done: false, value: 1}
const complete = rocketCountDown.next() // complete === {done: true, value: undefined}
```

First thing to notice is that the first `yield`ed value is return in the first `next` call.
Second thing is after five `next calls` in the result object with `value : 1`, the `done` property is not `true`.  Even though `1` is the last yielded value.  It's not until another `next` is called that the `done` property is `true`

### `next` and `yield`
It should be apparent at this point that there are to worlds (or scopes) when we are working with generators.  Let's name the scope in the generator the **generator scope** and the scope that created the iterator from the generator the **iterator scope** 

Up to this point, it seems that the relationship between generator and iterator scope is a one-way street.  Generator can `yield` values to the iterator scope, but seems not a way to pass values back into the generator scope.  Fortunately, that is not true!  the generator-iterator-scope relationship *is a two-way street*.  They are able to communicate with each other!

#### More about the `yield` keyword

This is where another feature of the `yield` keyword comes in.  Notice that the word **expression** is bolded in the "Generator Definition" section.  

In Javascript, `expressions` and `statements` are not the same.  Expressions are to produce a value, while statements are more dealing with flow of the program.  For example, `if` or `return` are statement keywords NOT expression keywords.  

Since `yield` is an expression keyword, this makes the `yield` act more like the `typeof` keyword than the `return` keyword.

```js
() => {
  str = "Hello"
  const type = typeof stringNum // type === "string"
  const fail = return stringNum // SyntaxError: Unexpected token return
}
```

Since a `yield` expression can actually return a value.  You can write your generator like so:
```js
function* countDown(initialStatus) {
  var crewStatus, fuelStatus, engineStatus, electricalStatus, finalStatus
  if (initialStatus.everythingGood) {
    crewStatus = yield 5;
  }
  if (crewStatus.everythingGood) {
    fuelStatus = yield 4;
  }
  if (fuelStatus.everythingGood) {
    engineStatus = yield 3;
  }
  if (engineStatus.everythingGood) {
    electricalStatus = yield 2;
  }
  if (electricalStatus.everythingGood) {
    finalStatus = yield 1;
  }
}

```

#### More about the `next` method

From the previous code block, we have the new countDown generator that are expecting a value passed back from the iterator scope with each `yield` expression.

This is how to pass back the status object:

```js
let rocketCountDown = countDown({everythingGood: true}) //parameter maps to initialStatus
// returns iterator object
rocketCountDown.next(); // no Parameter!!
// returns {done: false, value: 5}
rocketCountDown.next({everythingGood: true}) // parameter maps to crewStatus in generator 
// returns {done: false, value: 4}
rocketCountDown.next({everythingGood: true}) // parameter maps to fuelStatus in generator 
// returns {done: false, value: 3}
rocketCountDown.next({everythingGood: true}) // parameter maps to engineStatus in generator 
// returns {done: false, value: 2}
rocketCountDown.next({everythingGood: true}) // parameter maps to electricalStatus in generator 
// returns {done: false, value: 1}
rocketCountDown.next({everythingGood: true}) // parameter maps to finalStatus in generator 
// returns {done: true, value: undefined}
```

### TODO: Refactoring
