# Promises

Promises are all about "promising" to return a future value. 


## Making a Promise
To make a promise, you instantiate the `Promise` class.  Inside the `Promise` constructor, you pass a function.  We'll call this function the executor.

The executor function has two parameters: `resolve` and `reject`.  Both `resolve` and `reject` are functions that can take in one parameter.

```js
let askedForBurger = new Promise((resolve, reject) => { // the Executor function
  setTimeout(() => {
    if (kitchenOnFire) {
      reject('Kitchen is on Fire')
      return
    }
    let looksCouldKaleBurger = new Burger()
    resolve(looksCouldKaleBurger)
  }, 1000) //Takes one second to make your burger
})
```

## The `Promise` Object
From the code example above, now you have a Promise called `askedForBurger`.  You can now describe what you want to do with the burger after the Burger is done.

All promise objects have two methods: `then` and `catch`.

> **Note:** Any object with a method named `then` is called a Thenable object.  

```js
const eatBurger = (burger) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve('mmm so good!')
    }, 2000) // Takes two seconds to eat your burger
  } 
}

let ateBurger = askedForBurger.then(eatBurger)
```

## `resolve` and `then`
Whatever parameter passed into the `resolve` function, that value will get passed into the function parameter of the `then` function callback.

So from the example above:

```js
let askedForBurger = new Promise((resolve, reject) => { // the Executor function
  setTimeout(() => {
    if (kitchenOnFire) {
      reject('Kitchen is on Fire')
      return
    }
    let looksCouldKaleBurger = new Burger()
    resolve(looksCouldKaleBurger) //  >>>------ takes this value -----              
  }, 1000)                        //                                 |
})                                //                                 |
                                  //                                 |
const eatBurger = (burger) => {   // <<<----- to this burger param ---
  // burger's value is looksCouldKaleBurger                          |
  return new Promise((resolve, reject) => {   //                     |    
    setTimeout(() => {                        //                     | 
      resolve('mmm so good!')                 //                     | 
    }, 2000)                                  //                     | 
  }                                           //                     | 
}                                             //                     | 
                                              //                     | 
let ateBurger = askedForBurger.then(eatBurger)// <- because of this --
```

## `reject` and `catch`
Just like whatever is passed into `resolve` is available in the function passed into `then`, whatever is passed into `reject` is available in the function passed into `catch`.

## Chaining Promises
More often than not, Your async function need to call other async functions.  In order to chain your async function one after another, you need to return a new Promise object inside of the `then` callback.

From the previous code block, the `ateBurger` object has a `then` method on it, because the `eatBurger` returned a Promise.  You can do something like `ateBurger.then(complimentChef)`

> **Tip:** What I find useful is usually naming the Promise object in past tense.  And name the function you pass into the `then` method in present tense, signifying that it's an action ready to do something.

## Full Example
Scenario: You went to Bob's Burger restaurant.  You first **tell the waiter your food order**.  You wait for the food to come.  If it arrives, then you **eat the food**.  If the food is good, then you **finish eating the food**. Then you **go home happy**. If at any point, something goes wrong, you try to solve the problem or **go home sad**.

This is what the application code looks like:

```js
let toldWaiter = tellWaiterFoodOrder('Looks Could Kale Burger', 'Bob').catch(cannotOrderFood)
let foodArrived = toldWaiter.then(waitForFoodToCome).catch(cannotGetFood)
let finishedFood = foodArrived.then(eatFood).catch(cannotFinishFood)
finishedFood.then(goHomeHappy, goHomeSad)
```

Notices that without caring too much about the implementation details, the code almost becomes as readable as the english language.

For the full working example see [this jsFiddle](https://jsfiddle.net/howlowck/Lwhx9Lz8/) (Refresh to see different outcomes.)
