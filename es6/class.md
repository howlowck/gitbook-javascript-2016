# the `class` keyword

Javascript is, by its nature, an Object-orientated language. 

However, its inheritance paradigm is not class-based like Python, PHP, Java, etc, which are what computer science students learn in school.  

Javascript uses [prototypal inheritance](TODO).  So when ES6 proposed the keyword `class` as a way to define an constructor function (object), there was A LOT of pushback.  People who understood the power of prototypal inheritance says that using the `class` keyword will be misleading for people who are new to the language (some suggesting using the keyword `type` instead).

See all the outrage:
* [How to Fix the ES5 `class` keyword](https://medium.com/javascript-scene/how-to-fix-the-es6-class-keyword-2d42bb3f4caf#.8274bv6xs)
* [Does Javascript need classes](https://www.nczonline.net/blog/2012/10/16/does-javascript-need-classes/)
* [Two Pillars of Javascript](https://medium.com/javascript-scene/the-two-pillars-of-javascript-ee6f3281e7f3#.ap0laqkcy)

the `class` keyword is simply syntactic sugar for creating an object (constructor function) that should be instantiated or extended by another object.

## Resources
* [Nicolas Zakas' Principles of Object Orientated Javascript - Chapter 5](https://www.amazon.com/Principles-Object-Oriented-JavaScript-Nicholas-Zakas/dp/1593275404%3F)
* [ES6-feature](http://es6-features.org/#ClassInheritance)
* [MDN on Javascript inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
