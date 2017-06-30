# SchemaManager

## Methods

You access to settingGateway's methods by `client.schemaManager`, throught your eval command.

### [METHOD] add( _**key**: String, **options**: Object, **force**: Boolean_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
|  key  | `String`  | The name of the key to add. |
| options | `Object` | The object with the options. |
| force | `Boolean` | Whether force the update or not (Recommended). |
|       | `default=false` | The guild params default to null. |

Add a new key to the schema.

#### Options

| Param | Type | Description |
| :---: | ---- | ----------- |
| type | `String`  | The type of the key. |
| default | `Object` | The default value for the key. |
| array | `Boolean` | Whether the keys should be stored in an array or not. |
| min | `Integer` | Minimum value for `type=Integer`, or minimum string length for `type=String`. |
| max | `Integer` | Maximum value for `type=Integer`, or maximum string length for `type=String`. |
| sql | `String` | SQL query for the new row. |

> Returns: `Promise<Void>`

___

### [METHOD] remove( _**key**: String, **force**: Boolean_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
|  key  | `String`  | The name of the key to remove. |
| force | `Boolean` | Whether force the update or not (Recommended). |
|       | `default=false` | The guild params default to null. |

Remove a key from the schema.

> Returns: `Promise<Void>`

___

### [METHOD] force( _**action**: "add"|"delete", **key**: String_ )

| Param | Type | Description |
| :---: | ---- | ----------- |
| action | `"add"`\|`"delete"`  | Whether to add or remove a key. |
|  key  | `String`  | The name of the key to edit. |

This method can dangerous if it's used incorrectly. It's used from both `add` and `remove` methods if you set the option `force` to true. This method updates all documents (or rows, if SQL) automatically after a Schema update.

> Returns: `Promise<Void>`

___

### [GET] settingGateway

A shortcut of `this.client.settingGateway`.

> Returns: `SettingGateway`

___

### [GET] defaultDataSchema

Get the default DataSchema from Komada.

> Returns: `Object`