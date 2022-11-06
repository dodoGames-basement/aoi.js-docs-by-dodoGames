# toggle button switches

toggle button switches let's the user basically click a button to enable a feature as well as disable it by clicking on the same button, this can be useful for such as self roles, making a settings commands for bunch of features that is basically toggle a feature, etc



## Getting Started

for this example, we will start with multiple `$if` for a interaction cmd, as well as a variable

{% code title="commands/switch.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = [{
name: "switch",
code: `click on this button to toggle an certain option to either disable it or re-enable it
$addButton[1;Toggle;primary;toggle;no;🔄]
`
},{
name: "toggle",
type: "interaction",
$if: "v4",
prototype: "button",
code: `$if[$getServerVar[option]==false]
$interactionReply[enabled the Option]
$setServerVar[option;true]
$else
$if[$getServerVar[option]==true]
$interactionReply[disabled the Option]
$setServerVar[option;false]
$endif
$endif
`
}]
```
{% endcode %}

if the option is disabled then it will automatically detect that using `$if` and then use the first `$if` to enable it, same thing if it was enabled then it would disable it again with the second added `$if`
