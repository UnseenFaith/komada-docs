# Extendables (added in 0.20.1)

This feature has been implemented in Komada **0.20.1**, they are functions
that extend current Discord.js classes by adding methods or properties.

Extendables have the following syntax:

```js
exports.conf = {
  type: "get",
  method: "postable",
  appliesTo: ["GroupDMChannel", "DMChannel", "TextChannel"],
};

// eslint-disable-next-line func-names
exports.extend = function () {
  if (!this.guild) return true;
  return this.readable && this.permissionsFor(this.guild.me).has("SEND_MESSAGES");
};
```

## Understanding exports.conf

```js
exports.conf = {
  type: "get",
  method: "postable",
  appliesTo: ["GroupDMChannel", "DMChannel", "TextChannel"],
};
```

- **conf.type**: The type of the extendable. They're either `get` (property) or `method` (method).
- **conf.method**: The name of the method/property.
- **conf.appliesTo**: An array of affected properties from Discord.js. You can get a list [here](https://github.com/hydrabolt/discord.js/blob/master/src/index.js).

## Understanding exports.extend

Due to the nature of extendables, you **can't** use [arrow functions](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions),
instead, the first line must be:

```js
exports.extend = function () { return "thing" }
```

## Examples

Imagine we want to extend the [Message](https://discord.js.org/#/docs/main/master/class/Message) class
so it has a method called `prompt` so you can do `Message#prompt("Are you sure you want to continue?")`
everywhere in your code, resolving if the user confirms the prompt, or rejecting otherwise. Then, your
extendable is likely to be like the following:

> You can extend the Message object with this because you're likely to lock the prompt for a user in a channel,
and Message has both properties of `author` and `channel`.

```js
exports.conf = {
  type: "method",
  method: "prompt",
  appliesTo: ["Message"],
};

// eslint-disable-next-line func-names
exports.extend = function () {
  return prompt();
};
```

Where `prompt()` is your prompt function.
