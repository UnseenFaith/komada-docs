# Using internal Discord.js Methods

Methods are just Discord.js native functions added to Komada, so that we may
export them to any other piece that we may need them in. For example, if your bot
a larger bot and you need to make use of the shardingManager, but can't do since
it's a native Discord.js function, well now you can.

Current Methods are:
- Collections => `client.methods.Collection`
- Rich Embed Builder => `client.methods.Embed`
- Message Collector => `client.methods.MessageCollector`
- WebhookClient => `client.methods.Webhook`

To use any of the methods, you follow this same structure:
```js
let method = new client.methods.<MethodName>(OptionalMethodProperties);
```

So if you need to create a Message Collector, you will do:
```js
let messageCollector = new client.methods.MessageCollector(channelid, filter, options);
```