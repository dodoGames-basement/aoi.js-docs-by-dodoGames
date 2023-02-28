# parser support

since v6, json parser has been removed, there is now recently a alternative that let's you add stuff to normal functions like buttons and other stuff you used to in json parser but with also extra useful features like ephemeral, etc.

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

## some kind of examples

buttons including embeds inside `$sendMessage`: &#x20;

```javascript
$sendMessage[{newEmbed:{title:hi}}
{actionRow:{button:hello:1:helloButton:no}}
]
```
