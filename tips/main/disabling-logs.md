# disabling logs

want your own ready message instead of getting your bot name logged with an invite to official aoi.js support server? well, you can use `disableLogs` Option.

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
