# Custom Prefix

sometimes when you want your bot to be special or something like that, one of the common stuff an every multi-purpose bot would have is custom prefix system, in aoi.js this is possible using variables assigned only per Guild

## setting up

to get started, make sure you have an variable called prefix

example

{% code overflow="wrap" lineNumbers="true" %}
```javascript
bot.variables({
preifx: "PREFIX (e.g, !)"
})
```
{% endcode %}

now we have a variable created called `prefix`, we then use `$getServerVar[prefix]` to **prefix** property of client options

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: "$getServerVar[prefix]",
intents: ["GUILDS", "GUILD_MESSAGES"]
})
```
{% endcode %}

## basic prefix cmds (for new users)

now we have a variable being used as a prefix, we can make simple commands that let's the user set prefix and or reset it or view current used custom prefix, example

{% code title="commands/set-prefix.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
  name: "set-prefix",
  code: `$setServerVar[prefix;$message;$guildID]
 successfully changed prefix to \`$message\`, from now on i will only respond to that prefix
  $onlyIf[$getServerVar[prefix]!=$message; this prefix is already in use]
$onlyIf[$charCount[$message]<=5;prefix can't be longer than 5 characters]
$onlyIf[$message!=;you need to provide me a new prefix]
  $onlyPerms[manageserver;only server members with \`MANAGE_SERVER\` Permission can set custom prefix]
  `
}
```
{% endcode %}

{% code title="commands/reset-prefix.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
  name: "reset-prefix",
  code: `$setServerVar[prefix;;$guildID]
  successfully reseted prefix for this server
  $onlyPerms[manageserver;only server members with \`MANAGE_SERVER\` Permission can reset custom prefix]`
}
```
{% endcode %}

{% code title="commands/prefix.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
  name: "prefix",
  code: `my prefix in this server is \`$getServerVar[prefix]\`
  `
}
```
{% endcode %}

## Conclusion

now you have a custom prefix system, you can go modify the codes you added to your bot and changed it to your liking if you want
