# Creating Inhibitors

Inhibitors are only ran on commands. They are used to check a variety of conditions
before a command is ever ran, such as checking if a user has the right amount of permissions
to use a command. Inhibitors are loaded as core first, and if your code contains a inhibitor
of the same name it overrides the core inhibitor.

Their structure is restricted, meaning to work they must be defined exactly like
the following example. They *must* return `false` to let a command run, or `return "reason"`
to prevent it from running. Since **0.17.10**, inhibitors can also be silent, by
returning `true` instead of a string.

```js
exports.conf = {
  enabled: true,
  priority: 7,
};

exports.run = (client, msg, cmd) => {
  if(ok) {
    return false;
  }
  return "Reason for Rejection";
};
```

## Configuration
- **enabled**: Represents if the inhibitor should be enabled or disabled, it must be
a boolean. Set to false to completely disable this inhibitor, it cannot be forcefully enabled.
- **priority**: The priority in which the inhibitor should be run. When Komada
runs the inhibitors, it runs the ones with higher priority.

**Core Inhibitors**
Sorted by priority:
- **10**: permissions.
- **9**: disable.
- **8**: runIn.
- **7**: missingBotPermissions.
- **6**: requiredFuncs.
