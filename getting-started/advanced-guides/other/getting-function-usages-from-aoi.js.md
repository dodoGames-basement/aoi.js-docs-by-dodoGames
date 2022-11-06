# getting function usages from aoi.js

did you know you can actually get function usages from aoi.js without using api or anything?, well that's easy using function manager

## function manager

function manager is an thing existing in aoi.js (since 5.1.2) and it's used in ferel (in their own support server) to get info about function usages, this can be useful to avoid getting errors by outdated usages from the official aoi.js doc

## setting up

now you might be asking on how to use function manager?, well here's an simple code

{% code overflow="wrap" lineNumbers="true" %}
```javascript
$djsEval[client.functionManager.usage.get("$message");yes]
```
{% endcode %}

{% hint style="warning" %}
you must type function names in small letters as typing them in uppercase letters like `$addButton` will result in undefined error
{% endhint %}

below the code it will get the usage of an certain function you entered it's name and then it will return the usage (without the function name being shown in it) you can use this in case if you believe you find an outdated usage of an certain function from aoi.js official docs or you don't want to go to their support server to use ferel



## cmd example

now we have an code that let's us get info about usage of an certain function name, let's make an command dedicated to that

{% code title="commands/func.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
    name: "func",
    aliases: ["aoijs", "aoi"]
    code: `$title[Aoi.js Function Search]
    $addField[function Usage;\`\`\`$message$djseval[client.functionManager.usage.get("$message");yes]\`\`\`;no]
    $addField[function name;\`\`\`$message\`\`\`;no]
    $onlyIf[$djseval[client.functionManager.usage.get("$message");yes]!=undefined;invalid function provided]
$onlyIf[$message!=;you need to provide an function name]
    `
  }
```
{% endcode %}
