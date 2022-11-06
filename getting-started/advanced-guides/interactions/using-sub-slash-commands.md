# using sub slash commands

sub commands are a feature of slash commands that allows you to add extra commands to an existing slash command with it's own each different purpose up to 20 sub commands, this can be useful to avoid the limit of creating slash commands and it let's you organize your bot's slash commands with no issues

## getting started

{% hint style="danger" %}
you need to have your bot being having permissions in order to use and create slash commands if your bot does not have one then invite it with `applications.commands` scope from dev portal
{% endhint %}

let's take a look at how to create an example sub slash command, you can use the type `SUB_COMMAND` when creating an sub command

example

{% code title="commands/subcmd.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "sub",
code: `$createApplicationCommand[$guildID;slash;sub commands showcase!;true;slash;[
{
  "name": "sub1",
  "description": "an sub command example!",
  "type": "SUB_COMMAND" 
},
{
  "name": "sub2",
  "description": "second sub command example",
  "type": "SUB_COMMAND" 
}
]
```
{% endcode %}

{% hint style="danger" %}
you cannot add an normal slash option while adding an sub command type at the same time so you will have to use sub commands only for that
{% endhint %}

when executing the code you will notice that you have 2 sub commands being linked to the existing slash command with each different description and it's own options, but what if you want to add options to the sub commands? well then it's easy

<figure><img src="https://cdn.discordapp.com/attachments/647127947144069120/1029354603055161384/unknown.png" alt=""><figcaption><p>how sub commands look like in general</p></figcaption></figure>

let's for example add an option to one of them

{% code title="commands/subcmd.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "sub",
code: `$createApplicationCommand[$guildID;slash;sub commands showcase!;true;slash;[
{
  "name": "sub1",
  "description": "an sub command example!",
  "type": "SUB_COMMAND",
  "options": [
       {
          "name": "user", 
          "description": "example option", 
          "required": true, 
          "type": "USER"
        }
        ] 
}]
```
{% endcode %}

as you can see it will create the sub command with the option `user` shown below here

## responding to sub commands

now that you have created an sub command, you can respond to it by adding `$onlyIf[$interactionData[options._subcommand]==sub_slash_name;]` to your code

let's say that you have 2 sub commands so you will have to do this

{% code title="commands/sub_reply.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = [{
name: "slash-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[hi an reply from sub command!, awesome!]
$onlyIf[$interactionData[options._subcommand]==sub_slash_name1;]`
},
{
name: "slash-name",
type: "interaction",
prototype: "slash",
code: `$interactionReply[hi an reply from another sub command!, awesome!]
$onlyIf[$interactionData[options._subcommand]==sub_slash_name2;]`
}]
```
{% endcode %}
