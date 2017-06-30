# Creating Monitors

Monitors are special in that they will always run on any message. This is particularly
useful when you need to do checking on the message, such as checking if a message
contains a vulgar word (profanity filter). They are almost completely identical to
inhibitors, the only difference between one is ran on the message, and the other
is ran on the command. Monitors are loaded as core first, and if your code contains
a monitor of the same name it overrides the core monitor.

Their structure is identical to inhibitors, being the only difference is that you
don't pass a command parameter to them.

```js
exports.conf = {
  enabled: true,
  ignoreBots: false,
  ignoreSelf: false,
};

exports.run = (client, msg) => {
  // code here
};
```

> **NOTE**: `ignoreBots` and `ignoreSelf` properties were added on komada **0.18.8**.

## Configuration
- **enabled**: Represents if the inhibitor should be enabled or disabled, it must be a boolean. Set to false to completely disable this monitor, it cannot be forcefully enabled.
- **ignoreBots**: Set this to true if you want the monitor to ignore bots.
- **ignoreSelf**: Set this to true if you want the monitor to ignore the client user (the bot account, yourself if it's a selfbot).
