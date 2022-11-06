# allowing bot mention as a prefix

sometimes you have to guess on what's the prefix for your bot and you are kinda lazy to go back to the code to check it, luckliy you can also use bot mention as a second prefix than `!` (depends on what your prefix is), all you have to do is to add arrays to `prefix` property of client options for multiple prefixes support

example

{% code overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: ["prefix 1", "prefix 2", "prefix 3" ] // and so on
intents: ["GUILDS", "GUILD_MESSAGES"]
})
```
{% endcode %}

now that we have multiple prefixes, let's make one that triggers commands once the bot itself gets mentioned

{% code overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: ["!", "<@$clientID>"] // and so on
intents: ["GUILDS", "GUILD_MESSAGES"]
})
```
{% endcode %}

by adding `<@$clientID>` thingy as a prefix, it basically will let you use bot mentioning as an prefix, note that this won't work if you entered random stuff before the ping of the bot at the first argument

so it must be `@your bot#tag (command)` for it to work
