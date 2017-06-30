# Creating Event Handlers

Events are placed in `./events/` and their filename must be `eventName.js`. If a conflicting event is present in both the core and your client, *both* are loaded and will run when that event is triggered.

Their structure is the following:

```js
exports.run = (client, ...args) => {
  // event contents
};
```

Where `...args` are arguments you would *normally* get from those events. For example, while the `ready` event would only have `client`, the `guildMemberAdd` event would be `client, member`.