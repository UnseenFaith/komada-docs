# SQL

This class is core. If you have loaded [SettingGateway](../settingGateway.md) with a [NoSQL](https://en.wikipedia.org/wiki/NoSQL) provider, this class will
not be available throught it. And be careful on what you do here, the following methods are handled internally throught [SchemaManager](./schemaManager.md) and you don't need to use them.

## Methods

The following methods are only available throught `client.settingGateway.sql` **only** if the provider has the property `conf.sql` set to `true`. Otherwise it'll be `null` and all methods will remain unaccessible.

They're **NOT** suitable for NoSQL providers. If you try that, only thing you'll get is extra-processing, and a lot of errors. *You're warned*.

### [METHOD] buildSingleSQLSchema( _**value**: Object_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| value | `Schema<Value>` | A value from the schema. |
|       | `value.type` | The property `type` of `value`. |
|       | `value.default` | The property `default` of `value`. |
|       | `value.array` | The property `array` of `value`. |
|       | `value.sql` | The property `sql` of `value`. |

Generate a SQL query based on input. It'll use an exports `CONSTANTS` from the provider. Otherwise it'll log an error and use the default one (at the bottom of this page).

> Returns: `Promise<Void>`

___

### [METHOD] buildSQLSchema( _**schema**: Object_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| schema | `Schema` | The current schema. |

### [METHOD] initDeserialize()

Init the deserialization keys for SQL providers.

> Returns: `Void`

___

### [METHOD] deserializer( _**data**: Object_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| data | `Object` | The GuildSettings object. |

Deserialize stringified objects.

> Returns: `Void`

___

### [METHOD] updateColumns( _**schema**: Object, **defaults**: Object, **key**: String_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| schema | `Schema` | The current schema. |
| defaults | `Object` | The current schema's default keys. |
| key | `String_` | The key which is updated. |

Create/Remove columns from a SQL database, by the providen Schema.

> Returns: `Promise<Boolean>`

___

### [GET] schema

A shortcut of `this.client.schemaManager.schema`.

> Returns: `Schema`

___

### [GET] defaults

A shortcut of `this.client.schemaManager.defaults`.

> Returns: `Object`

___


## Helpers

If the provider lacks of an `exports.CONSTANTS`, Komada will take the following table:

|        Type | SQL DataType                                    |
| :---------: | ----------------------------------------------- |
|    `String` | `"TEXT"`                                        |
|   `Integer` | `"INTEGER"`                                     |
|     `Float` | `"INTEGER"`                                     |
|    `AutoID` | `"INTEGER PRIMARY KEY AUTOINCREMENT UNIQUE"`    |
| `Timestamp` | `"DATETIME"`                                    |
|    `AutoTS` | `"DATETIME DEFAULT CURRENT_TIMESTAMP NOT NULL"` |

> **PLEASE NOTE** This table is the one SQLite uses, which gives basic datatypes.