# organizing database using multiple tables

if you're a aoi.js user then you already know that by default aoi.js database would store all of variables data into a single file named `main_scheme_1.sql` inside `database` folder within `main` folder

normally this should not bother you but if you want a little advanced stuff to your aoi.js bot then you will learn on how to create multiple tables for the database to store each specific variable dedicated to a specific table!

## getting started

{% hint style="info" %}
as aoi.js v5 uses **dbdjs.db** as the main database then this guide will use **dbdjs.db** option as the main example of all the time however you're free to change these into something else like **aoi.db**
{% endhint %}

you need to add `database` object to your main bot client options

example

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: "DISCORD BOT PREFIX",
intents: ["GUILDS", "GUILD_MESSAGES"],
database: {
    db: require("dbdjs.db"),
    type: "dbdjs.db",
    path: "./database/",
    tables: ["main"],
  }
})
```
{% endcode %}

as you can see, this does nothing until you change stuff there like path and tables, you can add many table names like server-settings, eco-data, etc depending on what features your bot offers

example

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
const aoijs = require("aoi.js")

const bot = new aoijs.AoiClient({
token: "DISCORD BOT TOKEN",
prefix: "DISCORD BOT PREFIX",
intents: ["GUILDS", "GUILD_MESSAGES"],
database: {
    db: require("dbdjs.db"),
    type: "dbdjs.db",
    path: "./database/",
    tables: ["main", "main2", "main3"], // and so on that you can even add many!
  }
})
```
{% endcode %}

## saving variable data to a specific table

now that we have a multiple tables stored within our `database` folder, you can force variables function to save data to a specific table



here are the list of functions with support for tables:

## global vars

`$setVar[varname;value;table?]`

`$getVar[varname;table?]`

## server vars

`$setserverVar[varname;value;Id?;table?]` &#x20;

`$getserverVar[varname;guildID?;table?]` &#x20;

## channel vars

`$getchannelVar[varname;channelID?;table?]`&#x20;

`$setchannelVar[varname;value;channelId?;table?]`&#x20;



## global user vars

`$setGlobalUserVar[varname;value;userId?;table?]`

`$getGlobalUserVar[varname;userID?;table?]`&#x20;



## Message vars

`$setMessageVar[varname;value;messageID?;table?]`&#x20;

`$getMessageVar[varname;messageId?;table?]`&#x20;



## local user vars

`$setUserVar[varname;value;userId?;Id?;table?;]`&#x20;

`$getUserVar[varname;userId?;guildID?;table?]`&#x20;



## custom variables to a specific table

now that you have multiple tables, you can make each custom variables to a specific table

example

{% code title="index.js" overflow="wrap" lineNumbers="true" %}
```javascript
bot.variables({
variable: "value"
} ,'table name') 
```
{% endcode %}



this way you can benefit from database tables a lot
