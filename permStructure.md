# PermStructure (added in 0.20.1)

If you want to change the way permission levels are configured, you can use a new property: `permStructure`. You can set a permission structure with a range of 0-10. However, it only accepts an array of 11 objects, with the following format:

> Be careful! If you have assigned new **Komada.Client** to **client**, client will be already defined in upper scope. You can avoid that by assigning a generic name to `new Komada.Client` (like your bot's name).

```js
permStructure: [
  {
    check: () => true,
    break: false,
  },
  {
    check: () => false,
    break: false,
  },
  {
    check: (client, msg) => {
      if (!msg.guild) return false;
      const modRole = msg.guild.roles.find("name", msg.guild.conf.modRole);
      return modRole && msg.member.roles.has(modRole.id);
    },
    break: false,
  },
  {
    check: (client, msg) => {
      if (!msg.guild) return false;
      const adminRole = msg.guild.roles.find("name", msg.guild.conf.adminRole);
      return adminRole && msg.member.roles.has(adminRole.id);
    },
    break: false,
  },
  // ...
],
```

Which permLevel **0** always return `true` (everyone has this permission level), **1** always return `false`, **2** returns either `true` or `false`, depends if the condition is fulfilled or not.

You can also use `Komada.PermLevels` constructor, which is 'easier' to use. In that way, we just do:

```js
permStructure: new Komada.PermLevels()
  .addLevel(0, false, () => true)
  .addLevel(2, false, (client, msg) => {
    if (!msg.guild) return false;
    const modRole = msg.guild.roles.find("name", msg.guild.conf.modRole);
    return modRole && msg.member.roles.has(modRole.id);
  })
  .structure,
```

Any non-specified level will be fulfilled with functions that always return `false`.