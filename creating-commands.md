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

**Non-obvious options**:
- **enabled**: Set to false to completely disable this command, it cannot be forcefully enabled.
- **runIn**: Array of Message Channel Types that the command can be run in.
- **aliases**: Array of aliases for the command, which will *also* trigger it.
- **permLevel**: Permission level, controlled via `./functions/permissionLevel.js`.
- **selfbot**: Set to true to only load this command if the bot is configured to be a selfbot.
- **botPerms**: An array of permission strings (such as `"MANAGE_MESSAGES"`) required for the command to run.
- **requiredFuncs**: An array of function names required for this command to execute (dependency).
- **usage**: The usage string as determined by the Argument Usage (see below).

## New Extended Help Feature : 0.14.9
The new extended help feature allows you to go more in detail with your commands for your users.
This allows you specify extra information that couldn't make it into the description, examples on how to
use the command, or whatever your heart desires. Here's a good example of what an extended usage could look like.
```
extendedHelp: "**Usage Explained**

spambot.conf set <key> <new_value> to change the value of a key. The value should match the key type.
spambot.conf get <key> to get the current key value.
spambot.conf reset <key> to reset the key to the default value.
spambot.conf list to see all current configuration elements

**Example Configurations**

spambot.conf set banLevel 5 :: Sets the bot's ban level to 5 mentions (default is 10)
spambot.conf reset banLevel :: Resets the ban_level key to the default value (10)
spambot.conf set modRole @Admin :: Sets the moderator role to the Admin role (By Mention or ID, not by name)`
};"
```

#### Command Arguments

**Usage Structure**

`<>` required argument, `[]` optional argument
`<Name:Type{min,max}>`

- **Name** Mostly used for debugging message, unless the type is Literal in which it compares the argument to the name.
- **Type** The type of variable you are expecting.
- **Min, Max** Minimum or Maximum for a giving variable (works on strings in terms of length, and on all types of numbers in terms of value) You are allowed to define any combination of min and max. Omit for none, `{min}` for min, `{,max}` for max.
- **Special Repeat Tag** `[...]` will repeat the last usage optionally until you run out of arguments. Useful for doing something like `<SearchTerm:str> [...]` which will allow you to take as many search terms as you want, per your Usage Delimiter.

**Usage Types**

- `literal` : Literally equal to the Name. This is the default type if none is defined.
- `str`, `string` : Strings.
- `int`, `integer` : Integers.
- `num`, `number`, `Float` : Floating point numbers.
- `boolean`, : A true or false statement.
- `url` : A URL.
- `msg`, `message` : A message object returned from the message ID (now using fetchMessage as of d3d498c99d5eca98b5cbcefb9838fa7d96f17c93).
- `role` : A role object returned from the role ID or mention.
- `channel` : A channel object returned from the channel ID or channel tag.
- `guild` : A guild object returned from the guild ID.
- `user`, `mention` : A user object returned from the user ID or mention.
