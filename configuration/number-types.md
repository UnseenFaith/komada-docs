<a name="NumberConfig"></a>

## NumberConfig
The starting point for creating a Number configuration key.

**Kind**: global class

* [NumberConfig](#NumberConfig)
    * [new NumberConfig(conf, data)](#new_NumberConfig_new)
    * [.set(value)](#NumberConfig+set) ⇒ <code>[NumberConfig](#NumberConfig)</code>
    * [.setMin(value)](#NumberConfig+setMin) ⇒ <code>[NumberConfig](#NumberConfig)</code>
    * [.setMax(value)](#NumberConfig+setMax) ⇒ <code>[NumberConfig](#NumberConfig)</code>

<a name="new_NumberConfig_new"></a>

### new NumberConfig(conf, data)

| Param | Type | Description |
| --- | --- | --- |
| conf | <code>Config</code> | A guilds configuration obtained from the guildConfs map. |
| data | <code>Object</code> | The data you want to append to this number key. |

<a name="NumberConfig+set"></a>

### numberConfig.set(value) ⇒ <code>[NumberConfig](#NumberConfig)</code>
Sets the value for a number key, according to the minimum and maximum values if they apply.

**Kind**: instance method of <code>[NumberConfig](#NumberConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>Number</code> | The value you want to set the key as. |

<a name="NumberConfig+setMin"></a>

### numberConfig.setMin(value) ⇒ <code>[NumberConfig](#NumberConfig)</code>
Sets the minimum value a number key can be.

**Kind**: instance method of <code>[NumberConfig](#NumberConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>Number</code> | The value you want to set the minimum as. |

<a name="NumberConfig+setMax"></a>

### numberConfig.setMax(value) ⇒ <code>[NumberConfig](#NumberConfig)</code>
Sets the maximum value a number key can bey.

**Kind**: instance method of <code>[NumberConfig](#NumberConfig)</code>

| Param | Type | Description |
| --- | --- | --- |
| value | <code>Number</code> | The value you want to set the maximum as. |