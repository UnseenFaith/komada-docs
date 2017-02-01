<a name="StringConfig"></a>

## StringConfig
The starting point for creating a String configuration key.

**Kind**: global class

* [StringConfig](#StringConfig)
    * [new StringConfig(conf, data)](#new_StringConfig_new)
    * [.set(value)](#StringConfig+set) ⇒ <code>[StringConfig](#StringConfig)</code>
    * [.add(value)](#StringConfig+add) ⇒ <code>[StringConfig](#StringConfig)</code>
    * [.del(value)](#StringConfig+del) ⇒ <code>[StringConfig](#StringConfig)</code>

<a name="new_StringConfig_new"></a>

### new StringConfig(conf, data)

| Param | Type | Description |
| --- | --- | --- |
| conf | <code>Config</code> | The guild configuration obtained from the guildConfs map. |
| data | <code>Object</code> | The data you want to append to this String configuration key. |

<a name="StringConfig+set"></a>

### stringConfig.set(value) ⇒ <code>[StringConfig](#StringConfig)</code>
Sets the value of a string configurations possibles. This takes into account the list of acceptable answers from the possibles array.

**Kind**: instance method of <code>[StringConfig](#StringConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> | The value you want to set this key to. |

<a name="StringConfig+add"></a>

### stringConfig.add(value) ⇒ <code>[StringConfig](#StringConfig)</code>
Adds a value(s) to list of acceptable answers for this key. Accepts one item or an array of items.

**Kind**: instance method of <code>[StringConfig](#StringConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> &#124; <code>Array</code> | The value(s) you want to add to this key. |

<a name="StringConfig+del"></a>

### stringConfig.del(value) ⇒ <code>[StringConfig](#StringConfig)</code>
Deletes a value(s) from the string configurations possibles. Accepts one item or an array of items.

**Kind**: instance method of <code>[StringConfig](#StringConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> &#124; <code>Array</code> | The value(s) you want to delete from this key. |