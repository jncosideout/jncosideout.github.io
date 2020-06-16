---
purpose: How To
description: Tips and tricks for Game Center
title: Using Game Center
---
{%- assign game_center_pics = site.static_files | where:"family", "GameCenter" -%}
{%- assign debugString = game_center_pics | map: "name" | join: " " -%}


  _Mancala Fantasy - Online_ relies on Apple's Game Center to offer matchmaking services. On the Main Menu, tap "Online Game" to see a list of your Active Games...
  ![Active Games in Game Center][active games]
  **...then scroll down to see your Completed Games:**
  ![scroll down to see Completed Games in Game Center][completed games]
  If the Game Center server fails to connect you to your match or send match data to the next player, you may see a pop-up alert for these errors. Sometimes the alerts are shown when an error did not occur, so make sure you double check your match to see the status.

  For example, if you finish your turn and a pop-up alert with the title "Server Error" appears, try quitting the match and going back to the list of matches. Select the match you just played by tapping on the "i" button on the right, which brings you to the Detail screen shown below:
  ![Detail view of a match][details-1]
  **...then scroll down to see the current match status for each player.**
  ![scroll down to see the status of the players in this match][details-2]
  If nothing has changed in the match then there was a true server error and you must replay your turn. If the match status has been changed and looks correct, it was a false alarm.
#### Removing matches
  In the list of matches provided by Game Center, you can swipe to remove the matches. However this may cause the app to freeze and become unresponsive, so I recommend removing or quitting the matches by going to the detail view and selecting "Forfeit/Remove" (the label will be different depending on the state of the match, i.e. 'Active' or 'Completed').

  Access the Detail view of the match you want to remove by tapping on the "i" as described above.
  ![Do not swipe to remove][swipe remove]
  Unfortunately, I have not been able to resolve this bug because it comes from Game Center's Match Maker View Controller, (the screen you see in these screenshots). Since I am simply leveraging the Game Center API, I have no access to its code and my implementation of it is completely uncoupled with it.
  ![Correct method to remove a match][Details-3 Remove]

{% assign pic_paths = game_center_pics | map: "path" %}
{%- assign active_games_pic = pic_paths[0] -%}
{%- assign completed_games_pic = pic_paths[1] -%}
{%- assign details1_pic = pic_paths[2] -%}
{%- assign details2_pic = pic_paths[3] -%}
{%- assign details3_remove = pic_paths[4] -%}
{%- assign swipe-remove = pic_paths[5] -%}
[Active Games]: {{ active_games_pic | relative_url }} "Active Games in Game Center"
[Completed Games]: {{ completed_games_pic | relative_url }} "Completed Games in Game Center"
[Details-1]: {{ details1_pic | relative_url }} "Detail view of a match (top)"
[Details-2]: {{ details2_pic | relative_url }} "Detail view of a match (bottom)"
[Swipe Remove]: {{ swipe-remove | relative_url }} "This can cause the app to freeze"
[Details-3 Remove]: {{ details3_remove | relative_url }} "Correct way to remove/forfeit a match"
