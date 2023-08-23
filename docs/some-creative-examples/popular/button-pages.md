# Button Pages

## getting started

you can actually make a command that has multiple pages of embeds using buttons, it's pretty simple but you gotta deal with multiple custom ids for the interactions at least



## setting up

let's start with example of that as a **help** command! with at least 2 **pages**, we can have something like this

{% code title="commands/pages.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
name: "pages",
code: `$title[page 1]
$description[content here]
$footer[page 1/2]
$addButton[1;Previous;primary;previous;yes]
$addButton[1;Next;primary;next;no]`
}
```
{% endcode %}

now you might be wondering how is that even possible?

it's pretty actually easy to do that

we can have examples like this

{% code title="commands/pages.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = [{
name: "pages",
code: `$title[page 1]
$description[content here]
$footer[page 1/2]
$addButton[1;Previous;primary;previous;yes]
$addButton[1;Next;primary;next;no]`
},{
name: "next",
type: "interaction",
prototype: "button",
code: `$interactionUpdate[;{newEmbed:{title:page 2}{description:content here}{footer: page 2/2}};{actionRow:{button:Previous:primary:previous:no}{button:Next:primary:next2:no}}]`
},
name: "previous",
type: "interaction",
prototype: "button",
code: `$interactionUpdate[;{newEmbed:{title:page 1}{description:content here}{footer: page 1/2}};{actionRow:{button:Previous:primary:previous:yes}{button:Next:primary:next:no}}]`
}]
```
{% endcode %}

{% hint style="danger" %}
be mindful that this is will gonna get messy as the more you add more custom pages the more the code gets messy and flooded with bunch of codes you will also gotta deal with the custom ids for almost all the of the buttons for pages to change
{% endhint %}
