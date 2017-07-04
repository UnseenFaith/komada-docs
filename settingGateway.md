# Introduction

Previously, Komada used JSON to store per-guild configurations, in a very complex system that is hard to update and understand, plus it had its limits. Users repeatedly "bridged" the built-in configuration because they don't fit their needings (they want to use another database, such as SQLite, MySQL, MongoDB, RethinkDB...).

The old configuration system had also several flags, such as the Array type, it could store whatever you want, and for the built-in `modRole` and `adminRole` keys, they stored (literally), the role name.

# SettingGateway (added in 0.20.3)

SettingGateway is a configuration system that first saw the light in [#255](https://github.com/dirigeants/komada/pull/255), and got [SQL](https://en.wikipedia.org/wiki/SQL) Compatibility in [#289](https://github.com/dirigeants/komada/pull/289). It is the first configuration system that doesn't rely on an internal provider but it uses **pieces**. By default, it comes with a JSON provider optimized for speed that relies on [fs-nextra](https://github.com/bdistin/fs-nextra) and has something new: "table support". It means, while Komada uses the JSON provider, you're able to use it for another things, like a starboard system, without worrying about making another provider.

But that's not the point of it. The point of this new system is that you can easily "swap" the "provider engine" by just changing a name. Want to use the SQLite provider? Just add this to your Komada's configuration (in your `app.js`):

```js
provider: { engine: "sqlite" }
```

> **NOTE** If not specified, `config.provider.engine` defaults to `json`. The name must match the provider name, and it's case sensitive.

## How it works

When you boot up your bot, this system will load a provider and assign it to `this.provider` (performance wise, to avoid getting the provider once and again), and then, execute certain methods depending on what it needs.

So... yeah, **all providers must have exactly the same method names and arguments**, with a little exception on SQL providers' `Provider#createTable` method, as they have to create the columns with the table. In that case, they have a second argument for the data names and types (they're automatically given by the [SQL](settingGateway/sql.md) class).

## Methods

You access to settingGateway's methods by `client.settingGateway`, throught your eval command.

### [GET] schema

A shortcut of `client.settingGateway.schemaManager.schema`.

> Returns: `Schema`

___

### [GET] defaults

A shortcut of `client.settingGateway.schemaManager.defaults`.

> Returns: `Object`

___

### [METHOD] create( _**guild**: GuildResolvable_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |

Creates a new Guild entry in the database and caches it after creation.

> Returns: `Promise<Void>`

___

### [METHOD] destroy( _**guild**: Snowflake_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `Snowflake` | The Guild ID. |

Removes a Guild entry from the database and removes it from the cache.

> Returns: `Promise<Void>`

___

### [METHOD] get( _**guild**: GuildResolvable | "default"_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |
|       | `"default"` | The default configuration. |

Retrieve from the cache the settings for the specified guild, or the default one.

> Returns: `Object`

___

### [METHOD] getResolved( _**guild**: GuildResolvable_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |

Retrieve from the cache the settings for the specified guild and resolve it. For example, you have a `modRole` key which **type** is **Role**, then this method will return a **Role instance** based on the input.

> Returns: `Promise<Object>`

___

### [METHOD] sync( _**guild**: GuildResolvable_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |
|       | `default=null` | The `guild` params default to `null`. |

Sync either all Guild entries from the configuration, or a single one.

> Returns: `Promise<Void>`

___

### [METHOD] reset( _**guild**: GuildResolvable, **key**: String_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |
|  key  | `String` | The key to reset. |

Reset a key's value to default from a Guild's settings.

> Returns: `Promise<Any>`

___

### [METHOD] update( _**guild**: GuildResolvable, **key**: String, **data**: Any_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |
|  key  | `String` | The key to update. |
|  data | `Any` | The new value for the key. |

Update a key's value from a Guild's settings.

> Returns: `Promise<Any>`

___

### [METHOD] updateArray( _**guild**: GuildResolvable, **type**: "add"|"remove", **key**: String, **data**: Any_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| guild | `GuildResolvable`  | The Guild Instance or a Snowflake. |
|  type | `"add"`\|`"remove"`| Either add or remove the value |
|  key  | `String` | The key to update. |
|  data | `Any` | The value to be added or removed. |

> Returns: `Promise<(Boolean|Result)>`
