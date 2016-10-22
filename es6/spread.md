# Spread Operator

Spread Operator, as the name suggests, spread its elements into literal elements or function properties.  We will see the spread operator used a lot when we start using React.

Example:
```js
var techTeam = ['Dennis', 'Vince', 'Ross', 'Chris', 'Hao']

var cloneTechTeam = [...techTeam]

// cloneTeachTeam now has ['Dennis', 'Vince', 'Ross', 'Chris', 'Hao'], same values as techTeam
// however techTeam !== cloneTechTeam , simply a clone.

```

## Uses for the Spread Operator

I briefly mentioned that mutating objects leads to side-effects and bugs.  As we get more into Redux, we will reenforce that concept even more.  

Instead of mutating arrays, we can use the spread operator (and some array functions) to create a new array which leaves the original array alone.

### Concatenate/Append to an array
Instead of `array.push()` which mutates the array, we can use the spread operator like so:

```js
var techTeam = ['Dennis', 'Vince', 'Ross', 'Chris', 'Hao']
var newTeam = [ ...techTeam, 'Brett']

// OR use an array function that creates a new array
var newTeam = techTeam.concat('Brett')
```

### Remove Item from an array from an index

```js
var tasks = ['Better Logs', 'Implement EnvVar', 'Migrate DB', 'Build Email Micro-service']

// Removes 'Migrate DB' from tasks
var indexOfMigrateDB = 2;
var tomorrowTasks = [...tasks.slice(0, indexOfMigrateDB), ...tasks.slice( indexOfMigrateDB + 1 )]
```

### Change a property value in an object

```js
var hao = {
  name: 'Hao',
  gender: 'male',
  age: 28
}

var newHao = {
  ...hao,
  age: 29
}

// newHao = {
//   name: 'Hao',
//   gender: 'male',
//   age: 29
//}

```

## Resource
* [MDN on the topic](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)
