# parser support

since v6, json parser has been removed, there is now recently a alternative that let's you add stuff to normal functions like buttons and other stuff you used to in json parser

## setting up parser support

run the following command to your terminal

```javascript
npm i aoi.parser@latest
```

after the package is installed, add the following code to your index.js

```javascript
// parser support
const {  Util } = require("aoi.js");
const { parse } = require(`aoi.parser`);
Util.parsers.ErrorHandler = parse;
```

if you got no errors after restart then you're good to go

## some kind of examples

buttons including embeds inside `$sendMessage`: &#x20;

```javascript
$sendMessage[{newEmbed: {title:hi}}
{actionRow: {button: hi :1 : helloButton :no }}
]
```
