# Finalizers (added in 0.20.0)

This feature has been implemented in Komada **0.20.0**, they are functions run after
successful commands, and this is the reason of why all commands **must** return an
[Object Promise](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise).

Finalizers have the following (full) syntax:

```js
exports.run = (client, msg, mes, start) => {
  // code
};
```

## Arguments:

- **client**: The client object.
- **msg**: The message object.
- **mes**: The value the command returns.
- **start**: The time in which the command has been run, by `performance.now()`, ideal for benchmarking.

## Existing finalizers

Komada has two preinstalled finalizers: `commandCooldown` and `commandlogging`.

### commandCooldown

This finalizer applies the cooldown from the commands' `exports.conf.cooldown` (if
exists and its value is above `0`).

### commandlogging

This finalizer, unlike commandCooldown, it's only run if the property `cmdLogging` of
your Komada's configs is set to `true`. It prints in the cmd prompt the command run, where,
the user who ran it, and the time it took to process the command.