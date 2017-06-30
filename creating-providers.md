# Creating Data Providers

Data Providers are special functions designed to make your life easier when you're
using a **database**, there's **no** rule to make them. By default, Komada uses
JSON to store per-guild configuration.

When you create a data provider, you can access to them by: `client.providers.get(ProviderName)`.

There's a little trick we do with exports if you want to publish your data provider
in [Komada Pieces](https://github.com/dirigeants/komada-pieces).

```js
const config = {
  moduleName: "rethink",
  enabled: true,
  db: "Komada",
};

const r = require("rethinkdbdash")({ db: config.db });

exports.all = table => r.table(table).run();

exports.get = (table, id) => r.table(table).get(id).run();

exports.help = {
  name: "rethinkdb",
  type: "providers",
  description: "Allows you use rethinkDB functionality throughout Komada.",
};
exports.conf = config;
exports.conf.requiredModules = ["rethinkdbdash"];
```

The example above is the provider for [RethinkDB](https://www.rethinkdb.com),
you can check the source [here](https://github.com/dirigeants/komada-pieces/blob/master/providers/rethinkdb.js).

## Accessing Providers

Functions are stored in the main `client` object, in the `providers` property. This has an entry
for each function added, based on its `exports.help.name`. So for example if you have it set as
`sqlite` , you can access it through `client.providers.get("sqlite");`. If you use `exports.thing = "blah"`;
then you would access that rather from `client.providers.get("sqlite").thing;`.

For more details on modules, read [this article](https://www.hacksparrow.com/node-js-exports-vs-module-exports.html).
