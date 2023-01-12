# removing unneeded numbers of $ram

as you know by default aoi.js returns the current used ram of your bot project, it also includes random numbers after something like `61` which can look weird, if you want to remove it then this tip is for you!

## getting started

you can use `$round` which basically Rounds the number to the unit

```javascript
$round[$ram]
```

by including `$ram` inside `$round` you have removed the unnecessary numbers so you can make your bot seem more professional

<figure><img src="https://cdn.discordapp.com/attachments/1061624652054679553/1063229995687882762/image.png" alt=""><figcaption><p>output</p></figcaption></figure>
