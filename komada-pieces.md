# Komada Pieces

So... yeah. since "komada" actually means "pieces" in Croatian, it means this pages is... "Pieces Pieces". So sue me, I'm not *that* original.

But seriously. Komada is built on a stack of multiple parts that work together to offer what we consider to be one of the simplest botmaking experience available in JavaScript. 

The various pieces available are: 

- [Commands](commands.md): Chat commands that generally respond with a message after taking some actions.
- [Functions](functions.md): JavaScript functions available throughout all others pieces. Can also be constructed as multi-function modules. 
- [Monitors](monitors.md): Code that can run on every message, whether or not it triggers a command. Useful for spam monitoring, swear filters, etc. 
- [Inhibitors](inhibitors.md): Code that runs on messages that trigger a command. May prevent a command from running. Core inhibitors check for user permissions, bot permissions, disabled commands, etc.
- [Providers](providers.md): Providers give access to databases to other pieces. Providers are all built with the same methods and properties and should be interchangeable. 
- [Event Handlers](event-handlers.md): Default handling for events. While Komada does not add any custom events, any normal discord.js event can be handled by simply creating a file.
- [Finalizers](finalizers.md): Code that run on messages after a successful command. This feature has been implemented in **Komada v0.20.0**.
- [Extendables](extendables.md): Code that acts passively, they're loaded before Discord.js classes are ever created. They add properties or methods to existing Discord.js classes.