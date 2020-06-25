---
tags: [mancala]
date: 2020-05-24 14:29:58
---
## - Mancala Progress Update -
#### Monday:
- tried to test last fix for the scenario <a href="{%- post_url 2020-05-17-finishing-mancala-transition-overhaul -%}#AI-interruption">"AI interrupted by Online Game notification"</a>
- applied fix to "online bonus turns not saving" bug
- notifications on test devices are not working but I can receive some incoming from TestFlight testers
- found a bug accidentally: the 'winner takes all' end-of-game animation causes a crash when a player ends the game by capturing, leaving nothing to clear and that causes an 'index out of bounds' fatal error

##### other events
- had 2nd team meeting for martial arts class on Jitsi, discussed [history of Sayoc](https://sayoc.com/history/) and traditional greetings

#### Tuesday:
##### Game Center and local notifications
It appears that notifications are not being sent because the [GameKit GameCenter API callbacks][gamekit callback], which are normally triggered when it is the player's turn in an online match, are not being activated on old matches. However, for new matches and subsequent turns the callbacks are getting triggered. I can't explain why this stopped happening for the old matches except to blame it on the Game Center servers, and that is out of my hands. Perhaps this happens when matches get 'stale.'
##### Saving Bonus Turns<a name="saving-bonus-turns">
I am working on saving the online match after every bonus turn so that the player cannot cheat and redo their turn if they get a bonus. The fix I applied on Monday resulted in a bug where the "playerTurnText" did not reflect the current player when the opponent checks the match but it is not their turn. It also introduced a bug that caused it to be the next players turn when a player got a bonus turn, effectively giving that bonus turn to the opponent. That's not good.

This problem can be fixed but it is going to introduce a special case that changes an existing feature I worked hard on: Replay Mode. When opening an online match, after the first turn the opponent gets to see the last move or chain of moves made by the other player. Instead of recording the screen and sending a movie, I am recording the set of moves and sending a copy of the board before the last player took his turn, then the ReplayScene just executes those moves on the copied board when presenting the replay.

Now that I am saving the game between bonus turns, if the player gets a bonus turn but decides not to finish their full turn and exits the match, all match data is sent to the opponent. If the opponent happens to check on the status of the match at that point despite that it has not become their turn, they will see that last move up to the point it was saved. But when the original player finally returns to take their bonus turn, the data will be overwritten from that point on.

The result is that the opponent will get another update with a replay that only shows what happened since the original player picked back up from their last bonus turn. So unless players always take their bonus turns in one session, the set of moves for the replay may not show every turn that the last player took. Players are not notified until it has become their turn, so in this special case the replay they see would just show the last set of moves taken in the opponent's last session.

The old functionality of Replay Mode showed every move taken if a player chained multiple bonus turns because the match data was not saved and sent until the player's turn was finally over. Implementing replay with bonus turns that are taken on subsequent sessions instead of within one session would require much more work and I would need to find a way to save the list of old moves separately. So for the sake of time I'm leaving this as is.

#### Wednesday:
- researched how to use [bitmasks][c++ bitmasks] to select multiple objects

  This will make it easier to fade all the buttons in the SettingsScene when performing an animation that shows the "How To Play" instructions in a slide show. In [C/C++, you need to be creative][store bitmask in char]. Luckily, there is a [simple solution for Swift.][bitmasks swift]

- found a bug where replay mode in online game shows last move of P1 and P2.

  After analysis, I believe that my code was reverted back by Git, accidentally. That's right, I'm blaming Git.

- completed update for saving bonus turns in online matches

##### other events
- had first martial arts class since Covid19 began. Gyms in Texas have opened this week.

#### Thursday:
- finished a new animation for presenting the SettingsScene when the player unlocks <a href="{%- post_url 2020-03-13-pandemic-declared -%}#unlock-game-feature">new game modes</a>
- added new colors to the background animations

#### Friday:
- completed new additions to the set of background animation options

- researched how to include a hyperlink in NSMutableAttributed String

  I wanted to place a link in a SKLabelNode in my SettingsScene to link to my [PayPal.me page for donations to my app,]({{ site.paypal }}) but this only seems to work on UITextViews which aren't exposed by SKLableNodes. I will use an UIAlert instead.

#### Saturday:
- checked on my Bitcoin wallets, researched hardware wallets since those are the most secure

##### other events
- Celebrated Memorial Day early by grilling porkchops, steak and venison sausage with my parents.
- Cooked s'mores over a dying fire in the barbecue pit.

#### Sunday:
- composed a [timeline of production events]({%- post_url 2020-05-24-Mancala-behind-the-scenes-screenshots -%}) in the development of my Mancala app using screenshots I have taken while debugging, emailed it to my friend
- made some videos of the Mancala app gameplay for the App Previews to be used in the App Store
  + used this [built-in method on macOS Catalina for recording the screen][macos screen rec] to capture the iOS simulator running my app

[gamekit callback]: https://developer.apple.com/documentation/gamekit/gkturnbasedeventlistener/1521017-player
[bitmasks swift]: https://cocoacasts.com/how-to-work-with-bitmasks-in-swift/
[c++ bitmasks]: https://stackoverflow.com/questions/18591924/how-to-use-bitmask/18592049#18592049
[store bitmask in char]: https://stackoverflow.com/questions/3289065/how-to-store-8-bits-in-char-using-c
[macos screen rec]: https://www.imore.com/screenshot-mac
