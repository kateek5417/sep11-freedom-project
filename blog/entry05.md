# Entry 5
##### 4/28/25
### Content
As the project comes to a close, me and my partner combined our different parts of our project into one. For the bulk of the process my partner focused on creating the animated background while I focused on the random generation portion of the game. Over spring break my group organized a day to come together to finalize our game by combining and touching up and any works. For our game, my partner and I used [p5play](https://p5play.org/) to create the backgrounds and the sprites while my partners for the other game segment used [kaboom](https://kaboomjs.com/) to create their mini-game. 

This is the result of our work:
![image](https://github.com/user-attachments/assets/e7ff3c18-dcc2-4683-addb-f09db0f3817c)

To combine our code together I had to integrate her IDE code and my IDE code in a new [Github repo](https://github.com/kateek5417/sep11-cat-project). It was a little tricky because if the code was placed in the wrong spot then everything would break; I had to slowly add small parts of her code into my amalgamation of code to make sure each part worked together properly. One part that didn't work in the final code was the music. I had downloaded the file she provided and had her code but it still wouldn't work, but the music worked on her separate code.

To make the background animation, my partner (Xue) preloaded the images by storing them inside a variable. 
```js
 function preload() {
  cloudsImg = loadImage("clouds.png")
  flowerimg = loadImage("flowers.png")
  MuellerSUnimg = loadImage("mueller-sun.png")
  // soundFormats("mp3")
  frenchsound = loadSound("PeriTune_Alleyway-chosic.com_.mp3")
}
```
`function preload()` is used to load up assets before `setup()` and `draw()`

Then she used some `if()` statements so that the images would loop along the x-axis
```js
function draw() {
  textSize(40)
  background(117, 225, 250);
  
  // // sun
  image(MuellerSUnimg, 0 ,0 )
  
  // flowers
  image(flowerimg, flowersX, 0);
  image(flowerimg, flowersX + width, 0);
  flowersX -= 2;
  if(flowersX < -width) flowersX = 2;
  
  // clouds
  image(cloudsImg, cloudsX, 0);
  image(cloudsImg, cloudsX + width,0);
  cloudsX-= 3;
  if(cloudsX < -width) cloudsX = 0;
}
```
In the end, I like how our project came out. Though it's a silly game, we put a lot of effort into it and made a game we all share a hobby of.
[Here for project preview ](https://kateek5417.github.io/sep11-cat-project/)


### Skills
Two skills I used were collaboration and communication. Throughout the making of this project I've had to communicate with my partners on working details of different parts of the project as well as designating tasks, asking for help, and brainstorming new ideas. As I worked I would also consult with my collaborators on how the product could be improved upon and what things could be added..

### EDP
At this poin of the engineering design process we have finished the MVP of our project and are now working on adding on extra things to improve certain aspects. Additionally we still need to find a way to share data from both games with each other. The next step would be communicating our results with everybody else.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
