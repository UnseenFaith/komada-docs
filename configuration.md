&lt;a name="Config"&gt;&lt;/a&gt;



\#\# Config

The starting point for creating a Guild configuration



\*\*Kind\*\*: global class



\* \[Config\]\(\#Config\)

    \* \[new Config\(client, guildID, \[config\]\)\]\(\#new\_Config\_new\)

    \* \_instance\_

        \* \[.addKey\(key, defaultValue, type\)\]\(\#Config+addKey\) ⇒ &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

        \* \[.delKey\(key\)\]\(\#Config+delKey\) ⇒ &lt;code&gt;null&lt;/code&gt;

        \* \[.reset\(key\)\]\(\#Config+reset\) ⇒ &lt;code&gt;Config.&lt;Key&gt;&lt;/code&gt;

        \* \[.has\(key\)\]\(\#Config+has\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

    \* \_static\_

        \* \[.get\(guild\)\]\(\#Config.get\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.set\(key, defaultValue\)\]\(\#Config.set\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.setMin\(key, defaultMinValue\)\]\(\#Config.setMin\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.setMax\(key, defaultMaxValue\)\]\(\#Config.setMax\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.add\(key, defaultValue\)\]\(\#Config.add\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.del\(key, defaultValue\)\]\(\#Config.del\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.toggle\(key\)\]\(\#Config.toggle\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.has\(guild\)\]\(\#Config.has\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

        \* \[.hasKey\(key\)\]\(\#Config.hasKey\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

        \* \[.addKey\(key, defaultValue, \[type\]\)\]\(\#Config.addKey\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.delKey\(key\)\]\(\#Config.delKey\) ⇒ &lt;code&gt;Object&lt;/code&gt;

        \* \[.insert\(client, guild\)\]\(\#Config.insert\) ⇒ &lt;code&gt;String&lt;/code&gt;

        \* \[.remove\(guild\)\]\(\#Config.remove\) ⇒ &lt;code&gt;String&lt;/code&gt;

        \* \[.initialize\(client\)\]\(\#Config.initialize\) ⇒ &lt;code&gt;null&lt;/code&gt;



&lt;a name="new\_Config\_new"&gt;&lt;/a&gt;



\#\#\# new Config\(client, guildID, \[config\]\)



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| client \| &lt;code&gt;Client&lt;/code&gt; \| The Discord.js client. \|

\| guildID \| &lt;code&gt;GuildID&lt;/code&gt; \| The guild for which the configuration is being made. \|

\| \[config\] \| &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt; \| The local config to add to the configuration. \|



&lt;a name="Config+addKey"&gt;&lt;/a&gt;



\#\#\# config.addKey\(key, defaultValue, type\) ⇒ &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

Allows you to add a key to a guild configuration. Note: This should never be called directly as it could cause unwanted side effects.



\*\*Kind\*\*: instance method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key to add to the configuration. \|

\| defaultValue \| &lt;code&gt;String&lt;/code&gt; &\#124; &lt;code&gt;Array&lt;/code&gt; &\#124; &lt;code&gt;Number&lt;/code&gt; &\#124; &lt;code&gt;Boolean&lt;/code&gt; \| The value for the key. \|

\| type \| &lt;code&gt;String&lt;/code&gt; \| The type of key you want to add. \|



&lt;a name="Config+delKey"&gt;&lt;/a&gt;



\#\#\# config.delKey\(key\) ⇒ &lt;code&gt;null&lt;/code&gt;

Deletes a key from the respected guild configuration. This should never be called directly.



\*\*Kind\*\*: instance method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key to delete from the configuration \|



&lt;a name="Config+reset"&gt;&lt;/a&gt;



\#\#\# config.reset\(key\) ⇒ &lt;code&gt;Config.&lt;Key&gt;&lt;/code&gt;

Resets a key for the respected guild configuration.



\*\*Kind\*\*: instance method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key to reset in the configuration. \|



&lt;a name="Config+has"&gt;&lt;/a&gt;



\#\#\# config.has\(key\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

Checks the guild configuration for a key



\*\*Kind\*\*: instance method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key to check the guild configuration for. \|



&lt;a name="Config.get"&gt;&lt;/a&gt;



\#\#\# Config.get\(guild\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Simplifies the guild configuration for use in commands and modules.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| guild \| &lt;code&gt;Guild&lt;/code&gt; \| The guild to get a configuration for. \|



\*\*Example\*\*

\`\`\`js

{ prefix: '--', disabledCommands: \[\], modRole: 'Mods', adminRole: 'Devs', lang: 'en' }

\`\`\`

&lt;a name="Config.set"&gt;&lt;/a&gt;



\#\#\# Config.set\(key, defaultValue\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Set the default value for a key in the default configuration.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key for which you want to change. \|

\| defaultValue \| &lt;code&gt;Array&lt;/code&gt; &\#124; &lt;code&gt;Boolean&lt;/code&gt; &\#124; &lt;code&gt;Number&lt;/code&gt; &\#124; &lt;code&gt;String&lt;/code&gt; \| The value you want to set as the default. \|



&lt;a name="Config.setMin"&gt;&lt;/a&gt;



\#\#\# Config.setMin\(key, defaultMinValue\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Sets the default minimum value for a Number key



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The Number key for which you want to set the minimum value for. \|

\| defaultMinValue \| &lt;code&gt;Number&lt;/code&gt; \| The value you want to set as the "minimum" value. \|



&lt;a name="Config.setMax"&gt;&lt;/a&gt;



\#\#\# Config.setMax\(key, defaultMaxValue\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Sets the default maximum value for a Number key



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The Number key for which you want to set the maximum value for. \|

\| defaultMaxValue \| &lt;code&gt;Number&lt;/code&gt; \| The value you want to set as the "maximum" value. \|



&lt;a name="Config.add"&gt;&lt;/a&gt;



\#\#\# Config.add\(key, defaultValue\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Adds a value to the data array for an Array key.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The Array key for which you want to add value\(s\) for. \|

\| defaultValue \| &lt;code&gt;String&lt;/code&gt; \| The value for which you want to add to the array. \|



&lt;a name="Config.del"&gt;&lt;/a&gt;



\#\#\# Config.del\(key, defaultValue\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Deletes a value from the data array for an Array key.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The array key for which you want to delete value\(s\) from. \|

\| defaultValue \| &lt;code&gt;String&lt;/code&gt; \| The value for which you want to remove from the array. \|



&lt;a name="Config.toggle"&gt;&lt;/a&gt;



\#\#\# Config.toggle\(key\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Toggles the true/false statement for a Boolean key



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration for the key.



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The boolean key for which you want to toggle the statement for. \|



&lt;a name="Config.has"&gt;&lt;/a&gt;



\#\#\# Config.has\(guild\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

Checks if the guildConfs Map has the specified guild.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| guild \| &lt;code&gt;Guild&lt;/code&gt; \| The guild to check the Map for. \|



&lt;a name="Config.hasKey"&gt;&lt;/a&gt;



\#\#\# Config.hasKey\(key\) ⇒ &lt;code&gt;Boolean&lt;/code&gt;

Checks if the default configuration has a specified key.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key for which to check the default configuration for. \|



&lt;a name="Config.addKey"&gt;&lt;/a&gt;



\#\#\# Config.addKey\(key, defaultValue, \[type\]\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Adds a key to the default configuration, and every guilds configuration.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the entire default configuration



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key for which to add to the default and all guild configurations. \|

\| defaultValue \| &lt;code&gt;String&lt;/code&gt; &\#124; &lt;code&gt;Number&lt;/code&gt; &\#124; &lt;code&gt;Boolean&lt;/code&gt; &\#124; &lt;code&gt;Array&lt;/code&gt; \| The value for which you want to set as the default value. \|

\| \[type\] \| &lt;code&gt;String&lt;/code&gt; \| The type of key this will be. This can currently be Strings, Numbers, Arrays, or Booleans. \|



&lt;a name="Config.delKey"&gt;&lt;/a&gt;



\#\#\# Config.delKey\(key\) ⇒ &lt;code&gt;Object&lt;/code&gt;

Deletes a key from the default configuration, and every guilds configuration.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;

\*\*Returns\*\*: &lt;code&gt;Object&lt;/code&gt; - Returns the new default configuration



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| key \| &lt;code&gt;String&lt;/code&gt; \| The key for which to add to the default and all guild configurations. \|



&lt;a name="Config.insert"&gt;&lt;/a&gt;



\#\#\# Config.insert\(client, guild\) ⇒ &lt;code&gt;String&lt;/code&gt;

Inserts a guild into the guildConfs map and deletes the configuration JSON. This should never be called by anyone, this is purely for the guildCreate event.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| client \| &lt;code&gt;Client&lt;/code&gt; \| The Discord.js Client \|

\| guild \| &lt;code&gt;Guild&lt;/code&gt; \| The Guild being inserted into the map. \|



&lt;a name="Config.remove"&gt;&lt;/a&gt;



\#\#\# Config.remove\(guild\) ⇒ &lt;code&gt;String&lt;/code&gt;

Removes a guild from the guildConfs map and deletes the configuration JSON. This should never be called by anyone, this is purely for the guildDelete event.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| guild \| &lt;code&gt;Guild&lt;/code&gt; \| The guild being removed from the map. \|



&lt;a name="Config.initialize"&gt;&lt;/a&gt;



\#\#\# Config.initialize\(client\) ⇒ &lt;code&gt;null&lt;/code&gt;

The motherboard of our Configuration system. There's no reason to ever call this as it's called internally upon startup.



\*\*Kind\*\*: static method of &lt;code&gt;\[Config\]\(\#Config\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| client \| &lt;code&gt;Client&lt;/code&gt; \| The Discord.js Client \|

