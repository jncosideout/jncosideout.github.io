---
tags: [Java, Networking, Secure Chat Server 1, .NET, Ubuntu, PluralSight]
---
{%- assign github_proj = site.data.github["Secure Chat Server 1"] -%}

I have been setting up a Java development environment so I can rewrite one of my Java projects, which I call ["Secure Chat Server 1"][secChat1], as a .NET application in C#. Firstly, I installed Mars Eclipse on Ubuntu 18.04. However, I could not load my jar dependencies including JDBC/Connector J from my original project because the GTK GUI in Eclipse Mars on Ubuntu 18.04 has a bug that prevents you from opening the Build Path dialog box. I looked around but there seems to be no other way to add dependencies to an Eclipse project, not even through command line. The solution was to simply upgrade to Eclipse Oxygen. So much for [keeping things the same]({%- post_url 2020-03-29-setting-up-Java-C-sharp-environment -%}).

### PluralSight

On Friday I signed up for a free trial on [PluralSight.com](https://PluralSight.com) that lasts for the month of April. The first course I chose was Intro to Networking. PluralSight gives you an "IQ" test for each area of study to fit you into the best course level based on your existing knowledge of the subject. I like that, because even though I am an amateur Network Security enthusiast, I really needed to bone up on the fundamentals, and the "IQ test" showed me just how much I had to learn.

#### Private Communications

Later on Friday I created my first [Proton Mail](https://protonmail.com) account, which I recommend to anyone who wants email security but does not want to fuss around with managing RSA Certificates. I like messing with certificates, however, so later that day I also [created a GnuPG key]({{ site.GnuPG_key }}) and attached it to my Proton Mail account. Finally, I refreshed my memory of my [Senior Thesis paper]({{ site.senior_thesis }}) to review the design I implemented for my "Secure Chat Server 1" project.

##### The rest of my week

Saturday, April 4th, I continued my PluralSight Intro to Networking course. I will take the C# course next. I also set up Thunderbird with Enigmail to use my new GnuPG key. Later I wrote some more documentation for my Mancala source code and read more of my Senior Thesis.

Today, April 5th, I studied TCP/UDP and C# on PluralSight. I also installed .NET Core 3, MonoDevelop and VS Code so I can start working on my "Secure Chat Server 2" project.


[secChat1]: {{ site.github_url | append: github_proj.url }} "My senior thesis project"
