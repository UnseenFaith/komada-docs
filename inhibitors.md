# Inhibitors

Inhibitors run on messages that are confirmed to be a bot command - the prefix
has been detected and the command has found. They can be used to *stop* a command
from running depending on circumstances.

Default inhibitors include checking if a user has permissions, whether other pieces
are missing, the bot doesn't have permission to execute a command... etc. However,
you can create your own and custom inhibitors [here](creating-inhibitors.md), such
as an inhibitor that prevents some commands to be run in certain channels.

For instance, you can *extend* [commands](commands.md)' exports.conf object by
adding more properties, such as `ratelimit: 5`, and you access to it by doing
`cmd.conf.ratelimit` (for example).
