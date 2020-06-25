---
tags: [Secure Chat Server 2, mancala, xcode tools]
date: 2020-05-17
---
## - Mancala Progress Update -
#### Monday:
Last week my friend who is [a Polish electronic musician](https://soundcloud.com/nasoshnik) told me he wants me to safeguard a backup of his entire discography in case something happens to him or his computer. I met him a few years ago on SoundCloud and I love his music because it is unlike any kind of electronic music I have heard, and I consider myself a connoisseur of electronica/edm/techno/electro. He told me he would rather have someone who cares about his work to be a custodian and curator of it, unlike his friends and family.

So after he transferred it to me I have made a couple of copies of his archives, which took up several gigs of memory, but it is all worth it. He gave me permission to release it as long as I give him credit and include all appropriate information. I will probably do so in stages over a long period of time on [my SoundCloud account.](https://soundcloud.com/sour_cream_pringles)

##### other accomplishments on Monday
- encrypted my passwords using my new X509Certificate
- researched using certificates in conjunction with C# and SSL sockets

#### Tuesday:
- refreshed my knowledge of [OpenSSL with keytool]({%- post_url 2020-04-07-Using-Java-keytool -%}), created demo CA certificate, server certificate and test certificates for 'Client A' and 'Client B' entities

#### Wednesday:
- finished <a href="{%- post_url 2020-05-10-plugging-the-leaks -%}#scene-transition-overhaul">Mancala scene transition overhaul</a>

#### Thursday:
- updated documentation of Mancala to reflect new backend design changes
- read a few chapters of The Walking Dead

#### Friday:
- performed regression tests on Mancala to make sure all memory leaks are closed
- tried to eliminate memory leak when creating a new local game
- attended Zoom meeting for martial arts class, discussed ['System 1 & 2' logical thinking from "Thinking Fast and Slow"](https://en.wikipedia.org/wiki/Thinking,_Fast_and_Slow)

#### Saturday:
Talked to my friend on Zoom. He showed me how his cat Guillermo will catch a moth on command. His work as a grocer at a Whole Foods has him worried about being exposed to the Covid19 virus.

##### other accomplishments on Saturday
- completed investigation using Allocations Instrument to find memory leaks which occur when creating a new local game
<a name="AI-interruption"></a>
- discovered bug when switching from "VS Computer" to "Online Game" mode via a "Your Turn" notification which **interrupts the AI processing on a background thread**
  + Resolved with "mutex-like" flags set by viewWillLeave()

#### Sunday:
Conducted more stress tests on the scenario of 'switching from AI_GameScene to VS_Online_GameScene via notification.' Previously it crashed once after my last fix but I did not have the debugger running at that time. Have not caught it since though. This problem is caused by the transition happening during a very small time frame so it is very rare and difficult to test manually.

##### other accomplishments on Sunday
[Tested Jitsi with my martial arts instructor]({%- post_url 2020-04-08-Jitsi-vs-Zoom -%}). Quality was poor but may have been degraded by the fact that I was joining the meeting w/ my Windows 10 Lenovo Ideapad and Macbook Air simultaneously, causing congestion on my local network.
