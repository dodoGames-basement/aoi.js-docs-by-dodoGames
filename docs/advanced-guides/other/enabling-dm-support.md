# enabling DM Support

by default aoi.js does not allow you to run commands in the bot DMS however fortunately you can change this

## getting started

to get started, please add the following intent to your client options on **intents** property

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: "DISCORD BOT PREFIX",
intents: ["GUILDS", "GUILD_MESSAGES", "DIRECT_MESSAGES"]
})
```
{% endcode %}

## setting up

after adding `DIRECT_MESSAGES` you need to modify `bot.onMessage()` event to include the following

```javascript
bot.onMessage({
guildOnly: false
})
```

## configuring DM support on the existing commands

you can configurate dm support on the current commands you made with the property option: `executeAt` &#x20;

## options

* **guild**: only let the command execute per servers
* **dm**: only let the command execute in the DMS
* **both**: let the command execute in both guild and the DMS as well

example

{% code title="commands/dm.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
executeAt: "dm",
name: "dm",
code: `this command works only in dms`
}
```
{% endcode %}
