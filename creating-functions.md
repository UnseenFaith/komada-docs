# Creating Functions

Functions are the second thing loaded, every other piece can access them (with
exception of events at startup). Functions are loaded as core first, and if your
code contains a function of the same name it overrides the core function.

Their structure is somewhat freeform, in that they can contain a single function,
or they may be a module composed of more than one functions as a module. It's
not supposed to, but let's keep it between you and me, alright?

```js
module.exports = (str) => {
  str.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase());
};
```

The arguments are arbitrary - just like a regular function. It may, or may not,
return anything. Basically any functions. You know what I mean.
