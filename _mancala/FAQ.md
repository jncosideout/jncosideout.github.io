---
purpose: Support
description: Frequently asked questions
title: FAQ
---
{%- assign notifications_pics = site.static_files | where:"family", "notifications" -%}

1. **Q:** I started an Online Game but my opponent hasn't responded, when will they take their turn?

    **A:** If you tapped "Play Now" then two possible events can occur:

    1. You join someone's match.

    2. You start a match.

    If you tapped "Play Now" and the board is fresh (it looks untouched) and you do not see a "Replay" animation immediately, that signifies there were no open matches to join, so Game Center created a new match for you and you are Player One. After you take your turn, you won't get a reply-move automatically, because you can only play against real, human players.

   Therefore, you are waiting for someone elsewhere in the world to play Mancala Fantasy - Online and tap "Play Now." As soon as someone does that, Game Center will connect them to the oldest open match it has, and if that is yours (it should be) then that person will become your new opponent.  After they take their turn, if you have [notifications enabled](troubleshooting.html#activating-notifications), you will be alerted and you can drag-down on the notification to take your turn!

1. **Q:** How do I log out of my Game Center account?

   **A:** You need to do this from your iPhone's main Settings app

   1. **From settings, select Game center (scroll down to see it)**
   ![Apple's main Settings app][settings top]

   2. __Scroll to the bottom and tap *Sign Out*__
   ![controls for all Game Center options][game center options]

   For more help with Game Center see [Using Game Center](using-Game-Center.html)

{% assign pic_paths = notifications_pics | map: "path" %}
{%- assign gameCenter_all_options = pic_paths[0] -%}
<!-- {%- assign mancala_all_options_pic = pic_paths[1] -%}
{%- assign settings_mancala_pic = pic_paths[2] -%}
{%- assign settings_scroll_down_pic = pic_paths[3] -%} -->
{%- assign settings_top_pic = pic_paths[4] -%}

[Game Center Options]: {{ gameCenter_all_options | relative_url }} "From Settings tap Game Center to sign into your Game Center account"
<!-- [Mancala Notifications]: {{ mancala_all_options_pic | relative_url }} "Then tap Notifications to see all options"
[Settings Mancala]: {{ settings_mancala_pic | relative_url }} "Tap Mancala Fantasy Online"
[Settings Scroll down]: {{ settings_scroll_down_pic | relative_url }} "Scroll down to see your apps" -->
[Settings Top]: {{ settings_top_pic | relative_url }} "scroll down to see Game Center"
