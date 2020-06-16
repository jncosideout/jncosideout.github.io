---
tags: [Secure Chat Server 1, Ubuntu]
---
<script type="text/javascript">
  console.log("Dumping page.tags[0]");
  console.log( "{{ page.tags[0] }}" );
</script>
{%- assign secChat1 = page.tags[0] -%}
{%- assign github_SecChatServer1 = site.data.github[secChat1] -%}
<!-- site.data.github.docs | json | join: " - " -->
{%- assign debugExp = github_SecChatServer1.url -%}
{%- include jsLog_MD.html toDump='github-yaml' dumpExpression= debugExp -%}

On Monday, March 23, I submitted my second build to TestFlight. Its number is 1.2.3 because I didn't know how builds
are numbered at the time. There are conventions out there, but I think they are used arbitrarily anyway. So all my TestFlight builds will be 1.2.X

Now that I have a stable build on TestFlight that I'm happy with, I'll wait for tester feedback to come in while I switch gears to my next project. It will be a remake of the project for my [senior thesis]({{ site.senior_thesis }}) of my undergrad. I built an [instant message client and server in Java, designed to be fully encrypted and as secure as possible.]({{ site.github_url | append: github_SecChatServer1.url }})

I decided to use my desktop Ubuntu workstation for this project. Almost exactly one year ago, I installed Bionic Beaver onto my HP p7-1414. I haven't touched it since then as I have been focusing on my Mancala app. The first thing I tried to do on this Ubuntu machine last year was to build and install GnuPG. I quickly remembered why I really abandoned Ubuntu: installing this software by installing its dependencies one-by-one drove me insane.

So by Thursday I reached out to my friends online for help, and from them I learned that practically no one installs software  that way anymore, because digging through the endless chain of dependencies puts you into "Dependency Hell." One person advised me to get a package manager like Synaptic, which has come in handy. But for my purposes, my friend told me to check that GnuPG isn't pre-installed on Bionic Beaver before I waste more of my time. Lo and behold, it was.
