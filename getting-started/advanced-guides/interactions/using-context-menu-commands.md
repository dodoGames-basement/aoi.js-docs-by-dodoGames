# using context menu commands

context menu commands are basically app commands that are executable through right clicking on whether an message or on an user with hovering to apps option to run the command from discord right click menu

before we get started, we need to understand the differences first before going further

* **message**: commands that only appear when you right click on a certain message, normally these bring the message id if you have clicked their command through apps option from discord right click menu
* **user:** commands that only appear when you right click on a certain user, normally these bring the user id if you have clicked their command through apps option from discord right click menu

{% hint style="info" %}
all context menu commands are only usable with the `slash` prototype otherwise it won't work
{% endhint %}

## setting up an message command

let's create an context menu command for messages

{% code title="commands/message-create.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "create",
code: `$createApplicationCommand[$guildID;hello;.;true;message]`
}
```
{% endcode %}

this will create an context menu command for messages

## setting up an user command

let's create an context menu command for users

{% code title="commands/user-create.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "create",
code: `$createApplicationCommand[$guildID;example;.;true;user]`
}
```
{% endcode %}

this will create an context menu command for users

## getting the id of the (message/user)

you can use `$interactionData[targetId]` which then gets the target id so if it was an context menu message command then it will return the targeted message id, same as context menu user command but opposite where it returns the targeted user id

## responding

you need to use `slash` prototype for all context menu commands to work

{% code title="commands/reply.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "context-command-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[Hi!;;;;all;no]`
}

```
{% endcode %}

just like normally in almost every interaction cmd you can use embeds on context menu commands as well as buttons, select menus, etc
