# Async in Redux

Because Redux was built to be as thin and simple as possible with only a handful of concepts, it was never supposed to be an opinionated framework.  

Redux offers a handful of functions to allow predictable state management.  Its creator, Dan Abramov, encourages the community to build extensions on top of Redux and hook into Redux with its middleware mechanism.

One big gap in Redux is dealing with async functionalities.

One big concept used throughout Redux is the idea of **pure functions**. Since, async functions are technically side-effects, Redux and async functions seems to be water and oil.  Fortunately, people have came up with ways to combat that perception and use modern JS practices to make async functions in Redux as painless as possible.
