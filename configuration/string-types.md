&lt;a name="StringConfig"&gt;&lt;/a&gt;



\#\# StringConfig

The starting point for creating a String configuration key.



\*\*Kind\*\*: global class



\* \[StringConfig\]\(\#StringConfig\)

    \* \[new StringConfig\(conf, data\)\]\(\#new\_StringConfig\_new\)

    \* \[.set\(value\)\]\(\#StringConfig+set\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;

    \* \[.add\(value\)\]\(\#StringConfig+add\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;

    \* \[.del\(value\)\]\(\#StringConfig+del\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;



&lt;a name="new\_StringConfig\_new"&gt;&lt;/a&gt;



\#\#\# new StringConfig\(conf, data\)



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| conf \| &lt;code&gt;Config&lt;/code&gt; \| The guild configuration obtained from the guildConfs map. \|

\| data \| &lt;code&gt;Object&lt;/code&gt; \| The data you want to append to this String configuration key. \|



&lt;a name="StringConfig+set"&gt;&lt;/a&gt;



\#\#\# stringConfig.set\(value\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;

Sets the value of a string configurations possibles. This takes into account the list of acceptable answers from the possibles array.



\*\*Kind\*\*: instance method of &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| value \| &lt;code&gt;String&lt;/code&gt; \| The value you want to set this key to. \|



&lt;a name="StringConfig+add"&gt;&lt;/a&gt;



\#\#\# stringConfig.add\(value\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;

Adds a value\(s\) to list of acceptable answers for this key. Accepts one item or an array of items.



\*\*Kind\*\*: instance method of &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| value \| &lt;code&gt;String&lt;/code&gt; &\#124; &lt;code&gt;Array&lt;/code&gt; \| The value\(s\) you want to add to this key. \|



&lt;a name="StringConfig+del"&gt;&lt;/a&gt;



\#\#\# stringConfig.del\(value\) ⇒ &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;

Deletes a value\(s\) from the string configurations possibles. Accepts one item or an array of items.



\*\*Kind\*\*: instance method of &lt;code&gt;\[StringConfig\]\(\#StringConfig\)&lt;/code&gt;



\| Param \| Type \| Description \|

\| --- \| --- \| --- \|

\| value \| &lt;code&gt;String&lt;/code&gt; &\#124; &lt;code&gt;Array&lt;/code&gt; \| The value\(s\) you want to delete from this key. \|

