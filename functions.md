# Functions

Functions are as their name suggest:
[functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function).
They are pretty useful to run a "chunk" of code that is used in multiple pieces.
In Komada, functions are available globally anywhere the `client` variable is,
under `client.funcs.functionName()`

Komada has a lot of preinstalled functions such as `toTitleCase()`, in which allows
you to convert a string to title case. There's also something that you'd like to use:
The [log function](https://github.com/dirigeants/komada/blob/master/functions/log.js),
it takes two parameters, being the first the data, and the second the type of logs
(they are `debug`, `warn`, `error` and `log`, if undefined, it'll use `log`). Due
to this, they are perfect to debug. Since **0.18.5** (indev) they give error stacks.
And even inspect the data if it's an object.

Functions have the following syntax:

```js
module.exports = (...args) => {
  // code
};
```

You use them like you do with a normal function. `...args` represents a variable
number of arguments you want to work with. And the code must `return` something.
(Same you do with functions).
