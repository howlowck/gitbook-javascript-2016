# Module Importing and Exporting

## Brief History

### Pre-NodeJS
The idea of module loading and dependency management is not a new concept in programming.  For a long time in the javascript community, it seemed that developers weren't overly concerned with module loading.  

This lack of attention to module loading is likely due to the fact that variables can easily be loaded, and made available in the global context, and libraries like jQuery and Prototype encouraged developers to monkey-patch and add methods to its prototype in ways of extending the library.  YUI did have module loading but most developers were like  ¯\\\_(ツ)\_/¯

NodeJS came up around 2009, soon release with it `npm` or Node Package Manager.  In node, it allowed a special function, `require()`, which looks up modules that are installed to the local project via the `npm` command-line tool.  

Unfortunately, NodeJS and Npm was for the server, so developers were left out in the cold.
![sad](../assets/sad.gif)

This is NodeJS's **CommonJS** syntax looks like:
```js
var $ = require('underscore');
var react = require('react');
```

### Dawn of Client-side module loading

Soon after NodeJS, [RequireJS](http://requirejs.org/) was released in early 2010, bringing the ability to load external and internal modules into your javascript project.

The huge advantage of RequireJS was its ability to lazy load modules.  This means that until a piece of code was "required" by RequireJS, it won't be loaded in the browser.  When it *is* needed, RequireJS injects a `<script>` tag with the code to load it into the browser, then executes the code that requires the particular module.

This is what the RequireJS's **Asynchronous Module Definition (AMD)** syntax looked like
```js
requirejs(['jquery', 'underscore', 'app/modules/user'], function ($, _, user) {
  
})
```
In my experience, this kind of script loading can quickly get out of hand; And to me, the AMD syntax is not as readable as the CommonJS way.  

However, lazy-loading was seen as the way to go on the browser because lazy-loading means faster initial load time.  And developers can seamlessly develop the js app without any compile or render step.

### Browserify and Isomorphic/Universal Javascript Apps

More and more people in the JS community started to realize the advantages of running Javascript on both the server and client.  (Write Validation Rules only ONCE?!)  There needed a way to unify module loading between the server and the browser.

Around 2011, [Browserify](http://browserify.org/) was released which allows CommonJS way of loading modules in the browser.

Browserify bundled all the dependencies into one `bundle.js` file, resulting in a larger initial page load, *and*, because of the bundling process, browserify requires the extra step in order to load in the browser.  Despite those shortcomings, much of the JS community applauded the fact that CommonJS can be used to write client-side javascript.

![cheer](../assets/cheer.gif)
