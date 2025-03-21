# Entry 1 Tool + Idea
##### 10/28/2024
### Project Idea
#### Background Info
For this year's freedom project, my friends and I have come together to create a multipart game using inspiration from the games we play in our free time. The synopsis of our game is based on the Japanese "gachapon" or gacha system of obtaining items, characters, or other game components through chance. Many famous games use this gacha system as a method of enticing players and as a way for players to obtain new items, some widely known gacha games are; **Genshin Impact**, **Honkai Impact 3rd**, **Honkai Star Rail**, **Project Sekai**, **Onmyoji**, **Arknights**, **Wuthering Waves**, and many more in many different styles. 

These games often have a risk/reward exchange where players exchange the in-game currency to "pull" or "roll" for a certain character (most often of the highest rarity), where the reward would be obtaining the desired character and the risk is spending the game currency and not obtaining the desired item. There is a fixed chance of obtaining different rarities ranging from rare (R), super rare (SR), to super super rare (SSR) with the probability decreasing as rarity increases. Once the user reaches a certain number of pulls, they are guaranteed a random SSR character. Once the user obtains an *SSR* character, the number of pulls reset back to zero. This will all be essential to this section of the game. This [video](https://youtu.be/s_v_g72w-6M?si=7Hdjcp8Kz28orYRe) (0:08-1:22) on Cookie Run Kingdom also explains the gacha system.

#### Game
The main idea of this project is to combine two separate games together into one larger game. **Part A** will be where the user navigates the avatar, a cat, around a 2D tile map to collect the game's currency (cat food) with the help of a variety of boosts to assist the user. The cat food will randomly spawn around the map and the user will have to quickly run around the map avoiding obstacles and hindrances to collect them. The obstacles may consist of puddles of water the player has to go around or dogs that will end the round. The boosts can be cat toys that increase the user's speed for a temporary amount of time, and catnip that can extend the remaining time. The round will have 1 minute of gameplay to collect as much food as they can.

Basic Idea:

![fp-collect-sketch](https://github.com/user-attachments/assets/66b85fdb-5091-4a36-b22e-cdc02b83c559)

**Part B** will be where the user spends the currency they collected to obtain new kinds of cat avatars. For now, we have settled with the idea of having a gumball-looking machine where the cat avatars will be dispensed after inserting the cat food. There will be a total of 15 different avatars with different rarities and probabilities; 7 *Rare*: 75%, 5 *Super Rare*: 20%, and 3 *Super Super Rare*: 5%. Note that there is the chance of obtaining the same cat avatar more than once. 1 pull will cost 10 cat foods and a 10 pull will cost 100 cat foods. Once the user accumulates a total of 50 pulls, they are guaranteed to get a random *SSR* cat avatar. We might add a library system where the user can check what cats they have and have not collected.

### Tool
I decided to use the tool [P5Play](https://p5play.org/) to create Part B with Xue while Ellen and Qilin use [Kaboom](https://kaboomjs.com/) to create Part A. To learn P5Play I will follow the website's [Learn](https://p5play.org/learn/) page where they teach all of the different code snippets that can be used, ranging from sprites to gravity to animation. Additionally, there are also [YouTube videos](https://www.youtube.com/@davidbouchard) on P5Play that demonstrate and tinker with different P5Play codes.

So far I've learned about [Sprites](https://p5play.org/learn/sprite.html) and how to apply different properties such as `sprite.x`, `sprite.y`, and more to determine the position, size, orientation, and color of the sprite. And to set an image as a sprite you can link the sprite through its url pathway:
```js
moustache = new Sprite();
moustache.img = 'moustache_PNG37.png';
moustache.image.scale = .20
moustache.image.offset.y = -10;
moustache.image.offset.x = 29;
moustache.w = 430;
moustache.h = 100;
```
### Skills
The skills I am practicing are **collaboration** and **communication** because this is a bigger project with 4 people working in groups of two on separate functions that will come together as one whole game. In order to ensure that everything goes smoothly and everyone knows whos doing what, we have to communicate with each other, checking on others and how they are doing, as well as working together when someone needs help.

### Engineering Design Process
Right now I think we are in the Brainstorm and Planning stage as we will continue to adjust, add, and change details to the game as we work and tinker together. We will also consider things we can add beyond the MVP. And next, we are going to be learning our tools throughout the year to create our game.

[Next](entry02.md)

[Home](../README.md)
