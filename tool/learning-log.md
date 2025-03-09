# Tool Learning Log

## Tool: **P5Play**

## Project: **Cat Chance Game**

---

### 10/19/24:
#### Intro to P5Play: Sprites
* P5 is a code library that has a multitude of precoded objects and functions coded in JavaScript that is then used to build our own code, p5play is an addition that adds more to it
* I watched an [Intro to p5play - Sprites](https://youtu.be/ZQ23FHfgA0A?si=oRWzUChn_Sgg8_Po) video to follow along with and understand the concept of p5play better
* When creating sprites there is a shortcut of including the position and size inside of the `Sprite()` parenthesis. Ex: `let block = new Sprite (40, 100, 50, 60)` The values are the x-axis, y-axis, width, and height, respectively 
* Using `windowWidth` and `windowHeight` when creating a new canvas will make it so the canvas fits the size of the window. Ex: `new Canvas(windowWidth, windowHeight);`
    * Can also create an aspect ratio for the canvas instead of setting specific dimensions. Ex: `new Canvas("1:1");`
* I tinkered around with all most of the different attributes to change the shape and appearance of the sprite and discovered that the smaller the y-axis value, the higher the sprite goes.
![sprite attribute tinkering](p5play-sprite-att-tinker.png)
* Sprites have a default velocity of 0 but can be changed with `.velocity.x = ` or `.velocity.y =`. Positive x value will make the sprite travel to the right and negative value will travel left. A Positive y value will travel down while a negative value will travel up. Activating the velocity for both axis at the same time will have the sprite travel diagonally

* When I was taking notes on Grouping from the p5play website I didn't really understand how it worked, but after watching the video demonstrate it I think I understand it better now, the p5play website and the video use different methods but I think they generally mean the same thing. The video used `for (let i=0; i < 5; i++){let block = new Sprite ()}` while the website used `while (dots.length < 24) {let block = new block.Sprite();` and if it means what I think it means then as long as the amount of current amount of sprites is lower than the specified number, then the loop will keep creating copies of the sprite until the number is met.
* I messed around with the sprite sizes as they collided with each other and noticed that the size of the sprites do affect how they bump into each other like how physics actually works: the smaller the sprite is the less impact it'll cause and vice versa.

### 10/27/2024:
#### Img Sprites and physics
Because the project will require the use of a lot of custom image sprites, I learned about image sprites in p5play
* To set a sprite to an image, it needs to set on a url pathway to the file. e.i. `moustache = new Sprite();
  moustache.img = 'moustache_PNG37.png';`
* My image was way too big when it loaded in so I used `moustache.image.scale = .20` to scale it down to a fifth of its default size, though the website recommends to change the actual size of the img in the file if such issues occur.
* On the p5play website, it uses `sprite.debug = mouse.pressing();` to show the sprite's hitbox when the mouse is clicked, so I used that as well to check my sprite's hitbox. I found that the sprite's hitbox was what would have been the default sprite square. Because of this the hitbox was off centered and too small for the image
![moust tinker1](https://github.com/user-attachments/assets/76f56e29-ef67-4181-a2a4-f7e0b42739d3)

* I used the width and height properties to expand the hitbox's size to fit the sprite better and used `.offset` to shift the hitbox's x and y axis to center it on the sprite
* My final code looked like this:
```js
moustache = new Sprite();
moustache.img = 'moustache_PNG37.png';
moustache.image.scale = .20
moustache.image.offset.y = -10;
moustache.image.offset.x = 29;
moustache.w = 430;
moustache.h = 100;
```
This is what the hit box looked after:
![moust tinker2](https://github.com/user-attachments/assets/6daaf82a-240d-45d1-b599-d1e7133f132c)
* It is important that a sprite's hitbox is accurate to its size to make sure that it interacts with other sprites properly.
  * If the the hitbox is too small, the sprites will overlap, and if the hitbox is too big, the sprites will appear like they did not touch
 
Physics
* Colliders are used to determine collisions between sprites and are set at dynamic by default. Static colliders do not move, kinetic colliders are moved by the program, none collider does not collide with other sprites
* `world.gravity.y;` is used to activate gravity, increasing the y value will increase the speed the sprites will fall.
* I created a floor sprite and gave it a slant using `floor.rotation = 20;` and made its collider static so it wouldn't be affected by gravity and let the other sprite fall on it.
   * Because the sprite's hitbox is retangular it only slid for a little bit before stopping, but when it gave the sprite a round hitbox by setting it's diameter to 40, the sprite rolled along the floor sprite.
My tinker code looks like this:
```js
   let moustache, floor;

          function setup() {
            createCanvas(windowWidth, windowHeight);
            world.gravity.y = 10;

            moustache = new Sprite();
            moustache.img = 'moustache_PNG37.png';
            moustache.image.scale = .20
            moustache.image.offset.y = -10;
            moustache.image.offset.x = 29;
            moustache.x = windowWidth/2
            moustache.y = 100;
            // moustache.w = 430;
            // moustache.h = 100;
            moustache.diameter = 40

            floor = new Sprite();
            floor.w = 1000;
            floor.y = windowHeight-200;
            floor.collider = 's';
            floor.rotation = 20;
          }
```

### 11/11/24
Because my project involves a lot of random generating I wanted to test out what I learned in my project with sprites.
* I took my random number generating code snippet and assigned it to a `rng` variable then I wrote an `if else` function to make it so that if the value was equal to 1, then a sprite would be made. This didn't work.
* I back tracked and made things simpler, taking things step by step to see which part of the code was wrong and which part worked
* I set the `rng` value to 1 and changed the `if` statement to set the sprite's color to blue when the value of 1, this worked.
``` js
   var win
   var rng = 1

      function setup() {
         createCanvas(windowWidth, windowHeight);
         win = new Sprite();
      }

      function draw() {
         background(220);

         if (rng == 1) {
            win.color = 'blue';
         }
      }   
```
* Next I re-added the random value code to generate a number from 0 to 4 and set the `if else` function if set the color to blue if the value was `<=` 1 and the color to red if the value was `>=` 2. This makes the sprite have a 50% chance of being either red or blue
* Since this works I decided to try out the numbers that we will use in the game
``` js
   var win
   var rng = Math.floor(Math.random()*101)

      function setup() {
         createCanvas(windowWidth, windowHeight);
         win = new Sprite();
      }

      function draw() {
         background(220);

         if (rng > 1 && rng < 75) {
                win.color = 'brown';
            } else if (rng > 75 && rng < 95){
                win.color = 'grey';
            } else if (rng > 95) {
                win.color = 'yellow'
            }
      }   
```
* To make sure this works I refreshed the viewing page multiple times until I saw each other several times and the rates that each color popped up matches their respective probabilty.
<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->

### 11/24/24
Now that I can generate different outcomes depending on the value that is generated, I want to make it so that function happens when I click a button.
* I look up a video on [keyboard and mouse inputs for p5play](https://www.youtube.com/watch?v=s-nFqp4Jd3k)
* I also looked through the p5play learn pages for a certain piece of mouse input, which is `if (mouse.presses())`
To start off simple I set it so the sprite's color becomes red when I click the mouse


``` js
            var pull

            function setup() {
                createCanvas(windowWidth, windowHeight);
                pull = new Sprite();
            }

            function draw() {
                background(220);

                if (mouse.presses()) {
                    pull.color = 'red'
                }
            }
```
After confirming that it worked I then replaced the fixed `pull.color='red'` with the conditional from before to create a 50/50 chance of the sprite becoming red or blue
``` js
if (mouse.presses()) {
                    rng = Math.floor(Math.random()*2);
                    if (rng == 0){
                        pull.color = 'red'
                    } else {
                        pull.color = 'blue'
                    }

                }
```
Then I moved onto putting the entire chunk of conditionals into the function to generate brown, grey, or yellow when I click my mouse
``` js
               if (mouse.presses()) {
                    rng = Math.floor(Math.random()*101);
                    if (rng > 1 && rng < 75){pull.color = 'brown'}
                    else if (rng > 75 && rng < 95){pull.color = 'grey'}
                    else if (rng > 95) {pull.color = 'yellow'}
                }
```
To go even further, instead of just changing the sprite's colors, I made it so that it would change between the custom sprites I made for the final project and it works! The next step will to have the program choose a sprite from an array because the `brown`, `grey`, and `yellow` were only the rarities and there will be multiple sprites in each rarity.

### 12/2/24
Before I get too carried away with just the generation of sprites because that is mostly javascript code, I have to learn how to do the other components of my game. This time I wanted to figure out how to create sprites after the user clicks a button because that is more similar to how they will play the game in the future.
* I first googled "p5play buttons" and found a [p5.js](https://p5js.org/reference/p5/createButton/) site with the information I needed.
   * The website with a function example along with the code with comments describing the function of different parts of code which was really helpful.
   * `createButton()` is assigned to a variable to create a button, and then a string or a number is put into the parenthesis to be displayed on the button.
   * `.mousePressed()` is put after the button variable name and the code that is run once the button is pressed is placed inside the parenthesis, this is often a function that is being called by the button.
```js
let button = createButton('click me'); //creates the function

function repaint() { // function
  let g = random(255);
  background(g);
}

button.mousePressed(repaint); // pressing button calls the function
```
But instead of having the button change the background color, I made a different function that created one new ball sprite when the button was pressed:

```js
let button = createButton(`ball`)
button.position(100, 100);

button.mousePressed(newBall);

function newBall(){
   new ball.Sprite(windowWidth/2, windowHeight/2);
}
```

This time the button calls the `newBall` function that makes a new sprite in the center of the page. 

**Note: this does not delete the previous sprite and replace it with a new one, it only stacks the sprite on top of each other, hence if stack is moved it _will_ explode into a bunch of sprites.**

To fix this issue I used the `.removeAll()` property I found on p5play's [sub group](https://p5play.org/learn/group.html?page=5) page and I put it in the `newBall` function right above the code part that created the sprite so that it'd delete the previous sprite and _then_ make a new one
* To make sure that this worked I applied `world.gravity.y = 1` so that the sprite would move out of its original location so I can see if the sprite is removed and replaced instead of just stacking on top of each other.

Now I can connect the button to the functions that will generate the random cat sprite for the user.

### 12/30/24
Continuing with buttons, now that I could create new sprites with the click of a button, I wanted to try tweaking the button function so that it "uses up values" in order to run. The premise is that the button will subtract one from a monetary value, create a sprite, and then adds one to a counter value. And if there isn't enough "money" then the function won't run.

Starting with the value counting, I created a `variable` called "spent" with the defined value of 0, and another `variable` called "money" with the defined value of 100. Then I used `text()` inside the `draw` function to display the two values.
``` js
let spent = 0;
let money = 100;
 function draw() {
   background(200);
   textSize(100);
   text("spent: " + spent,width/2-25, height/2-150);
   text("money: " + money, width/2-125, height-500)
}
```
![image](https://github.com/user-attachments/assets/e1026d65-50f1-4d55-b967-9817fc79c181)

Then to change the values everytime the button is pressed, I added `spent ++` and `money --` to the `newBall` funciton. That way, everytime the `newBall` function runs to create a new ball sprite, one is subtracted from `money` and one is added to `spent`.
```js
let button = createButton(`buy ball`) //make button 2
button.position(100, 100);

function newBall(){ //button 2 function
   ball.removeAll();
   new ball.Sprite(windowWidth/2, windowHeight/2);
   spent ++;
   money --;
}
button.mousePressed(newBall); // call button 2 function
```
![image](https://github.com/user-attachments/assets/79e3bfa4-4108-4388-b1ce-8240f965e0e1)

Next I had to condition the function to run only when there is enough "money". I added an `if` statement inside of the `newBall` button function to run if there was at least 1 money, else a new ball sprite will not be made.
``` js
function newBall(){ //button 2 function
   if (money >= 1){
      ball.removeAll();
      new ball.Sprite(windowWidth/2, windowHeight/2);
      spent ++;
      money --;
   }
}
```

https://github.com/user-attachments/assets/5a777384-7334-49b3-a322-728551c98fe6

You can see that everytime I click on the `new ball` button, one sprite is created and the values of `money` and `spent` decrease and increase accordingly. And once `money` is decreased to the value of 0, no more sprites are made.

### 1/12/25
Now that I've figured out how to make buttons, how to create new sprites, how to generate random values, and more, I wanted to combine everything together. In order to do this I looked back at the different tinkering files I've been accumulating over the past months. 
* To start off I first made a new button with the basic function of generating a number between 0 (inclusive) and 100 (excluded).
``` js
         var rng

            function setup() {
                createCanvas(windowWidth, windowHeight);
                var box = new Sprite(1000, 500, 50, 50);
                box.color = 'white'

                let pull = createButton(`click me`) //make `pull` button
                pull.position(100, 100);

                pull.mousePressed(genRarity); //calls `pull` function when its pressed

                function genRarity(){ //`pull` function
                    rng = Math.floor(Math.random()*100); //generates a value ranging of 100
                    console.log(rng)
                }
            }
```
* Next I touched up some of the if/else code from my random generator function and added it into the `pull` button function
  ``` js
           var rng
            function setup() {
                createCanvas(windowWidth, windowHeight);
                var box = new Group();

                let pull = createButton(`click me`) //make `pull` button
                pull.position(100, 100);

                pull.mousePressed(genRarity); //calls `pull` function when its pressed

                function genRarity(){
                    box.removeAll();
                    new box.Sprite(windowWidth/2, windowHeight/2);
                    rng = Math.floor(Math.random()*100+1); //generates a value ranging of 100
                    //box color differs base on rng value
                    if (rng <= 75){box.color = 'brown'; return "r"}
                    else if (rng > 75 && rng <= 95){box.color = 'grey'; return "sr"}
                    else if (rng > 95) {box.color = 'yellow'; return "ssr"}
                    console.log(rng)
                }
            }
  ```
In the `Math.random()` part I added `+1` after `*100` so that instead of generating a number between 0 and 99, it would properly generate a number between 1 and 100. The `*100` sets the 0 to 99 range and then the addition of 1 at the end raises it to 1 through 100. This way I won't be confused about what numbers are included and the proper range size of numbers. 

This all creates a box representing the rarity of the item with brown being rare, grey being super rare, and yellow being super super rare.

Next thing I want to try is to make the "box" interactable so that the user will be able to "open" the box to obtain their item. So far I think I've managed to set up the function by loosely glancing over [this piece of code](https://editor.p5js.org/mbardin/sketches/O9daqLpj_) but it doesn't actually work for some reason. I will try to look more in depth later.
``` js
 box.onMousePressed = function() {
                    box.removeAll();
                    }
```

### 2/24/25
Me trying to figure out how to make a sprite clickable probably shaved some years off of my lifespan. Did I want to rip my hair out? Yes. Was it worth it? Also yes.

When I searched "p5play clicking on sprite" I came upon a web editor [demo](https://editor.p5js.org/mbardin/sketches/O9daqLpj_) about `.onMousePressed` that would carry out a function after that sprite was pressed. But when I tried the code in my IDE it didn't work, nothing happened when I clicked on the sprite.
``` js
var sprite = new Group()
new sprite.Sprite()
sprite.onMousePressed = function(){
   sprite.color = "blue"
}
```
I fiddled around with it a few times but it just wouldn't work at all. At one point I thought it was something I was doing wrong so I copied and pasted the entire code from the demo into my IDE to check if it actually worked, and it turns out that the code that worked in the demo doesn't work in my IDE for some reason.

After some more failed attempts at different codes and a short [stackoverflow](https://stackoverflow.com/questions/79411871/how-to-detect-a-click-on-a-sprite-in-p5play) thread I had basically given up the idea of making the sprite clickable. Instead of having a function carry out when the sprite is clicked, I has going to make another button that would carry out the same function.

With this method, I made it so that when the `pull` button was pressed a new `open` button would be created along with the sprite.
``` js
var pull = createButton(`pull`) //make pull button
pull.position(200, 200);

pull.mousePressed(genRarity); //call `pull` function
function genRarity(){ //`pull` function
   var open = createButton('open')
   open.position(100, 100);
   box.removeAll();
   new box.Sprite(windowWidth/2, windowHeight/2);
}
```
Then I was going to add a function to the `open` button until I decided to do some last minute desperate digging for clicking on a sprite.

That's when I found [this video](https://www.youtube.com/watch?v=s-nFqp4Jd3k) on keyboard and mouse inputs with p5play and in the last seconds of the "keyboard input" chapter in the video, the creator shows a snippet of p5play's `sprite.mouse` and I felt like I had just struck gold. I immediatly went to test it out in my IDE to see if it worked.

In my little test I made it so that the sprite is default colored red, blue if the mouse clicks on another part of the screen, and delete the sprite when the mouse clicked on the sprite.

https://github.com/user-attachments/assets/0ba12fb6-7aba-42b4-affc-59335a1d31ea

I don't think I have ever felt such victory over the simple deletion of a sprite before. I then added it into my bigger code with the button and the rng but this time instead of only deleting the "box" sprite, it would also make a new "cat" sprite by adding `new cat.Sprite()` in the `box.mouse.pressed()` conditional function.

https://github.com/user-attachments/assets/cf2c216d-ec74-4a85-96be-71e671e9baa0

### 3/8/25
The next bump I hit was when trying to attach the cat picture pngs onto the sprite to set the sprite's png but the png wouldn't appear, the sprite was still the default ball. I trialed and errored things that I thought might've affected it, maybe somehow the `if()` statement was doing something, maybe it was the png location, png name, etc. Then I thought maybe whether it was in the `setup` function or the `draw` function made a difference, but when I tried to set the pngs for the box crates, those didn't work either.

Then I found out it was because the sprite was a `group`. If the sprite is in a group the png won't work.
``` js
//does not work
var crate = new Group()
crate.new Sprite()
crate.img = 'r-crate.png'

//works
var crate = new Sprite()
crate.img = 'r-crate.png'
```



