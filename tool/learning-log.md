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

* When I was taking notes on Grouping from the p5play website I didn't really understand how it worked, but after watching the video demonstrate it I think I understand it better now: Grouping just makes a bunch of the same sprite by creating a kind of loop until a certain amount of sprites is met. The loop defines a limit of how many sprites are to be created and will stop after it hits the specified number.
* I messed around with the sprite sizes as they collided with each other and noticed that the size of the sprites do affect how they bump into each other like how physics actually works: the smaller the sprite is the less impact it'll cause and vice versa.

### X/X/XX:
* Text


<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
