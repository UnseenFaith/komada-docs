<a name="ArrayConfig"></a>

## ArrayConfig
The starting point for creating an Array Configuration key.

**Kind**: global class

* [ArrayConfig](#ArrayConfig)
    * [new ArrayConfig(conf, data)](#new_ArrayConfig_new)
    * [.add(value)](#ArrayConfig+add) ⇒ <code>[ArrayConfig](#ArrayConfig)</code>
    * [.del(value)](#ArrayConfig+del) ⇒ <code>[ArrayConfig](#ArrayConfig)</code>

<a name="new_ArrayConfig_new"></a>

### new ArrayConfig(conf, data)

| Param | Type | Description |
| --- | --- | --- |
| conf | <code>Config</code> | The guild configuration obtained from the guildConfs map. |
| data | <code>Object</code> | The data you want to append to this Array configuration key. |

<a name="ArrayConfig+add"></a>

### arrayConfig.add(value) ⇒ <code>[ArrayConfig](#ArrayConfig)</code>
Adds a value(s) to the array. Accepts a single value or an array of values.

**Kind**: instance method of <code>[ArrayConfig](#ArrayConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> &#124; <code>Array</code> | The value(s) to add to the array. |

<a name="ArrayConfig+del"></a>

### arrayConfig.del(value) ⇒ <code>[ArrayConfig](#ArrayConfig)</code>
Deletes a value(s) from the array. Accepts a single value or an array of values.

**Kind**: instance method of <code>[ArrayConfig](#ArrayConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>String</code> &#124; <code>Array</code> | The value(s) to delete from the array. |