# ES5

ES5 was introduced in 2011, has been solidified. Current browsers have support for its specs. [See compatibility table](http://kangax.github.io/compat-table/es5/)

## Function binding 

In javascript, functions are [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen).  This means that functions can accept functions as parameters and return other functions.  

Since all functions are objects, and all objects are passed by reference, the keyword `this` is usually a headache for novice javascript developers.

with the `bind` function, you can explicitly bind an object to a function which defines what the variable `this` refers to.

For example:

```js

var hao = {

   firstName: 'Hao',

   age: 28

};

function greet() {

   console.log('Hi ' + this.firstName + '!');

} 

//creates the function with the explicit binding

var greetsHao = greet.bind(hao);  

greetsHao(); //logs "Hi Hao!"

```

## Array Functions

Popularized by libraries like underscore or lodash, functions like `forEach` or `map` (and much more) now exists on all javascript arrays.

Here is how I think when to use some of the array functions:

### `forEach`

`forEach` simply iterates over all the elements in the array and puts in a function, allowing the develop to do anything they want in the iterator function.  

I try to use `forEach` as little as possible, because this function is so flexible and often introduces side effects. **And using `forEach` makes the code less readable than using other methods below.**  The function also returns `undefined` which makes it not chainable.

See [forEach On MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

### `map`

`map` transforms an array by transforming each element passed in the callback.

I use `map` when I want to change the array in some way.  `map` returns the newly transformed array.

[map on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

### `reduce`

I tend to use `reduce` when I want to condense the array into one value.  One example is summing all the element with a certain condition.

[reduce on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

### `every`, `some`

`every` and `some` returns true or false if the array satifies with the condition returned by the callback.

[every](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) and [some](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) on MDN
