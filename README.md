# MSc CGE – Advanced Game Programming 1
# Unreal MiniGame Cube – Individual Report (Mohammad Ali)


#### Members: 

Mohammad Ali


### Introduction:

The objective for the game was get accustomed to using various features of the Unreal Engine 4. Including Blueprints (various), Editor Usage, Event Graphs, and Scripting.

The concept was to create a game loosely based on the Movie 'The Cube', where you wake up in a cube shaped room connected to hundred of similar room that keep moving around, and you need to survive and find your way out of the maze.


### Features:

I choose to tackle some tasks into categories Level, Controls, Game Mode.

Most of these task had multiple sub tasks which will be described below. This was very new to me so learning the engine and editor interface took priority as that was the main goal of the project.


### Level

My implementation revolved around spawnning the character in an empty room, like in the movie. This room was contructed using cubes of various sizes and saved as a blue print, along with some collision triggers that helped the character activate menu items (more on this later)

![room1](https://github.com/mali055/AGP1_Cube/blob/master/img/room1.PNG)

![room2](https://github.com/mali055/AGP1_Cube/blob/master/img/room2.PNG)

The room blueprint was then spawned 27 times in the main level as the center piece of the maze, this rooms will be the only place the character will be.

![level1](https://github.com/mali055/AGP1_Cube/blob/master/img/level1.PNG)

I used the Third Person controller from the Unreal's own content pack examples. This helped set a baseline from my own controller, which was modified to have the menu system mentioned in the next section. It had WASD movement a control that followed over the head, and jump / crouch movement. This was the part where I learned to use the Event Graphs.

![char1](https://github.com/mali055/AGP1_Cube/blob/master/img/char1.PNG)

### Controls

The controls that were inherited from the Third person controller helped but they needed to be modified, it jumped too high (could reach ceiling). and need a climbing mechanics which just dragged him up a wall (didn't want to get into animation), and also not get stuck in the bottom doorway, so let him climb up was a little tricky but managed it. Finally the main part of the controls was the door menu when pressing 'E' a drop menu would pop up explaining the "actions" the player could perform wbased on the vicinity, i had a boolean array that took the trigger collisions and set up which controls would be visible and using the mouse wheel to scroll up/down the menu to select the item and pressing 'E' again would activate the action while pressing any mouse button early would close the menu. As seen below the main actions were just reading, climbing and going through doors. 

![menu1](https://github.com/mali055/AGP1_Cube/blob/master/img/menu1.PNG)

The Interface also needed a clock for the player to be able to identify the "zero time" of the rooms circulating. Which was easy enough to implement. 

![clock1](https://github.com/mali055/AGP1_Cube/blob/master/img/clock1.PNG)

The last thing I wanted to implement but did not get around to doing was a Math calculator from prime numbers and a notepad that stores notes by the player. These were not a priority so were left out.

### Game Mode

This came in two forms the Level Blueprint and the GameMode Blueprint along with my own maze script that handled the logic of how which room the player was in, his surround rooms and how all the rooms in the maze kept moving.

The logic was that I had a single dimensional array representing a three dimensional array of rooms (this was a struct with an XYZ ID (origin), and a numerical ID for the player, and a boolean for if it was a trap or not. This got messy when all the nested loops were needed to access everything. Then a smaller one telling the controller which were the rooms surrounding him. An update timer that rotation all the rooms in the array, The rotation of rooms was by far the more difficult task to do in this project as handling a complicated three dimensional array and moving things around in it. Basically every layer (think onion layers) magically teleported one step ahead in a clock wise / anti clock wise (alternatively to keep it jumbled at all time, if they moved together it would still be easy) direction around a randomly selected axis (at start of game)

![rotation1](https://github.com/mali055/AGP1_Cube/blob/master/img/rotation1.PNG)

Other small mechanics like killing the player in a death room , contecting the values mentioned above with the interfaces were also done.


### Conclusion:

Was satisfied with what i accomplished in this project although i wish more polished mechanics would allow this to be a more presentable demo.


### Bibliography:

[1] 	Unreal Engine Documentation 
https://docs.unrealengine.com/latest/INT/GettingStarted/index.html






