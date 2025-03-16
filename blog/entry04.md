# Entry 4
##### 3/10/25

### Content
The progress I have been making with my tool is making sprites clickable and working on figuring out the big random at selection when the user opens their crate box. I also finished up the rest of the sprites. 

To click on a sprite I added `.mouse.pressed()` after the name of the box sprite and put it as the conditional of an `if()` statement. I set the function of the `if()` statement to delete all the box sprites.

``` js
function draw(){
  if (box.mouse.pressed()){
    box.removeAll();
  }
}
```

The next thing that I am trying to do is to randomly generate the cat depending on the rarity generated before. I was able to create a default sprite with different colors depening on the rarity but I havent been able to properly attach the cat pngs onto them. With arrays of cats for each rarity, I thought I could `Math.floor(Math.random())` an index of the array.

```js
function draw(){
  if (box.mouse.pressed()){
    box.removeAll();
    if(rarity == 'r'){
      cat.img = rare[Math.floor(Math.random()*7)]
    }
  }
}
```

However this didn't work as I had planned, it would genereate cats from the wrong rarity or not generate any at all. Maybe it is because I didn't upload all the cat pngs into the file tree yet or maybe it is the names in the array.

### EDP
I am now in the brainstorming and creating phases of the Engineering Design Process as I brainstorm about possible solutions to errors and implement the ideas into my IDE.

### Skills
One skill that I have used is embracing failure


[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
