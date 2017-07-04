<a name="Config"></a>

## Config
The starting point for creating a Guild configuration

**Kind**: global class

* [Config](#Config)
    * [new Config(client, guildID, [config])](#new_Config_new)
    * _instance_
        * [.addKey(key, defaultValue, type)](#Config+addKey) ⇒ [Config](#Config)
        * [.delKey(key)](#Config+delKey) ⇒ <code>null</code>
        * [.reset(key)](#Config+reset) ⇒ <code>Config.&ltKey&gt</code>
        * [.has(key)](#Config+has) ⇒ <code>Boolean</code>
    * _static_
        * [.get(guild)](#Config.get) ⇒ <code>Object</code>
        * [.set(key, defaultValue)](#Config.set) ⇒ <code>Object</code>
        * [.setMin(key, defaultMinValue)](#Config.setMin) ⇒ <code>Object</code>
        * [.setMax(key, defaultMaxValue)](#Config.setMax) ⇒ <code>Object</code>
        * [.add(key, defaultValue)](#Config.add) ⇒ <code>Object</code>
        * [.del(key, defaultValue)](#Config.del) ⇒ <code>Object</code>
        * [.toggle(key)](#Config.toggle) ⇒ <code>Object</code>
        * [.has(guild)](#Config.has) ⇒ <code>Boolean</code>
        * [.hasKey(key)](#Config.hasKey) ⇒ <code>Boolean</code>
        * [.addKey(key, defaultValue, [type])](#Config.addKey) ⇒ <code>Object</code>
        * [.delKey(key)](#Config.delKey) ⇒ <code>Object</code>
        * [.insert(client, guild)](#Config.insert) ⇒ <code>String</code>
        * [.remove(guild)](#Config.remove) ⇒ <code>String</code>
        * [.initialize(client)](#Config.initialize) ⇒ <code>null</code>

<a name="new_Config_new"></a>

### new Config(client, guildID, [config])

| Param | Type | Description |
| --- | --- | --- |
| client | <code>Client</code> | The Discord.js client. |
| guildID | <code>GuildID</code> | The guild for which the configuration is being made. |
| [config] | <code>Object</code> | The local config to add to the configuration. |

<a name="Config+addKey"></a>

### config.addKey(key, defaultValue, type) ⇒ <code>[Config](#Config)</code>
Allows you to add a key to a guild configuration. Note: This should never be called directly as it could cause unwanted side effects.

**Kind**: instance method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key to add to the configuration. |
| defaultValue | <code>String</code> &#124; <code>Array</code> &#124; <code>Number</code> &#124; <code>Boolean</code> | The value for the key. |
| type | <code>String</code> | The type of key you want to add. |

<a name="Config+delKey"></a>

### config.delKey(key) ⇒ <code>null</code>
Deletes a key from the respected guild configuration. This should never be called directly.

**Kind**: instance method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key to delete from the configuration |

<a name="Config+reset"></a>

### config.reset(key) ⇒ <code>Config.&ltKey&gt</code>
Resets a key for the respected guild configuration.

**Kind**: instance method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key to reset in the configuration. |

<a name="Config+has"></a>

### config.has(key) ⇒ <code>Boolean</code>
Checks the guild configuration for a key

**Kind**: instance method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key to check the guild configuration for. |

<a name="Config.get"></a>

### Config.get(guild) ⇒ <code>Object</code>
Simplifies the guild configuration for use in commands and modules.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| guild | <code>Guild</code> | The guild to get a configuration for. |

**Example**
```js
{ prefix: '--', disabledCommands: [], modRole: 'Mods', adminRole: 'Devs', lang: 'en' }
```
<a name="Config.set"></a>

### Config.set(key, defaultValue) ⇒ <code>Object</code>
Set the default value for a key in the default configuration.

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key for which you want to change. |
| defaultValue | <code>Array</code> &#124; <code>Boolean</code> &#124; <code>Number</code> &#124; <code>String</code> | The value you want to set as the default. |

<a name="Config.setMin"></a>

### Config.setMin(key, defaultMinValue) ⇒ <code>Object</code>
Sets the default minimum value for a Number key

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The Number key for which you want to set the minimum value for. |
| defaultMinValue | <code>Number</code> | The value you want to set as the "minimum" value. |

<a name="Config.setMax"></a>

### Config.setMax(key, defaultMaxValue) ⇒ <code>Object</code>
Sets the default maximum value for a Number key

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The Number key for which you want to set the maximum value for. |
| defaultMaxValue | <code>Number</code> | The value you want to set as the "maximum" value. |

<a name="Config.add"></a>

### Config.add(key, defaultValue) ⇒ <code>Object</code>
Adds a value to the data array for an Array key.

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The Array key for which you want to add value(s) for. |
| defaultValue | <code>String</code> | The value for which you want to add to the array. |

<a name="Config.del"></a>

### Config.del(key, defaultValue) ⇒ <code>Object</code>
Deletes a value from the data array for an Array key.

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The array key for which you want to delete value(s) from. |
| defaultValue | <code>String</code> | The value for which you want to remove from the array. |

<a name="Config.toggle"></a>

### Config.toggle(key) ⇒ <code>Object</code>
Toggles the true/false statement for a Boolean key

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration for the key.

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The boolean key for which you want to toggle the statement for. |

<a name="Config.has"></a>

### Config.has(guild) ⇒ <code>Boolean</code>
Checks if the guildConfs Map has the specified guild.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| guild | <code>Guild</code> | The guild to check the Map for. |

<a name="Config.hasKey"></a>

### Config.hasKey(key) ⇒ <code>Boolean</code>
Checks if the default configuration has a specified key.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key for which to check the default configuration for. |

<a name="Config.addKey"></a>

### Config.addKey(key, defaultValue, [type]) ⇒ <code>Object</code>
Adds a key to the default configuration, and every guilds configuration.

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the entire default configuration

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key for which to add to the default and all guild configurations. |
| defaultValue | <code>String</code> &#124; <code>Number</code> &#124; <code>Boolean</code> &#124; <code>Array</code> | The value for which you want to set as the default value. |
| [type] | <code>String</code> | The type of key this will be. This can currently be Strings, Numbers, Arrays, or Booleans. |

<a name="Config.delKey"></a>

### Config.delKey(key) ⇒ <code>Object</code>
Deletes a key from the default configuration, and every guilds configuration.

**Kind**: static method of [Config](#Config)
**Returns**: <code>Object</code> - Returns the new default configuration

| Param | Type | Description |
| --- | --- | --- |
| key | <code>String</code> | The key for which to add to the default and all guild configurations. |

<a name="Config.insert"></a>

### Config.insert(client, guild) ⇒ <code>String</code>
Inserts a guild into the guildConfs map and deletes the configuration JSON. This should never be called by anyone, this is purely for the guildCreate event.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| client | <code>Client</code> | The Discord.js Client |
| guild | <code>Guild</code> | The Guild being inserted into the map. |

<a name="Config.remove"></a>

### Config.remove(guild) ⇒ <code>String</code>
Removes a guild from the guildConfs map and deletes the configuration JSON. This should never be called by anyone, this is purely for the guildDelete event.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| guild | <code>Guild</code> | The guild being removed from the map. |

<a name="Config.initialize"></a>

### Config.initialize(client) ⇒ <code>null</code>
The motherboard of our Configuration system. There's no reason to ever call this as it's called internally upon startup.

**Kind**: static method of [Config](#Config)

| Param | Type | Description |
| --- | --- | --- |
| client | <code>Client</code> | The Discord.js Client |