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

P5play's [Learn}(https://p5play.org/learn/index.html) page offered a page on [sprite physics](https://p5play.org/learn/sprite.html?page=1) which included gravity and colliders properties.


### EDP
### Skills

[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
