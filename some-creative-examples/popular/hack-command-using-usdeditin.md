# Hack command using $editIn

have you wondered on how to make a hack command in v5? well that's possible using `$editIn`&#x20;

## how

`$editIn` supports multiple replies which for example you can add multiple replies which one of them contains `hi` and the second one `bye`, this can be useful to make a hack command like this

## example

{% code title="commands/hack.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "hack",
code: `
Hacking $userTag[$mentioned[1]] $editIn[5s;20% Complete...;40% Complete...;60% Complete...;80% Complete...;100% Complete... Extracting Email and Password...;**Email:** $get[email]\n**Password:** $get[pass]]

$onlyIf[$mentioned[1]!=$get[id];WHY DO YOU WANT TO HACK ME??]
$onlyIf[$mentioned[1]!=$authorID;WHY DO YOU WANT TO HACK YOURSELF?]
$onlyIf[$mentioned[1]!=$authorID;WHY DO YOU WANT TO HACK YOURSELF?]
$argsCheck[1;Please mention someone to hack!]

$let[pass;$randomText[add random passwords here for eg ;NoobForever@1234;CoderGenius#heckerarmy]]
$let[email;$randomText[add random emails here for eg ;kinotheforgotten@gmail.com;dudewhocancode@outlook.com]]
$let[id;$clientID]
`
```
{% endcode %}

{% hint style="info" %}
the emails in this example command are likely fake including the passwords as well
{% endhint %}
