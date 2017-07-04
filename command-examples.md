# Command examples

The following example is the [Ping Command](https://github.com/dirigeants/komada/blob/master/commands/System/ping.js),
a core command that comes by default when you install/download Komada:

```js
exports.run = async (client, msg) => {
  const message = await msg.channel.sendMessage("Ping?").catch(err => client.funcs.log(err, "error"));
  message.edit(`Pong! (took: ${message.createdTimestamp - msg.createdTimestamp}ms)`);
};

exports.conf = {
  enabled: true,
  runIn: ["text", "dm", "group"],
  aliases: [],
  permLevel: 0,
  botPerms: [],
  requiredFuncs: [],
};

exports.help = {
  name: "ping",
  description: "Ping/Pong command. I wonder what this does? /sarcasm",
  usage: "",
  usageDelim: "",
};
```

Seems clear, right? You trigger this command by doing `ping` (with your prefix),
and it runs an async function that sends a message and edits it showing the time
it took to send the message. In the `exports.conf` we know that:

- The command is enabled.
- The command can be run in `text`, `dm` and `group` channel types.
- The command has no aliases, it'll run only by doing `ping`.
- The permLevel is 0, it means, everyone can use it.
- The bot doesn't require any special permissions for it.
- The bot doesn't require any external function for it.
- The command has no arguments.
- The command has no cooldown (0 seconds).

(and neither has extendedHelp, do you need it for a ping command?)

When you do `help`, the help command will show you *Ping/Pong command. I wonder what this does? /sarcasm*
next to the command name, *ping*.

Now, we want a command with an argument, we will take this one as example:
[spy.js](https://github.com/dirigeants/komada-pieces/blob/master/commands/Misc/spy.js),
from the GitHub repo [komada-pieces](https://github.com/dirigeants/komada-pieces):

```js
exports.run = (client, msg, [ugc]) => {
  const util = require("util");
  ugc = util.inspect(ugc, { depth: 0 });
  msg.channel.sendCode("xl", client.funcs.clean(client, ugc));
};

exports.conf = {
  enabled: true,
  runIn: ["text"],
  aliases: [],
  permLevel: 3,
  botPerms: [],
  requiredFuncs: [],
};

exports.help = {
  name: "spy",
  description: "Spies on a user, guild, or channel",
  usage: "<role:role|msg:msg|user:user|guild:guild|channel:channel>",
  usageDelim: "",
};
```

This command has one arguments, but accepts different types of it. We can know that:

- The command is enabled.
- The command can be run only in `text` channel type (guild only).
- The command has no aliases, it'll run only by doing `spy <argument>`.
- The permLevel is 3, it means, by default, only administrators and the owner of
the guild can run this command.
- The bot doesn't require any special permissions for it.
- The bot doesn't require any external function for it.
- The command has one argument, with multiple usage types on it.

## That's all!

You can ask us questions by joining our [Discord channel](https://discord.gg/dgs8263). And you can also check out our [komada-pieces](https://github.com/dirigeants/komada-pieces) GitHub repo for command examples provided by devs who used [komada](https://github.com/dirigeants/komada) (we also accept PRs from external collaborators, just read the rules written in the readme.md).
