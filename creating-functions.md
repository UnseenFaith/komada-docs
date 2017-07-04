# Creating Functions

Functions are the second thing loaded, every other piece can access them (with
exception of events at startup). Functions are loaded as core first, and if your
code contains a function of the same name it overrides the core function.

Their structure is somewhat freeform, in that they can contain a single function,
or they may be a module composed of more than one functions as a module (. It's
not supposed to, but let's keep it between you and me, alright?

```js
module.exports = (str) => {
  return str.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase());
};
```

The arguments are arbitrary - just like a regular function. It may, or may not,
return anything. Basically any functions. You know what I mean.

## Accessing Functions

Functions are stored in the main `client` object, in the `funcs` property. This has a property for each function added, based on its filename. So for example if you have `./functions/myFunc.js` , you can access it through `client.funcs.myFunc(arguments)`. If you use `exports.thing = "blah";` then you would access that rather from `client.funcs.myFunc.thing;`.

For more details on modules, see [this nice little article I've found that describes it well](https://www.hacksparrow.com/node-js-exports-vs-module-exports.html).

## Komada-Pieces

If you want to PR a function to Komada-Pieces, make sure you PR it with the following format:

```js
module.exports = (str, l) => {
  const x = str.substring(0, l).lastIndexOf(" ");
  const pos = x === -1 ? l : x;
  return str.substring(0, pos);
};

module.exports.conf = { requiredModules: [] };
module.exports.help = {
  name: "splitText",
  type: "functions",
  description: "Find the last space of a string and cuts it down to a manageable size for use in Discord.",
};
```

So we can download it with the `download` command. Only change is defining the function as `func` instead of assigning it to `module.exports`, and in `func`, apply both objects with the properties written in the example above.