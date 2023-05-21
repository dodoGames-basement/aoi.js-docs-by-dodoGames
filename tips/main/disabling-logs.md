# disabling logs

Want your own ready message instead of getting your bot name logged with an invite to official aoi.js support server? well, you can use `aoiLogs` Option.

Example:

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const { AoiClient } = require('aoi.js')

const bot = new AoiClient({
   token: "DISCORD BOT TOKEN"
   prefix: "DISCORD BOT PREFIX"
   intents: ["Guilds", "GuildMessages", "MessageContent"],
   events: ["onMessage", "onInteractionCreate"],
   aoiLogs: false,
   database: { 
     type: "aoi.db",
     db: require("aoi.db"),
     tables: ["main"],
     path: "./database/",
     extraOptions: {
         dbType: "KeyValue" 
     },
 }
 })
```
{% endcode %}

You can revert that by setting `aoiLogs` option to `true` again.

{% hint style="success" %}
You can also use `aoiWarning` option to disable the update message of aoi.js when an new version releases (setting it to `true` will disable the update message, otherwise `false` would do the opposite.
{% endhint %}
