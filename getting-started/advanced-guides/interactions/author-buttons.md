# Author Buttons

author buttons let's only the user who executed the command himself interact with the bot buttons, this is useful to avoid disturbance from other users, it also prevents people from tampering up with your bot stuff without you being aware of

let's start of with an example command that has `$authorID` to the button id thingy

{% code title="commands/author.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "author",
code: `$title[author button test!]
$description[hi click the button shown below!]
$addButton[1;Here;primary;hello_$authorID;no]`
}
```
{% endcode %}

at the custom id part of the `$addButton` function we then add `$authorID` to the custom id name of the button in order to make the author buttons

## making the author interaction

now we have a command that has a button with `$authorID` being used, let's make it respond to the only one who executed the cmd

{% code title="commands/author.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = [{
name: "author",
code: `$title[author button test!]
$description[hi click the button shown below!]
$addButton[1;Here;primary;hello_$authorID;no]`
},
{
type: "interaction",
prototype: "button",
code: `$interactionReply[you're the author who clicked this!;;;;all;no]

$onlyif[$get[authorID]==$interactionData[author.id];{
"content" : "You aren't the author of this interaction.",
"ephemeral" : true,
"options" : { "interaction" : true }
}]

$onlyif[$get[customId]==hello;]

$let[authorID;$splitText[2]]
$let[customId;$splitText[1]] 
$textSplit[$interactionData[customId];_] 

`
}]
```
{% endcode %}

{% hint style="info" %}
unlike normal interactions, author interactions should not have **name** property being used in the command code as it will not work either
{% endhint %}

## Note

it is basically the same thing with select menu option value replies, you only need extra `$onlyif` code which is likely `$onlyIf[$interactionData[values[0]]==menu option value]`

## Conclusion

now you have a author button that only works for the user who executed your bot commands!, anyone who tried to click on the button will likely get a error that they're not the author who has executed the cmd
