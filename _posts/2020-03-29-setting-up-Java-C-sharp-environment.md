---
tags: [Ubuntu, Java, MySQL, Secure Chat Server 2, Covid19]
---

{%- assign github_SecChatServer1 = site.data.github["Secure Chat Server 1"] -%}
{%- assign secChat1 = github_SecChatServer1.url -%}

On Thursday, March 26, after avoiding ["Dependency Hell"]({%- post_url 2020-03-26-switching-gears -%}), I moved on to my first task in setting up the development environment for my next project: {{ page.tags[3] }}, based off of [my previous project]({{ site.github_url | append: secChat1 }}). I am going to convert that project from Java to C#.

The first step was installing Eclipse Mars. I want it to be Mars because this is the first time I have cloned a project from one operating system to another, so I want everything to be as close to my original environment as possible. The original Secure Chat Server 1 was built on JDK 8_181 which worked fine on Mars Eclipse. I don't want to upgrade in case that would break my code. By Friday I got both of these parts installed, Eclipse Mars and JDK 8 on Ubuntu 18.04.

The next step was to install MySQL. Again, I want to keep everything as close to my first environment as possible, so I'm going to install ver. 5.6 even though it's outdated. By Saturday I got that installed. Because I was trying to [follow the instructions on the official docs][guide I followed], I tried to figure out how to start MySQL from boot-up using systemd. I have heard people complain about systemd but I am new to Ubuntu so to me it's just another challenge.

I called it a day after testing some queries then rode my bike to the park. I saw yellow caution tape wrapped around all the playgrounds, benches and gazebos, but people were still acting pretty normal otherwise, except for the kids who weren't allowed in the skatepark. Strange times.

Next week I will look into fixing a bug that caused the Mancala app to crash, reported by one of my testers in TestFlight. Supposedly, I can download a crashlog and it will contain a stack trace from the point of the crash.

[guide I followed]:https://dev.mysql.com/doc/mysql-secure-deployment-guide/5.7/en/secure-deployment-post-install.html#secure-deployment-systemd-startup "MySQL official docs"
