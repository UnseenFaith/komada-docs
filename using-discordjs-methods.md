# Using internal Discord.js Methods

Methods are just Discord.js native functions added to Komada, so that we may
export them to any other piece that we may need them in. For example, if your bot
a larger bot and you need to make use of the shardingManager, but can't do since
it's a native Discord.js function, well now you can.

Current Methods are:
- Collection => `client.methods.Collection`
- RichEmbed => `client.methods.Embed`
- MessageCollector => `client.methods.MessageCollector`
- WebhookClient => `client.methods.Webhook`
- escapeMarkdown => `client.methods.escapeMarkdown`
- splitMessage => `client.methods.splitMessage`

To use any of the methods, you follow this same structure:
```js
const method = new client.methods.<MethodName>(OptionalMethodProperties);
```

So if you need to create a Message Collector, you will do:
```js
const messageCollector = new client.methods.MessageCollector(channelid, filter, options);
```
