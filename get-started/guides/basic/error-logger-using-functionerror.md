# Error logger using functionError

sometimes in aoi.js, you want to make your bot log errors so you or your bot team can then investigate on why it's occurring, this guide, you will learn on how to make error logger system using `onFunctionError` event by aoi.js.

for getting started head over to the [#getting-started](error-logger-using-functionerror.md#getting-started "mention").

## getting started

to start off, you need to add the following into your `events:` events

{% code overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
    token: "Discord Token",
    prefix: "Discord Prefix",
    intents: ["MessageContent", "GuildMessages", "Guilds"],
    events: ["onMessage", "onInteractionCreate", "onFunctionError"]
})
```
{% endcode %}

`onFunctionError` will then enable the ability to log errors of an bug occurring upon running an command!

now we will make an example error logger command that sends an error each time an problem occurs in one of the commands for an specific channel with **channel** property

{% code title="commands/error-log.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
type: 'functionError',
channel: "CHANNEL ID",
code: `$title[Error In $serverName]
$description[Function: $handleError[function]
Command: $handleError[command]
Error: $handleError[error]]
$color[Red]`
}
```
{% endcode %}

after filling up the channel id you want to on the **channel** property, you will notice that everytime an error occurs when using the certain commands, then it will send the error with the server name (as shown in the example) with the command name and the code error itself to the channel you specified off using it's id

## Conclusion

now you have an error logging system that is perfectly working with no issues, you can customize anything to your liking including changing the way on how should the errors be shown
