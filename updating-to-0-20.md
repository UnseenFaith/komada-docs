# Breaking changes

## Our init file, app.js

Starting from your **app.js**, since this version is classbased now, the
way we configure our bots has been changed, remember this?

```js
const komada = require("komada");

komada.start({
  botToken: "your-bot-token",
  ownerID: "your-user-id",
  clientID: "the-invite-app-id",
  prefix: "+",
  clientOptions: {
    fetchAllMembers: true
  }
});
```

Now, your bot token **must** go in a separated function: `client.login`. And instead of
`komada.start`, we create a new instance of `Komada.Client` and assign it to any variable,
for example `client`, and with this variable, call the function login.

```js
const Komada = require("komada");

const client = new Komada.Client({
  ownerID: "your-user-id",
  clientID: "the-invite-app-id",
  prefix: "+",
  clientOptions: {
    fetchAllMembers: true,
  },
});

client.login("your-bot-token");
```

Additionally, if you want to change the way permission levels are configured, you
can use a new property: `permStructure`. You can set a permission structure with a
range of 0-10.

However, it only accepts an array of 11 objects, with the following format:

> Be careful! If you have assigned new **Komada.Client** to **client**, client
will be already defined in upper scope. You can avoid that by assigning a generic
name to `new Komada.Client` (like your bot's name).

```js
permStructure: [
  {
    check: () => true,
    break: false,
  },
  {
    check: () => false,
    break: false,
  },
  {
    check: (client, msg) => {
      if (!msg.guild) return false;
      const modRole = msg.guild.roles.find("name", msg.guild.conf.modRole);
      return modRole && msg.member.roles.has(modRole.id);
    },
    break: false,
  },
  {
    check: (client, msg) => {
      if (!msg.guild) return false;
      const adminRole = msg.guild.roles.find("name", msg.guild.conf.adminRole);
      return adminRole && msg.member.roles.has(adminRole.id);
    },
    break: false,
  },
  // ...
],
```

Which permLevel **0** always return `true` (everyone has this permission level), **1**
always return `false`, **2** returns either `true` or `false`, depends if the condition
is fulfilled or not.

You can also use Komada.PermLevels constructor, which is 'easier' to use. In that way, we just do:

```js
permStructure: new Komada.PermLevels()
  .addLevel(0, false, () => true)
  .addLevel(2, false, (client, msg) => {
    if (!msg.guild) return false;
    const modRole = msg.guild.roles.find("name", msg.guild.conf.modRole);
    return modRole && msg.member.roles.has(modRole.id);
  })
  .structure, // **Make the Komada.PermLevels' constructor return an array**
```

Any non-specified level will be fulfilled with functions that always return `false`.

## Commands

All commands **MUST** return an [Object Promise](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise),
you can do that by adding the `async` keyword to the function, or simply returning methods
that return a Promise, like `msg.send`. There's no need to change anything else.

If you return something, like a **Message** object, the variable `mes` from
the [finalizers](./finalizers.md) will be available and defined as whatever
the [command](./commands.md) returned.

## Log function

Do you use `client.funcs.log()` in your code? It's not a thing anymore in our code. We have changed
it a bit, it's now an event:

```js
client.emit("log", data, type);
```

It'll execute the event `log` from komada's core folder, **events**. `data` is the data you want it
to print, while `type` is one of the following:

- **debug**: Prints a log with a magenta timestamp. (Emits console.log)
- **warn**: Prints a log with a yellow timestamp. (Emits console.warn)
- **error**: Prints a log with a red timestamp. (Emits console.error)
- **log**: Prints a log with a blue timestamp. (Emits console.log)

If `type` is not assigned, it'll be assigned to **log** by default.

Additionally, you have the following:

```js
client.emit("error", data);
client.emit("warn", data);
```

## Permissions

`Message#hasAtleastPermissionLevel(<0-10>)` is an extendable for the Message object from Discord.js
in which loops the permission structure. It returns a `Boolean` value (true/false): `true` if the
author of the message has at least the permission level, `false` otherwise.

Additionally, you can check all commands a User can run with `Message#usableCommands`. This extendable
returns a [Collection](https://discord.js.org/#/docs/main/master/class/Collection) of commands the
author of the message can run, also, it runs all inhibitors in every command.

# New features

## Finalizers

They are functions that are run after a successful command. Check [finalizers](./finalizers.md).

## Cooldown

Cooldown inhibitors are something pretty popular within Komada, so we implemented a set of
finalizer-inhibitor, in which the cooldown is applied after a successful command, and the
inhibitor prevents the command from working while the cooldown is active on the user. To use
that, you must set in `exports.conf.cooldown` an integer in seconds.

## Editable Commands

You send a message and your bot runs a command. Then you edit your message and the bot edits the
response. This feature requires the property `cmdEditing` from your Komada configs set to `true`.

To send 'editable commands', you have to do something: change `msg.channel.send("Hello World");` to
`msg.send("Hello World");`, and now, you have an editable command, it means, Komada will cache both
triggerer (the message which triggered the command) and the response. When you edit a message, Komada
will check if the message exists in the cache with a response, if it exists, it'll edit the message
rather than sending a new one.

Additionally, you can use: `Message#sendMessage`, `Message#sendEmbed` and `Message#sendCode`.

> `Message#sendFile` and `Message#sendFiles` are not available because you can't edit the attachments
of a message after it's send.

> Do you miss the discord.js aliases to send messages? We extended the `Channel` object so you can use
`Channel#sendMessage`, `Channel#sendCode`, `Channel#sendEmbed`, `Channel#sendFile` and `Channel#sendFiles`
without deprecation warnings.
