---
title: Mancala Behind the Scenes - Debugging Screenshots
date: 2020-05-24 15:29:58
tags: [mancala, xcode tools]
---
{%- assign debug_screenshots_photos = site.static_files | where: "family", "debug_screenshots" -%}
{%- assign dump_string = debug_screenshots_photos | map: "name" | join: " " -%}

<script type="text/javascript">
  console.log("Dumping debug_screenshots_names");
  console.log( "{{ dump_string }}" );
</script>

{%- assign pic_paths = debug_screenshots_photos | map: "path" -%}
I am wrapping up my project now. I just have to take some screenshots and submit it to the App Store. For nostalgia’s sake I have been looking back at the screenshots I took while debugging.

Here is the first prototype from over a year ago. To get the animations to work was a real chore, but I figured out how to time them in the future and sync them up seamlessly using multi-threading.
![prototype 1]({{ pic_paths[0] | relative_url }})

When I got the game to be multiplayer online, I switched to a framework called Sprite Kit that is used specifically for games that makes animation much easier, like storyboarding a movie. But it meant that the board and layout of images had to be done all in code, versus in the drag-and-drop Interface Builder, a tool provided by Xcode. So I had to create it by trial and error. What you see below is a major step in that progress, but it is obviously wrong:
![layout of board with Sprite Kit for the first time]({{ pic_paths[1] | relative_url }})

Saving the data was crucial, especially for Online play. The first method I used was the one that I was taught in college when I took an iPhone development class. It led to runtime errors like the one you see below because I was trying to archive data structures that I made which were generic and the system didn’t know how to describe them when writing the data to disk. Eventually I got it to work, but I ended up going in a different direction and choosing to save less data.
!["Attempting to unarchive generic Swift class"]({{ pic_paths[2] | relative_url }})

It didn't help that I was trying to save a data structure I made to represent the entire game board, and that this data structure was made up of other structures I made that were designed to be generic, not specific to my application, so that they could be reusable.

These structures also allowed for instances to be linked to each other, which caused another complication. Those links / references cannot be saved when they refer back to each other. This creates a "chicken-or-the-egg” dilemma.

The Mancala game board is based on my CircularLinkedList class, meaning each node links forward to the next node, and the last node links to the first. So you can see why it causes a dilemma. The advantage of the CircularLinkedList is that it makes updating the pits on the board very simple, since Mancala is played circularly!
- - -
Because I have to add images in code, I have to use trial and error to get the size and placement correct for each button, which can lead to amusing results:
![Really big 'Settings' gear!]({{ pic_paths[3] | relative_url }})

The last major bug I had to squash was a memory leak problem. I don’t use this tool often enough, but the View Hierarchy Debugger shows the effect of this problem, that multiple scenes were being created and not destroyed which is what a memory leak is, in effect:
![Memory leak of MenuScene in View Hierarchy]({{ pic_paths[5] | relative_url }})

Here are a few more shots of the View Hierarchy Debugger in action. This one shows the app from the normal, head-on view that the user will see.
![Normal view of game board]({{ pic_paths[8] | relative_url }})

The View Hierarchy Debugger lets the developer rotate and "blow up" the views in three-dimensions, to give them a new perspective on the layout. I have yet to figure out why the pits and board node connecting-lines are on different levels, when I was expecting all the pits to be an equal height and lines to be on a separate level below the pits. Well, it's not affecting gameplay so… : )
![game board angled downward]({{ pic_paths[6] | relative_url }})
![game board angled leftward]({{ pic_paths[7] | relative_url }})

Another great tool that I recently learned to use is the Memory Graph, which is also built into Xcode. It helped me spot the objects that were causing the memory leaks, and which objects still had references to them that kept them from being deallocated:
![Memory Graph shows relationships between objects]({{ pic_paths[4] | relative_url }})
![The arrows point from an object parent to its child]({{ pic_paths[9] | relative_url }})

These screenshots only make up a fraction of the challenges I have overcome while developing this app. If you count the month of December 2018 when I made the prototype for this app as a [Windows Win32 API desktop program with a GUI](https://www.youtube.com/playlist?list=PLte_Zz-p0FPB45TBQy_yNd_ce7_C17pR5), this project is 1.5 years old. And the gameplay algorithms are based on my original design from my first full-fledged C++ command-line program I wrote in 2014, which took a month or so. I had the idea for a GUI based version ever since then!
