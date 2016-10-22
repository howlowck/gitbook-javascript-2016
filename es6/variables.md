# Defining Variables or Constants

## `let`
Before ES6, the only way to define a variable is using the `var` keyword.  `var` is fine, but it can be very confusing.

That's why quizzes like these exist:
1. [Quiz about var scopes](http://madebyknight.com/javascript-scope/)
2. [First question on this quiz](http://dmitry.baranovskiy.com/post/91403200)

In the article, [Why you shouldn't use var anymore](https://hackernoon.com/why-you-shouldnt-use-var-anymore-f109a58b9b70#.p35hexjfk), it features the classic for-loop gotcha with `var`

## `const`
`const` defined a constant variable (oxymoron!).  Once a const is assigned, it cannot be changed.  You have to declare **and** initialize a const variable.

```js
const hao; // will throw an Error
const hao = 'Hao';
hao = 'Vince' // will throw an Error
```

Also, you cannot "redefined" a variable as a const.  For example:
```js
var hao = 'Hao'; //a regular variable
const hao = 'Real Hao'; // will throw an Error
```

`const` is recommended because it will insure you stay true to the original intent of the variable, and can help eliminate function side-effects (a common cause for bugs).

# Resources
* [Getify on the topic](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20%26%20beyond/ch2.md#let-declarations)
