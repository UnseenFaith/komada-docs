# Creating your own Commands

New commands are created in the `./commands/` folder, where subfolders are
the categories offered in the help command. For instance adding `./commands/Misc/test.js`
will create a command named `test` in the `Misc` category. Subcategories can
also be created by adding a second folder level.

```js
exports.run = (client, msg, [...args]) => {
  // Place Code Here
};

exports.conf = {
  enabled: true,
  runIn: ["text"],
  aliases: [],
  permLevel: 0,
  botPerms: [],
  requiredFuncs: []
};

exports.help = {
  name: "name",
  description: "Command Description",
  usage: "",
  usageDelim: "",
  extendedHelp: ""
};
```
> Tip: If you need something created before the command is ever ran, you can specify
exports.init = (client) => {...} to make Komada run that portion of code beforehand.

`[...args]` represents a variable number of arguments give when the command is
run. The name of the arguments in the array (and their count) is determined
by the `usage` property and its given arguments.
