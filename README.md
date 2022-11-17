# Fall2022_CSC532_Project


---
# **Scrum Project 1** #
---

# **Finch, Laurence H** #
## **User Story 1**: As a player, I can click on a menu to exit the game.
1.   I created a menustrip with File - Quit option on frmLevel.
2.   On the quitToolStripMenuItem_Click event, I added code to exit the application.

## **User Story 2**: As a player, I want damages from battle to be a random number between 2 values that I specify.
1.   After researching this, I decided to use the Random function to determine damage created by both the player and enemy.
2.   I created a form called frmRandomBattleDamageInput.
3.   On this form, I created 2 textboxes and 2 command buttons.
4.   One textbox is for the minumum damage allowed and the other textbox is for the maximum damage allowed.
5.   One command button is labeled 'Cancel', which cancels any changes and exits the form.
6.   The other command button saves the changes to the textboxes and exits the form.
7.   I stored the minimum and maximum damage allowed in 'Properties.Settings.Default' (MinRandomBattleDamage and MaxRandomBattleDamage) and when the form opens, it reads and displays the data in the appropriate text boxes.
8.   On the frmBattle form, I created a new instance of the Random class named '_random'.
9.   When the 'Attack' button is clicked, then the code reads the values for minimum and maximum damage from Properties.Settings.Default.MinRandomBattleDamage and Properties.Settings.Default.MaxRandomBattleDamage.
10.   Then a random integer is calculated between these two values and passed to the 'OnAttack' event of the player class.

## **User Story 3**: As a player, I want the enemy icons to be removed once they are defeated.
1.   This one was a little tricky. I had to find a way to remove the icon of the enemy off the form without causing the code to break. This was tricky because of the 'collider' class. I couldn't just make them invisible, I had to dispose of the enemy class created for each enemy, which breaks the code later due to it looking for them.
2.   I decided to add the delete code under the tmrPlayerMove_Tick event, just for quickness. 
3.   I added code to first check to see if the enemy object had already been disposed of (!=null).
4.   Then I checked to see if that enemy had died (Health<=0). If so, then I called the Dispose method for that object.
5.   I tried to dispose of the enemy object after the frmBattle form was closed, but I kept getting errors, so this was the easiest method I could find.  There are probably better options available though.

# **Boyt, Jacob C** #
## **User Story 1**: As a game player, I want to choose my avatar from a collection of possible avatars.
1. I collected six different images of characters to use as avatars in the game.
2. Each of the six avatars, and an empty image called "PickedPlayer" were encoded in the Resources program.
3. Mr. Peanut's design was removed to avoid confusion.
4. After researching C# forms, I made a form entitled "PlayerPicks".
5. Six buttons were added to this form, each of which corresponds to one of the six avatar choices.
6. A message box was added to let the player which avatar had been selected.
7. "PickedPlayer" image, which is used as the player image, is overwritten by the image of the avatar character selected.

---
# **Yusuff Afeez** #
---
## **User Story 1**: As a player, I want a welcoming page to show up first when the game is loaded.

I went about this by
1. Researching online how to create and add form to a project in C-sharp. Youtube videos did help me a lot on this.
2. Implemented the knowledge obtained from watching tutorial on youtube by creating this form on the group project and added a label which allows me to add the welcoming text.
3. I also added a play button to the welcoming screen, serving as a connection point to the rest of the game.
4. I was not able to add the help form to the game as intended before.

## **User Story 2**: As a player, I want to have the option to restart the game
 I went about this by 
1. Researching first how to write a code to restart an application in C sharp.
2. Later on, I implemented the knowledge by writing the code in the formlevel.cs file 
3. thereafter, I tested it and it worked fine in that once the restart button is selected, the current stage of the game is canceled and the game starts again from the beginning without exiting the game. 





---
# **Scrum Project 2** #
---
# **Boyt, Jacob C** #
## **User Story 1**: As a game player, I want to have random Wall patterns chosen from a collection of Wall Patterns.
1. I found three different wall pattern designs were collected.
2. Along with the existing brick wall design, the wall patterns were encoded into the Resources program.
3. The brick wall image was relabeled so that the "wall" Resource image could be overwritten with any of the four design patterns.
4. A random variable entitled "WallPattern" was made, producing an integer of either 0, 1, 2, or 3.
5. The "wall" image was overwritten with one of the four different wall design patterns, depending on which random integer was selected.

