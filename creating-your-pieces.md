# Creating your own Pieces

Essentially, the way Komada works is that we have *core* pieces (functions, events, commands, etc.) loaded automatically.
But you can add your own pieces easily by adding files to your *local* folders (which are created on first load).

These pieces are:
- **commands** which add in-chat functionality to your bot.
- **functions** which can be used by other pieces or anywhere in the bot.
- **inhibitors** which are used to check if a command should be run or not.
- **monitors** which are used to check a message before it's a command.
- **events** which are triggered based on what happens in Discord.
- **providers** which are database connectors.
- **methods** which are native Discord.js functions.
- **finalizers** which are functions run after a successful command.

> Finalizers have been added to Komada **v0.20.0**.
