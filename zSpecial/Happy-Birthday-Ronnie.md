---
layout: page
title: Happy Birthday, Ronnie!
tag: birthday
permalink: /happy-birthday-ronnie-2020.html
---
This is your private page on my website. You are free to do whatever you want here.

You don't even need to log in, isn't that cool?

<a href="https://youtu.be/NWWOAC2Ua6s" class="button">Watch cat videos</a>

<a href="https://www.chesspuzzles.com/mate-in-one" class="button">Don't watch cat videos</a>

<br>
  Your Age:<input type="text" class="age-form" id="your-age"><br><br>
  <button type="button" onclick="myFunction()">submit</button>

<h3 id="output"> </h3>

<script>
  function myFunction() {
    var age = document.getElementById("your-age").value;
    document.getElementById("output").innerHTML = age + "?, wow, you're a big boy! \u{1F382} \u{1F973}" ;
  }
</script>
