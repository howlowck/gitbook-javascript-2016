## JSX

Perhaps the most jarring of changes is a new way to write XML inside your Javascript app.  This syntax is called JSX.


Here is some snippet from the [React site on JSX](https://facebook.github.io/react/docs/jsx-in-depth.html)
```js
<Greet color="blue" shadowSize={2}>
  Hi {name}!
</Greet>
```
is the exact same as
```js
React.createElement(
  Greet,
  { color: "blue", shadowSize: 2 },
  "Hi ",
  name,
  "!"
)
```

As you can see, while JSX is just syntactic sugar, but that sugar is oh so sweet.  
Jsx makes defining and utilizing React components so much easier.

## Jsx is NOT a template language
While JSX looks like a new templating language, it's important to remember that JSX is just Javascript.

You can do everything you want in Javascript with JSX.  The only part that looks different is you can now write XML.
