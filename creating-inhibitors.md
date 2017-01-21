# Creating Inhibitors

Inhibitors are only ran on commands. They are used to check a variety of conditions
before a command is ever ran, such as checking if a user has the right amount of permissions
to use a command. Inhibitors are loaded as core first, and if your code contains a inhibitor
of the same name it overrides the core inhibitor.

Their structure is restricted, meaning to work they must be defined exactly like the following example. They *must* `resolve()` to let a command run, or `reject("reason")` to prevent it from running.

```js
exports.conf = {
  enabled: true,
  spamProtection: false,
};

exports.run = (client, msg, cmd) => {
  return new Promise( (resolve, reject) => {
    if(ok) {
      resolve();
    } else {
      reject("Reason for Rejection");
    }
  });
}
```

