# Examples

[`SettingGateway`](../settingGateway.md) might be confusing for some developers, this is a guide of **how to use it correctly**.

___

## Change the Provider Engine

The greatest feature from SettingGateway is not just its stability, you can *switch* the provider from JSON to another. I want to use my RethinkDB provider to store my guild settings? As easy as adding `config.provider.engine = "rethinkdb"`:

```js
const client = new Komada.Client({
  ownerID: "",
  prefix: "k!",
  clientOptions: {},
  provider: { engine: "rethinkdb" },
});
```

___

## Adding a key to the schema

When you start using Komada, it'll use 4 keys: `prefix`, `adminRole`, `modRole` and `disabledCommands`. But what if... I want to add a new key, called `users`, which can store multiple ids, and then check if a user is in said list to prevent them from running commands.

**Solution**:

```js
client.schemaManager.add("users", { type: "User", array: true }, true);
```

> Check the `add` method from [`schemaManager`](schemaManager.md).

___

## Editing Guild settings

I have created a key, now I want to edit it. For example, I dislike the built-in `conf` command and I want to make one. But now, I want to update the `prefix` value assigned to my Guild to `k!`.

**Solution**:

```js
client.settingGateway.update(msg.guild, { prefix: "k!" });
```

> Check the `update` method from [`settingGateway`](../settingGateway.md)

___

Now I want to add more users to my `users` key! I want to add the user `242043489611808769` to that array.

**Solution**:

```js
client.settingGateway.updateArray(msg.guild, "add", "users", "242043489611808769");
```

> Check the `updateArray` method from [`settingGateway`](../settingGateway.md)

___

## Removing a key from the schema

But it turns out you added that key but it wasn't useful, so you want to remove it, so you want to remove the key `users`.

**Solution**:

```js
client.schemaManager.remove("users", true);
```

> Check the `remove` method from [`schemaManager`](schemaManager.md).

___

## Checking if a property is in the current schema

> This is useful for [komada-pieces](https://github.com/dirigeants/komada-pieces/)'s pieces that rely on [SettingGateway](../settingGateway.md).

I want to check if a key (for example, `modLog`) exists in the schema, and if it doesn't, create it.

**Solution**:

```js
if (!client.schemaManager.schema.modLog) {
    await client.schemaManager.add("modLog", { type: "Channel" }, true);
}
```
