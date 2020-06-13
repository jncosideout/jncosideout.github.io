---
tags: mancala Covid19
---

Despite some significant world events this week, I have made good progress on _Mancala World_ (the working title of my app).
First the market had a flash crash, then on Wednesday March 11, Covid19 was declared a pandemic by the World Health Organization.
In the U.S., the President declared a National Emergency for Covid19.

Many states are beginning to force local businesses to close and residents told to stay home, but here in Texas no official orders have been issued as far as I know. On the bright side, I can take the opportunity to finish working on this app!

## Mancala Progress Update:

1. Finished "unlock new game modes" feature

    This is the only feature I will not advertise except for here and to my TestFlight testers. By storing an offline list of the user's match outcomes of games played online, I can check to see if enough games have been won to unlock a new game mode that allows players to start a game with five beads per pit instead of four. And after winning some more games, players unlock six beads per pit.

    I'm storing the list offline, i.e. locally on the phone because Game Center allows users to delete completed matches or resign from active ones. Then, I check the list every time the user turns the app on or completes a game. When they meet the thresh-hold to unlock the user will get a notification that will present the new option in the settings menu.

    I won't limit the game modes that this option can be used on, so it will be possible to start an Online Game with five or six beads per pit even if the other player does not know they about it. Hopefully this will keep things interesting for players and give them the incentive to play more online games.

2. Changed backgrounds to use static images

    Previously, I was using the same code to generate [animated gradients for the game background](http://augmentedcode.io/2017/11/12/drawing-gradients-in-spritekit/) as I was to generate static gradients for the green background in the menu. Because I was getting runtime errors from that code, I decided to switch to static .png images for the menus. This meant going back to Gimp 2.10 to create these images for each iOS device's respective screen size.

    Once I had an image for each iOS device, I needed a way to [identify the exact iOS device model](https://stackoverflow.com/questions/26028918/how-to-determine-the-current-iphone-device-model/30075200#30075200) the user was running so I could grab the correctly sized image. Luckily, I found some very useful code on Stack Overflow for this exact purpose, and it worked very well, despite being somewhat of a hack.

3. Fixed a bug where game info text was staying when changing game modes

    The game info text box at the top of the screen usually says things like "Player 2's turn" or "Player 1 got a bonus turn!"
    but I noticed it wasn't being cleared sometimes when moving from "Vs Computer" to the other game modes, ("2 Player" and "Onine Game"). It turned out that the static `[players]` array used by the AI to keep track of players when running its simulations was behind the problem. Since the other game modes were also referring to this property, the simple solution was to divorce them from it and create new player objects each non-AI game played.
