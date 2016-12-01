# Module Importing and Exporting

## Brief History

### Pre-NodeJS
The idea of module loading and dependency management is not a new concept in programming.  For a long time in the javascript community, however, it seemed that developers weren't overly concerned with module loading.  

This lack of attention to module loading is likely due to the fact that variables can easily be loaded, and made available in the global context, and libraries like jQuery and Prototype encouraged developers to monkey-patch and add methods to its prototype in ways of extending the library.  

> _**Note:**_ YUI (Yahoo UI) did have module loading but most developers were like  ¯\\\_(ツ)\_/¯ ~meh~

### NodeJS and CommonJS

NodeJS came out around 2009, and soon released with it Node Package Manager (`npm`), an command-line tool.  In NodeJS, it allowed a special function, `require()`, which looks up modules that are installed to the local project via `npm`.  

Unfortunately, NodeJS and NPM was for the server, so front-end developers were left out in the cold.
![sad](../assets/sad.gif)

This is NodeJS's **CommonJS** syntax:
```js
var $ = require('underscore');
var react = require('react');
```

### Dawn of Client-side module loading

Soon after NodeJS, [RequireJS](http://requirejs.org/) was released in early 2010, bringing the ability to load external and internal modules into your javascript project.

The huge advantage of RequireJS was its ability to lazy load modules.  This means that until a piece of code was "required" by RequireJS, it won't be loaded in the browser.  When it *is* needed, RequireJS injects a `<script>` tag with the code to load it into the browser, then executes the code that requires the particular module (much like how JSONP works).

This is what the RequireJS's **Asynchronous Module Definition (AMD)** syntax looked like
```js
requirejs(['jquery', 'underscore', 'app/modules/user'], function ($, _, user) {
  
})
```
> _**Opinion:**_ In my experience, AMD's way of script loading can quickly get out of hand with increasing number of dependencies; And to me, AMD is not as readable as CommonJS.  

Lazy-loading and AMD was seen as the way to go on the browser because lazy-loading means faster initial load time.  Also developers can seamlessly develop their js app without any compile or render step.

### Browserify and Isomorphic/Universal Javascript Apps

More and more people in the JS community started to realize the advantages of running Javascript on both the server and client.  (Realtime App *and* Write validation rules only ONCE?!) The community needed a way to unify module loading between the server and the browser.

Around 2011, [Browserify](http://browserify.org/) was released which allows CommonJS way of loading modules in the browser.

Browserify, unlike RequireJS, bundled all the dependencies into one `bundle.js` file, resulting in a larger initial page load, *and*, because of the bundling process, browserify requires the extra step in order to load in the browser.  

Despite those shortcomings, much of the JS community applauded the fact that CommonJS can be used to write client-side javascript.  
![cheer](../assets/cheer.gif)

### ES6 and the import/export syntax
In 2014, ES6 (was still called ES6, not ES2015) finalized its module loading syntax.  The goal of the import/export syntax was to again unify the Javascript community with one syntax that would rule them all.

The goal of import/export functionality is to be as concise and readable as CommonJS, and allow asynchronous module loading that's more suited for the browser.

It's the best of both worlds!

## `export` and `import` syntax

This is what the **`export`** syntax looks like:  

```js
// Coder module named Coder.js
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min;
}

class Coder {
  constructor(name) {
    this.name = name
    this.energy = getRandomInt(3, 7)
  }
  drinkCoffee() {
    this.energy += getRandomInt(2,5)
  }
  doWork() {
    this.energy -= 1
  }
  isTired() {
    return this.energy <= 0
  }
  reportStatus() {
    if (this.isTired()) {
      this.drinkCoffee()
      return this.name + ' is drinking coffee.'
    }
    this.doWork()
    return this.name + ' is coding.'
  }
}

export default Coder
```

This is what the **`import`** syntax looks like:

```js
import Coder from './Coder' // the ./ looks for the file (with .js extension) in the current directory

var vince = new Coder('Vince')
vince.reportStatus() // returns 'Vince is coding'
vince.reportStatus() // returns 'Vince is coding'
vince.reportStatus() // returns 'Vince is drinking coffee'
```

## Resource
* [Overview of the topic](http://www.2ality.com/2014/09/es6-modules-final.html)