## **User Story 2**: As a game player, I want to have random villains chosen from a set of villainous characters.
1. I found nine different villainous characters, three characters each from three major franchises (Indiana Jones, Doctor Who, Universal Monsters)
2. All were encoded into the Resources program, and the three original enemy characters were removed.
3. To avoid issues with how the enemies' movements, health, etc. were defined, the names of the enemy characters were used to define empty images.
4. A integer parameter in the settings labelled "Rogue" was set to zero.
5. A random integer in the FrmLevel, also labelled Rogue, was made, producing an integer of either 0, 1, or 2.
6. The "Rogue" paramter was set equal to the "Rogue" integer.
7. The enemy characters were overwritten by one of the villain groups, dependent on which random integer was selected.

## **User Story 3**: As a game player, I want to change the Final Battle Audio Files based on chosen Avatars and Rogues.
1. For each combination of one of the three BossEnemys and one of the six Avatar choices, I recorded a Final Battle Audio File.
2. Online Recording editors were used to change the pitch and volume of the audio files, and to convert from mp3/mp4 files to wav files.
3. All eighteen Audio Files were uploaded to the Resources program.
4. A second integer parameter, "PlayerChoice", was made in settings and set to zero.
5. In the "PlayerPicks" form, for any of the avatar selections, an integer between 1 and 6 was added to the "PlayerChoice" parameter, corresponding to the button number selected.
6. In the "FrmBattle", for the Final Battle sound file being played, a series of if/else if statements were made for each of the eighteen possible combinations of "Rogue" and "PlayerChoice" parameter integers.
7. If the conditions of the one of the if/else if statements were met, the corresponding audio file was called and played.
8. For troubleshooting, a Message Box was made declaring the "Player Choice" integer in the "PlayerPicks" form.

# **Finch, Laurence H** #
---
## **User Story 1**: As a player, I want the enemy characters to move randomly around the screen.	


1.   I researched different ways of making the enemy characters change direction when they hit either a wall or another enemy character.
2.   I decided on using another timer, named tmrEnemyMove. 
3.   I started with a list of the three enemy characters, with their 'object' name.  This way if there is another enemy character added later, all we'd need to do is add that object to the list. I was trying to find a way to just find all the objects of Enemy class, but couldn't.
4.   I then created a for loop to iterate through the enemies.
5.   If the enemy object was still valid (!=null), then I called their Location method to update their cooresponding picture box.
6.   Under the Character class, I created a new integer variable to store what direction the character is currently moving.
7.   I created a new function called ChooseRandomDirection that takes the enemy object as input and stores a new random direction, not the current direction, in the variable I created in step 6. Directions are 1:left, 2:up, 3:right, 4:down.  I did notice that in using the Random.Next(minvalue, maxvalue) that the maxvalue has to be one more than what you really want. So for a random value between 1 & 4, you have to use 1 & 5.
7.   I then started each enemy moving left.
8.   Then I created an if statement to determine if any of the enemies hit a wall or each other. If they did, then I called ChooseRandomDirection to get a new direction and had the enemy start moving in that direction.

## **User Story 2**: As a player, every time the game starts I want the location of inner walls to change.

1.   After a lot of research, I found a small algorithm to use to create a random map. I used a nxm matrix holding either 0 (open area) or 1 (wall). 
2.   Once the matrix is created, I then loop through it and everywhere there is a 1, I created a new PictureBox named "PictureWall_#" at the cooresponding location on the form and updated the count of number of walls.
3.   Then I modified the existing code, so instead of using the old walls, I loop through all these new pictureboxes and created colliders for them so that the player and enemy characters would bounce off of them.
4.  Now I had to randomly place the player and enemy characters in open areas of the map. I did this by creating a while loop checking if the player/enemy object was null. If it was, then I grabbed a 2 random integers (between 1 and the size of the map minus 1). I then used these two numbers to check the map matrix to see if the value was 0 (open), and if so place the character/enemy there. If it was 1, then I just looped back through until the character/enemy was placed.

---
---
# **Yusuff Afeez** #
---
## **User Story 1**: As a user, I want to assign unique intro voice to selected avatar out of the bunch of avatars available.

I went about this by doing the following:
1. I created audio files with each corresponding to a particular avatar.
2. I used a pitch change application to modulate the pitch of the audio file
3. Thereafter, I downloaded the modified audio file and saved it inside the bin folder of the repository.
4. The third step is repeated for all the remaining audio files.
5. I wrote the corresponding line of codes to run this added feature by editing the FrmLevel
6. I believe all to be working fine as I have tested it and it worked.	

## **User Story 2**: As a player, I want to be able to control my game using pause and play control functions.
1. This is achieved by modifying the existing switch statements and added to it another case that made spacebar key to be the control.
2. I also add a GamePursed function to the body of code already existing. Part of the task of this code is to note down the time at the point of pausing the game so that whenever the game is resumed by pressing the spacebar key, the time will start from where it was before.
3. At the end, I checked it out on my local machine and found all to be working well.
