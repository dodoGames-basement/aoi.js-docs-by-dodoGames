# setting up aoi.parser

aoi.parser is an extension for aoi.js parser system that adds features such as ephemeral messages for interaction error messages from `$onlyIf`, including the ability to use different types of select menu such as select menu for [channels](https://aoi-parser.vercel.app/documentation/parsers/component#channelinput) and other types like `{reply:}`, etc.

## understanding what you do

when you setup aoi.parser you agree that all of your usage of parsers will be changed to aoi.parser ones, we recommend viewing [aoi.parser docs](https://aoi-parser.vercel.app/documentation/parsers/embed) for viewing aoi.parser usages of parsers like components, embeds, etc (you may have to scroll down to see all of them though.)

{% hint style="info" %}
if you want to use the original version of parser then you may use advanced setup which allows you to choose on which parser to change to aoi.parser one
{% endhint %}

## setting up parser support

run the following command to your terminal

```javascript
npm i aoi.parser@latest
```

after the package is installed, add the following code to your index.js

```javascript
// parser support
const { Util } = require("aoi.js");
const { setup } = require("aoi.parser");

setup(Util);
```

if you got no errors after restart then you're good to go

## what use cases are aoi.parser for

**Example Use Cases:**

you want to use ephemeral for interaction error messages alongside with `{interaction}` option.

you want to try different types of select menu.

you want to make the bot use discord's reply feature from an function like `$sendMessage` in normal commands.

you want to control on what mentions are allowed in bot commands with allowedMentions Option inside functions like `$sendMessage`

using slash option parsers for creating slash commands using `$createApplicationCommand`

**Examples you don't need aoi.parser for:**

using components parser inside functions like `$sendMessage` in normal commands (you can do that already without aoi.parser).

using files parser for functions like `$sendMessage` in normal commands (you can do that without it as well).

using slash option parsers for creating autocomplete commands (you can do it without it with this guide from [official Aoi.js Docs](https://aoi.js.org/docs/guides/interactioncommands#autocompleterespond-functions--examples)). + note that it's up to your liking of which method you prefer for creating slash options so this is not a force.

&#x20;

## some kind of examples

buttons including embeds inside `$sendMessage`: &#x20;

```javascript
$sendMessage[{newEmbed:{title:embed}{description:click on the button below}}
{actionRow:{button:hello:1:helloButton}}
]

// fact: this code also works without aoi.parser 
// as said in the not needed cases to use aoi.parser
```

interaction error from `$onlyIf` with ephemeral option including interaction option:

{% code overflow="wrap" lineNumbers="true" %}
```javascript
$onlyif[disabled!=disabled;
  Error.
{options:{ephemeral}}
{extraOptions:{interaction}}
]
```
{% endcode %}

using select menu for selecting Text channels Only:

{% code overflow="wrap" %}
```javascript
$sendMessage[{newEmbed:{title:menu}}
{actionRow:{channelInput:channelMenu:select a channel:1:1:no:{channelType:0}}}
]
// use $interactionData[values[0]] for returning the selected channel id from the select menu when responding to select menu for channels in an interaction cmd.

```
{% endcode %}
