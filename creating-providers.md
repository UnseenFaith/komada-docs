# Creating Data Providers

Data Providers are special functions designed to make your life easier when you're
using a **database**, there's **no** rule to make them. By default, Komada uses
JSON to store per-guild configuration.

When you create a data provider, you can access to them by: `client.providers.get(ProviderName)`.

There's a little trick we do with exports if you want to publish your data provider
in [Komada Pieces](https://github.com/dirigeants/komada-pieces).

```js
let db;

const config = {
  moduleName: "rethink",
  enabled: true,
  db: "Komada",
};

exports.all = table => db.table(table).run();

exports.get = (table, id) => db.table(table).get(id).run();

exports.help = {};
exports.help.name = "rethinkdb";
exports.help.type = "providers";
exports.help.description = "Allows you use rethinkDB functionality throughout Komada.";
exports.conf = config;
exports.conf.requiredModules = ["rethinkdbdash"];

exports.init = () => {
  db = require("rethinkdbdash")(config.db);
};
```

You define a variable by `let db;`, and then, when Komada loads the piece, it'll run
the function from `exports.init`, assigning the module (and the configuration if exists,
or any function) to said variable. Then, we can work with it anywhere.

The example above is the provider for [RethinkDB](https://www.rethinkdb.com),
you can check the source [here](https://github.com/dirigeants/komada-pieces/blob/master/providers/rethinkdb.js).

## Accessing Providers

Functions are stored in the main `client` object, in the `providers` property. This has an entry
for each function added, based on its `exports.help.name`. So for example if you have it set as
`sqlite` , you can access it through `client.providers.get("sqlite");`. If you use `exports.thing = "blah"`;
then you would access that rather from `client.providers.get("sqlite").thing;`.

For more details on modules, read [this article](https://www.hacksparrow.com/node-js-exports-vs-module-exports.html).
