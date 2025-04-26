# Entry 2
##### 12/9/24

### Content
For the past few months I have been learning the tool [p5play](https://p5play.org/) to help me buld my Freedom Project at the end of the year. The component that I've worked on the most are `Sprites` and more recently user inputs because they make up a large portion of the game function. The first thing I did was to create a `tinker.html` file in my IDE and copied-pasted the code links into the file so that I could try out code as I learn and use other sources to guide me. To start me off with something simple I looked up tutorials for sprites and found this [video introducing p5play and basic sprite functions](https://www.youtube.com/watch?v=ZQ23FHfgA0A&t=1770s). The video goes through a list of different properties that can be applied to sprites to change their apperance, position, or orientation, and demonstrates them by applying several of them on a sprites. I followed along with the properties but changed the values to see how much it affected the sprite.
![p5play-sprite-att-tinker](https://github.com/user-attachments/assets/d7c39fda-c402-47a2-b6ae-7f8ce29a5251)

The `.x` and `.y` properties determines the sprites X and Y coordinates, `.rotation` determines how much its rotated, etc. The properties are pretty self-explanatory which makes them easy to understand and use.

After covering the basics of sprites and sprite properties, the video moved onto **velocity**. Every sprite has the default velocity of 0, meaning its not moving, until its velocity is determined by the `.velocity` property. The direction and speed of the sprite is determined by the values of the `.velocity.x` and `velocity.y` properties, positive x or y values would make the sprite move right or up respectively, and vice versa for negative values. The bigger the value the faster the sprite moves in that direction, i.e. if `velocity.x=10` then the sprite will move quickly to the right, if `velocity.y=-10` then the sprite will move quickly down. I was fiddling around with sprite sizes when they were colliding into each other and found that the size of the sprites influence how they interact with each other; larger sprites move less when collided into that smaller sprites.

Staying on the topic of sprites, the next thing I wanted to learn how to do was to have the sprites be images, which was easily achievable by setting the `.img` property to equal to the image png. For example: 
```js
moustache = new Sprite();
moustache.img = 'moustache_PNG37.png';
```
Though the sprite's apperance might seem bigger its actual hitbox hasn't changed from the small default square. Lucky p5play offers a way to view a sprite's hitbox by using `sprite.debug = mouse.pressing();`.
![380522947-76f56e29-ef67-4181-a2a4-f7e0b42739d3](https://github.com/user-attachments/assets/31e80028-8c16-4cbd-99e7-49f1d73e5271)
I then used the height and width properties to alter the size and shape of the hitbox to fit the sprite's size
```js 
moustache = new Sprite();
moustache.img = 'moustache_PNG37.png';
moustache.image.scale = .20
moustache.image.offset.y = -10;
moustache.image.offset.x = 29;
moustache.w = 430;
moustache.h = 100;
```
I while I was trying to size the hitbox, I noticed that it wasn't centered with the image so I used `.offset` to move the hitbox, not the sprite. This is what the code resulted in:
![380523202-6daaf82a-240d-45d1-b599-d1e7133f132c](https://github.com/user-attachments/assets/70bd613c-8da2-412e-b540-3e39c02f516d)

P5play's [Learn}(https://p5play.org/learn/index.html) page offered a page on [sprite physics](https://p5play.org/learn/sprite.html?page=1) which included gravity and colliders properties. Colliders are used to set how sprites interect when they collide into each other. By default colliders are set to dynamic and don't move unless moved by something else (could be another sprite, gravity, etc), static colliders do not move, and kinetic colliders move the sprite based on code rather than interaction.

To test there colliders I created a slanted static floor using the `.rotation` property and made it static with `collider = 's'`. 
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
Then with `world.gravity.y` I can make the `moustache` sprite fall down onto the slanted `floor` sprite and because I changed `moustache`'s hitbox round with `moustache.diameter = 40`, the sprite rolled down the floor which I caught a picture of:
![image](https://github.com/user-attachments/assets/126490f7-7647-4790-b30b-2ff923c755e3)

After this I took some tinkering with `loops`, `conditionals`, and `Math.random()` to be able to randomly generate different sprites based on certain interger ranges. To test out whether the code was generating properly I needed a way to control when the program would generate a new value and its outcome. I browsed through p5play and found a piece of code that would work perfectly for my testing on the [subgroup](https://p5play.org/learn/group.html?page=5) page. I used `if (mouse.presses())` to activate my random number generating (rng) code.
``` js
if (mouse.presses()) {
                    rng = Math.floor(Math.random()*101);
                    if (rng > 1 && rng < 75){pull.img = 'eepycat.png'}
                    else if (rng > 75 && rng < 95){pull.img = 'loafcat.png'}
                    else if (rng > 95) {pull.img = 'notgojo.png'}
                }
                console.log(rng)
```
This was the piece of code I was testing and I used the `if (mouse.presses())` condition to activate it. When the mouse button is pressed then a number between 0 and 100 will but generated depending what that number is different images will pop up on screen. I used `console.log(rng)` on the bottom so that I could check if the generated number matched up with the displayed result.

My plans over the winter break is to finish drawing my sprites for the game because I drew some of them earlier in the year but as assignments increased I've had no time to focus on them. The sprites my group still needs are the boost items, the dispenser machine, the cat crates, the cat food, the hostiles, some remaining cats, and maybe some obstacles. 

### Skills
Some skills I practiced by learning p5play and tinkering on my own were **logical reasoning** and **growth mindset**. When I found that `if(mouse.presses())` code snippet on the p5play website I had to change up some of the code so that it would fit my code, and because it was condition I knew that I could put it infront of my conditional too. As I tinkered and coded, things would come together like puzzle pieces because they continued to build on top of each other. Sometimes thoughts would pop up in my head about what the final product would look like and I would make a mental note to myself that I would need to learn more p5play or tinker more with the code to be able to make the idea happen, like the user interaction and the need to learn about p5play buttons in the future.

### EDP
For the past months I have been **researching** my tool and as I continue to build up my knowledge on it I can start **planning** how I can implement the tool into my code for my final project. But for now I will continue to **research** my tool and learn more about what I can do with it.



[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
