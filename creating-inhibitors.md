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
  spamProtection: false,
  priority: 7,
};

exports.run = (client, msg, cmd) => {
  if(ok) {
    return false;
  } else {
    return "Reason for Rejection";
  }
}
```
