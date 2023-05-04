# javascript-collision-animation

Add basic boilerplate just like you did for the sprite animation, parallax and movement js projects
Remember to test your code along the way for easier debugging, so in this case use fillStyle and fillRect to ensure the canvas paints properly
Remove the testing variables and initialize a variable called explosions and assign it an empty array
Create an Explosion class and a constructor with xy coordinates as its parameters
Use this keyword to assign xy as variables and assign the parameters to them
Also add the width and height of the variables you are using in the constructor
Reduce the aspect ratio of the sprite you want to use by dividing the spriteWidth and height to the ratio you want (2:1 in this case) and assigning them a new variable (width and height in this case)
Add the image you are using by adding and assigning image variable to new Image() in constructor to create image everyytime Explosion class is created
Add the source image to the construtor as well
Add a frame variable and set it to 0 in the constructor
As usual, add update and draw methods after the constructor to update and draw the explosions
For update, just do an increment of the frame for now
For draw, do a drawImage method on ctx with the full 9 arguments
For sx in drawImage, you are moving horizontally across the sprite file so you multiply spriteWidth with frame (which you are incrementing in update) to move along the sprite file
Since there are no vertical components, only the first element exist in sy at index 0 so sy is 0
sw and sh are the width and height of the sprite respectively
For the last 4 parameters, they determine where on the canvas you want to draw them
Assign x, y, width and height you created in the constructor to dx, dy, dw, and dh
To test the class you just created, add a window event listener for clicks, add a fillRect method for ctx with the coordinates, width and height as arguments, and use the event.target method to draw where you click
To do this, the arguments in fillRect must be made to target the event (in this case e.x or event.x depending on the parameter you put in function()) and the same for y
For now use a fixed value of what you want for width and height
Remember to use fillStyle to change the color of your clicks since default is black
For now the clicks are just created randomly on the canvas, initialize a global variable called canvasPosition and use the getBoundingClientRect method on canvas which if you console.log it will show you the width, height, x and y positions for you to offset in this case
To make sure the object is created where your cursor clicks, you need to offset the top and left of where your event click is happening
Offset e.x by left of canvasPositon and e.x by top of canvasPosition
To be create the objects at exactly the middle of your cursor click, you will need to offset x and y by an additional 50% of the width and height you have designated in fillRect's arguments
Create new variables in the event listener called positionX and positionY and put the calculations of x and y inside them instead
For now remove everything except the new variables you just created and the hardcoded additional offset of 50% in your positionX and Y calculations
Now you want to push the Explosion class objects into the explosions array you created before
You want to move through each frame of the image and delete the last frame of the image when it reaches there
Call push onto explosions in the event listener with the Explosion class as argument
The constructor expects an x and y argument so use the positionX and Y variable you created in the event listener
Created a new function animate
Add a for loop with explosions.length as its limitation and call update and draw for each array item in the explosions array;
Invoke requestAnimationFrame on animate in the function and call animate after the function
Invoke clearRect at the start of animate
Add timer property to constructor
Increment timer in update and add an if condition where you increase frame by 1 when timer reaches 10 cycles
You should be able to see animation when you click now
To center the animation on your cursor, you will need to offset your x and y in constructor by the width and height of your sprite by 50%
Move the x and y variable in constructor to be below width and height so x and y can read the values of width and height
Now offset x by width divided by 2 and do the same for y in constructor
Since we are using push method, the objects stay in the canvas even if you do not see it(console.log explosions after the push method)
The simple method to remove them is by adding an if condition after update and draw in your for loop where if frame is more than 5 in the explosions array, splice 1 explosions array item at i index
Decrement i by 1 after splice to make sure the next object is correctly updated and animated after you remove its neighbour
To keep event listeners clean, create a function called createAnimation and copy paste the code of your event listener into createAnimation and pass event (or e if you use e) as the parameter
Call createAnimation with argument event in the event listener
