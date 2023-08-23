# Daily Command with reminder using $setTimeout

in this tutorial you will learn on how to setup daily command for your economy bot with an reminder using the `$setTimeout` function

{% hint style="danger" %}
this function only allows up to 21 days so it's not possible to make an monthly command with it atm, you can still make an weekly command with it
{% endhint %}

## setting up

this guide assumes that you have variable money or cash (whatever you call it) for your economy system if not then you may create one for yourself

{% hint style="warning" %}
this guide by default uses global economy example but you can change it to use local economy by using user local variables
{% endhint %}

let's start with an simple daily command with an button and an cooldown that gives you 100 dollars each day

{% code title="commands/daily.js" overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = {
  name: "daily",
  code: `$title[you have received 100$]
  $description[everyday you can claim your daily reward, so you can get richer!, to get reminded when to claim daily rewards, press button below]
  $addButton[1;Remind me;primary;daily;no;⏲]
  $setGlobalUserVar[money;$sum[$getGlobalUserVar[money];100]]
  $globalCooldown[1d;{newEmbed:{title:heyo slowdown}{description:you have to wait for at least about %time%}}]`
}
```
{% endcode %}

running the command will give you 100 dollars saved to your economy data as well as an button to get reminded of when it's time to claim your daily reward again

now for part of making this work, i will start of with this example

{% code overflow="wrap" lineNumbers="true" %}
```javascript
module.exports = [{
name: "daily",
type: "interaction",
prototype: "button",
code: `$interactionReply[you will be reminded after one day of daily!;;;;everyone;yes]
$setTimeout[remind;1d;user: $interactionData[author.id]] 
`
},{
  name: "remind",
  type: "timeout",
  code: `
  $title[you can now claim your daily reward]
  $description[it's been a day ago since you claimed your daily reward!]
  $color[BLURPLE]
  $dm[$timeoutData[user]]
`
}]
```
{% endcode %}

<figure><img src="https://cdn.discordapp.com/attachments/753177960617607211/1029001691984568390/unknown.png" alt=""><figcaption><p>output from timeout command after waiting</p></figcaption></figure>

so in this example, first of all we make the button `daily` respond to promise that the user will be reminded after one day of claiming their reward, so it then set the timeout to about one day once pressed by the author, after timeout command execution (after a day) it will dm the user that it's time to claim their reward again since it's been an day ago since they successfully did claimed reward



## Conclusion

now that you have made an daily command with an reminder system to dm the user about it, you're good to go, you can indeed take an inspiration from this guide and make your even better daily commands with reminder system as well as weekly command too
