---
purpose: Support
description: Steps for troubleshooting common problems in the app
title: Troubleshooting
---
{%- assign notifications_pics = site.static_files | where:"family", "notifications" -%}
{%- assign debugString = notifications_pics | map: "name" | join: " " -%}


### 1. Tips For Resolving Connection Errors
As soon as you open the app, you will be automatically signed into your Game Center account for _Mancala Fantasy - Online._ If you haven't signed into Game Center yet, you will be presented with the Game Center official log-in screen. If neither of those things happen and the "Online Game" button is still greyed-out, it means the app cannot connect to the Game Center server. Check your WiFi or cellular network connection and you will automatically be logged in once your connection is restored.

If your connection is working and _Mancala Fantasy - Online_ still will not log into your Game Center account, close the app, wait a while and try again. If all else fails, try <a href="FAQ.html#log_out_Game_Center">logging out of Game Center directly</a> then log back in.

### 2. Change the Background
  By default, the Background Animations feature is turned off. However, if you would like to try out one of the nine styles of Background Animations available then go to the Settings screen by clicking the gear icon in the top-right corner of the Main Menu.

  You will see a button in the bottom-left corner labeled "Background Animations". If it is greyed-out, animations are off. When you tap the button, it will change to "Background Animation 1". The next game you play will have the style for "Background Animation 1". From now on, all games will use this animation style until you change it.

  Go back to the settings and tap the button again to try out the other styles (2 - 9). To turn off animations completely, keep tapping the button until you get to "Background Animation 9," then tap one more time to reset to the greyed-out state where it began.

### 3. Other Settings
  * External Settings:
  As mentioned below in **4.** ***Activating App Notifications***, you can go straight to the iPhone's external settings app by tapping the button on the right side of the Settings menu in Mancala Fantasy - Online. It is labeled "Exteral Settings" and it will prompt you to open the iPhone settings app.

  * First time Walkthrough:
  On the left side, you will see the "First time Walkthrough" button. When tapped, it will bring up a dialog telling you that "You will be taken back to the Main Menu to see the first-time walkthrough."

    Hit Ok to go back to the Main Menu, where you will be presented with an introduction to the _Mancala Fantasy - Online_ app and an explanation on how to use it.

    Then choose "2 Player" or "Versus Computer" to continue the walkthrough. On the next menu screen, you will be presented with another explanation about the 'save game' feature works.
    ***If you don't complete the walkthrough it will repeat every time you visit the Main Menu until you choose "2 Player" or "Versus Computer" to finish it.***

    Afterward, you won't see the walkthrough again until you go back to the Settings menu and tap the "First time Walkthrough" button again.

  * How to Play:
    This button activates a slide show that explains Mancala's background and the rules of the game.

  * Credits:
    This button presents a slide show of credits for code sources, art and images, or any other resources I borrowed under Creative Commons licenses to build this app.

  * Value for Value:
    This button, in the bottom-center of the screen, brings up a dialog which gives you the option to [voluntarily compensate me for my work on this app]({%- link _mancala/Value_For_Value.md -%}), by opening your phone's browser and taking you to my PayPal.me page.


<h3 id="activating-notifications">4. Activating App Notifications</h3>
You can activate notifications for Mancala Fantasy - Online at any time through your iPhone's external settings (the main settings app for the phone itself).

  * Go to the iPhone Settings apps

    ![settings top][settings top]

    **...scroll down to *Mancala Fantasy - Online***

    ![settings scroll down][settings scroll down]

There are two types of notifications sent by the app: *Game Center **push** notifications* and *Mancala Fantasy - Online **local** notifications*. They both contain updates about matches you are currently playing, but they work in different ways.

1. **Game Center push notifications**

    The Game Center push notifications only occur when you are not using the _Mancala Fantasy - Online_ app.

    _iPhone 8 and below_

    To turn them off or on:
    1. Go to the iPhone external settings
    2. Choose *Notifications* > *Games*
    3. Check "Allow Notifications"
    4. If you want to customize the Alert Style, or other options of the notifications, you can do so here.

2. **Mancala Fantasy - Online local notifications**

    The local notifications only come when _Mancala Fantasy - Online_ is open.

    To turn them off or on, you have three options:

    **Option 1**
    _iPhone 8 and below_

    1. Go to the iPhone external settings
    2. Choose ***Notifications* > *Mancala Fantasy - Online***
    3. Check "Allow Notifications"
    4. If you want to customize the Alert Style, or other options of the notifications, you can do so here.

    ![Fine tune notifications for Mancala Fantasy - Online][Mancala Notifications]

    **Option 2**
    1. Go to the iPhone external settings

    2. Scroll down to ***Mancala Fantasy - Online***
    3. Below "Siri & Search" choose *Notifications*
    4. Follow steps 3 and 4 from above.

    ![After tapping Mancala Fantasy - Online in Settings app][Settings Mancala]

    **Option 3**
    1. Open _Mancala Fantasy - Online_ and tap the "Settings" gear in the top-right corner.
    2. Tap the button on the right labeled "External Settings"
    3. An Alert will pop up. Select "Settings" to go straight to the iPhone's main settings app
    4. Follow steps 3 and 4 from **Option 2** above.

{% assign pic_paths = notifications_pics | map: "path" %}
{%- assign gameCenter_all_options = pic_paths[0] -%}
{%- assign mancala_all_options_pic = pic_paths[1] -%}
{%- assign settings_mancala_pic = pic_paths[2] -%}
{%- assign settings_scroll_down_pic = pic_paths[3] -%}
{%- assign settings_top_pic = pic_paths[4] -%}

[Game Center Options]: {{ gameCenter_all_options | relative_url }} "From Settings tap Game Center to sign into your Game Center account"
[Mancala Notifications]: {{ mancala_all_options_pic | relative_url }} "Then tap Notifications to see all options"
[Settings Mancala]: {{ settings_mancala_pic | relative_url }} "Tap Mancala Fantasy Online"
[Settings Scroll down]: {{ settings_scroll_down_pic | relative_url }} "Scroll down to see your apps"
[Settings Top]: {{ settings_top_pic | relative_url }} "Apple Settings App main menu"
