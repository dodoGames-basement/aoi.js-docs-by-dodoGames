# Logging Errors

logging errors might be pretty useful to help developers finding out the bugs of their created commands and fix it for their bot users to enjoy the bot without issue

in this case, we will be using function error event to log errors when an mistake occurs upon running an command

## getting started

to start off, first of all add the following option to your client options

<pre class="language-javascript" data-overflow="wrap" data-line-numbers><code class="lang-javascript">const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: "DISCORD BOT PREFIX",
intents: ["GUILDS", "GUILD_MESSAGES"],
<strong>events: {functionError: true}
</strong>})</code></pre>

`events: {functionError: true}` will then enable the ability to log errors of an bug occurring upon running an command!

now let's make an command that is dedicated to function error to log errors especially to an specific channel by using it's own id after copying it

{% code title="commands/error-log.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
type: 'functionError',
channel: "CHANNEL ID",
code: `$title[Error In $serverName]
$description[Function: $handleError[function]
Command: $handleError[command]
Error: $handleError[error]]
$color[RED]`
}
```
{% endcode %}

after filling up the channel id you want to on the **channel** property, you will notice that everytime an error occurs when using the certain commands, then it will send the error with the server name (as shown in the example) with the command name and the code error itself to the channel you specified off using it's id

## Conclusion

now you have an error logging system that is perfectly working with no issues, you can customize anything to your liking including changing the way on how should the errors be shown
