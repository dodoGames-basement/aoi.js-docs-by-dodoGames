# disabling logs

tired of console being spammed with bunch of commands that was loaded from the command handler?, you can disable that with the option `disableLogs`&#x20;

example

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require('aoi.js')

const bot = new aoijs.AoiClient({
   token: "DISCORD BOT TOKEN"
   prefix: "DISCORD BOT PREFIX"
   intents: ["Guilds", "GuildMessages", "MessageContent"],
   disableLogs: true
 })
```
{% endcode %}

you can revert that by setting `disableLogs` option to `false` again
