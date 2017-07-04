# Command Arguments

This is a full guide that explains how a command is configured step-by-step, also extended with [examples](command-examples.md).

# Understanding exports.conf

```js
exports.conf = {
  enabled: true,
  runIn: ["text"],
  aliases: [],
  permLevel: 0,
  botPerms: [],
  requiredFuncs: [],
  cooldown: 30,
};
```

## Properties
- **enabled**: Represents if the command should be enabled or disabled, it must be a boolean. Set to false to completely disable this command, it cannot be forcefully enabled.
- **runIn**: Represents the type of channels where the command can run in. It must be an array, channel types are at: [Channel.type](https://discord.js.org/#/docs/main/stable/class/Channel?scrollTo=type).
- **aliases**: Represents aliases or alternative names that can trigger the command. Must be an array.
- **permLevel**: Represents the level of permissions the user should have to run this command. Must be an integer, by default, 10 means the owner of the bot, set as the ID you have set in `ownerID` when you created the file to configure and initiate Komada.
- **botPerms**: Represents an array of strings with all [Discord permissions](https://discord.js.org/#/docs/main/stable/typedef/PermissionResolvable) in which your bot requires to run this command (such as `"MANAGE_MESSAGES"`).
- **requiredFuncs**: Represents an array with all functions your bot requires to run this command. They are present on [komada-pieces](https://github.com/dirigeants/komada-pieces) GitHub repo.
- **cooldown**: Amount of time in seconds for the command cooldown. They are per-user and affects globally. The cooldown is **not** applied when the command fails, but in success.
- **selfbot**: Additionally, there's a property called selfbot, must be a boolean. Set to true to only load this command if the bot is configured to be a selfbot.

> Note: About **aliases**, if you have a command called ping, and you set "pong" as an alias inside the aliases array, both ping and pong will trigger the same command.

# Understanding exports.help

```js
exports.help = {
  name: "name",
  description: "Command Description",
  usage: "",
  usageDelim: "",
  extendedHelp: "",
};
```

## Properties
- **name**: Represents the name of the command. It's the key for the command inside the Collection `client.commands`.
- **description**: Represents a short information of the command, in which is shown in the help message.
- **usage**: Represents all arguments for the command.
- **usageDelim**: The character or combination of characters you want to separate the arguments with.
- **extendedHelp**: This feature allows you to go more in detail with your commands for your users. This allows you specify extra information that couldn't make it into the description, examples on how to use the command, or whatever your heart desires. If it's not defined, it'll return `No extended help available.` when using the `help` command with a defined command. (Such as `help transfer`).

> Note: `extendedHelp` feature was added in komada **0.14.9**.

Once you have created your command, you might want to add some arguments to it, that's what `usage` is designed for: you insert your commands arguments inside.

Usage is a `string` in which contains different tags, and it's written in every file like the following one:

## Usage Structure

`<>` required argument, `[]` optional argument `<Name:Type{min,max}>`

- **Name** Mostly used for debugging message, unless the type is Literal in which it compares the argument to the name.
- **Type** The type of variable you are expecting.
- **Min, Max** Minimum or Maximum for a giving variable (works on strings in terms of length, and on all types of numbers in terms of value) You are allowed to define any combination of min and max. Omit for none, `{min}` for min, `{,max}` for max. If you set `min` and `max` with the same integer, then the provided string must have equal length.
- **Special Repeat Tag** `[...]` will repeat the last usage optionally until you run out of arguments. Useful for doing something like `<SearchTerm:str> [...]` which will allow you to take as many search terms as you want, per your Usage Delimiter.

> Note: You can set multiple options in an argument by writting `|`. For example: `<Message:msg|Content:string{4,16}>` will work when you provide a message ID or a string with a length between 4 and 16 (including both limits).

### Usage Types

|                         Type | Description
| ---------------------------: | -----------
|                    `literal` | Literally equal to the Name. This is the default type if none is defined.
|            `str` \| `string` | A [String](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String).
|           `int` \| `integer` | An [Integer](https://en.wikipedia.org/wiki/Integer).
| `num` \| `number` \| `float` | A [Floating Point Number](https://en.wikipedia.org/wiki/Floating-point_arithmetic).
|                    `boolean` | A [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean).
|                        `url` | A [URL](https://en.wikipedia.org/wiki/URL).
|           `msg` \| `message` | A [Message](https://discord.js.org/#/docs/main/master/class/Message) instance returned from the message ID.
|                       `role` | A [Role](https://discord.js.org/#/docs/main/master/class/Role) instance returned from the role ID or mention.
|                    `channel` | A [TextChannel](https://discord.js.org/#/docs/main/master/class/TextChannel) instance returned from the channel ID or channel tag.
|                      `guild` | A [Guild](https://discord.js.org/#/docs/main/master/class/Guild) instance returned from the guild ID.
|          `user` \| `mention` | A [User](https://discord.js.org/#/docs/main/master/class/User) instance returned from the user ID or mention.
|                     `member` | A [GuildMember](https://discord.js.org/#/docs/main/master/class/GuildMember) instance returned from the member ID or mention.

> Note: `Literal` is very useful in arguments with multiple options.

___

# Using arguments in your command.

Now, after we understand how to configurate the command, we'll start writting it:

```js
exports.run = async (client, msg, [...args]) => {
  // Place Code Here
};
```

`[...args]` represents a variable number of arguments give when the command is run. The name of the arguments in the array (and their count) is determined by the `usage` property and its given arguments.

> Note that the commands' arguments are an array. This is a trick called [Destructuring assignment](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

For example, when you have:

```js
exports.help = {
  name: "messager",
  description: "Deletes a message, or edits it.",
  usage: "<Message:msg> <delete|edit> [newContent:string]",
  usageDelim: "|",
  extendedHelp: "",
};
```

Then, we have to define all the arguments from *help.usage*, the following code block is an example of how it would look like, and how we would work with them.

```js
exports.run = async (client, msg, [message, action, newContent]) => {
  // code
};
```

In which `message` is the argument assigned to the message object as provided in `<Message:msg>` argument from usage. Same does `action` for `<delete|edit>` and respectively.

> Keep in mind that we declared `newContent` as an optional argument, if it's not provided, it'll return undefined.

Keep in mind that arguments are delimited by the character or combination of characters written in *help.usageDelim*. In this case, we have assigned the character `|` for it. How do we use this command? Easy:

`komessager 293107496191655936|delete`

The line above will execute the command with the name `messager` (or a command with `messager` as an alias), it'll use [Channel.fetchMessages](https://discord.js.org/#/docs/main/stable/class/TextChannel?scrollTo=fetchMessage) (or [Channel.fetchMessages](https://discord.js.org/#/docs/main/stable/class/TextChannel?scrollTo=fetchMessages) if the bot is a userbot). If the message is not found (you mistyped it or the message is in another channel) it'll warn you that the message hasn't been found. The next argument is a literal, in which must be either `delete` or `edit`. Keep in mind that Komada does *String.toLowerCase()*, if you write `DELETE` or any other variation of [font case](https://techterms.com/definition/font_case), it'll work too.

We come back to the `exports.run`, remember that we have:

```js
exports.run = async (client, msg, [message, action, newContent]) => {
  // code
};
```

As I explained before, `message` will return a message object, it'll be the message found with the ID `293107496191655936`, and `action` is defined as the string `delete`.
`newContent` is undefined because we didn't write that argument. The code inside the curly brackets (`{}`) will be executed when the usage is valid.

As a reminder from [Creating Commands](creating-commands.md):

> If you need something created before the command is ever ran, you can specify `exports.init = (client) => {...}` to make Komada run that portion of code beforehand.

Still hard to understand? Maybe you'll get it on [Examples](command-examples.md) page.
