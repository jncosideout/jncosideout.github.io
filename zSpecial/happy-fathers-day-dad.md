---
layout: page
title: Happy Father's Day 2020, Dad!
---
This is your private page on my website. You are free to do whatever you want here.

You don't even need to log in, isn't that cool?

<a href="https://youtu.be/NWWOAC2Ua6s" class="button">Watch cat videos</a>

<a href="https://www.365chess.com/puzzles_solving_guest.php" class="button">Don't watch cat videos</a>

<br>
  Your Message:<input type="text" class="my-form" id="your-msg"><br><br>
  <button type="button" onclick="myFunction()">submit</button>

<h3 id="output"> </h3>

<script>
  function myFunction() {
    var msg = document.getElementById("your-msg").value;
    document.getElementById("output").innerHTML = msg + "?, wow, that's incredible! \u{1F632} \u{1F4A3}" ;
  }
</script>
