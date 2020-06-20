---
title: "Progress Update: Secure Chat Server 2"
tags: [Secure Chat Server 2, GnuPG]
date: 2020-04-19
---
### My Week in Review
#### Monday:
- Picked back up on server prototype for my new project: Secure Chat Server 2
- gave out public links for TestFlight to friends and family
- promoted my TestFlight beta on Reddit

#### Tuesday:
- got the server prototype to run on multiple threads (one per client plus main for socket listening)
- need to network with iOS developers in Houston area, find someone who knows how to leverage TestFlight experience

#### Wednesday:
- got the client prototype of Secure Chat Server 2 to use multi-threading
- set up GnuPG key exchange with my first certificate I made on my Windows machine
  - [I used my macarrao_1 key to sign my armahdeggan key]({{ site.GnuPG_key_armahd }}), creating a circle of trust between me and myself
- finished setting up Proton Mail
- created a revocation certificate for my Windows-based certificate

#### Thursday:
- called my sister to wish her a happy birthday
- multi-threaded chat server prototype is blocking when reading input from client

#### Friday:
- finished more documentation of source code in Mancala apps
- celebrated my Mom's birthday, assembled the new Wet Vac we got her for her birthday
- played Splendor with my family [(a great board game you should try)](https://boardgamegeek.com/boardgame/148228/splendor/ratings)
- talked to my youngest sister on FaceTime

#### Saturday:
- researched how [DataContractSerializer]({%- post_url 2020-04-09-Data-Contract-vs-Serializable -%}) works with sockets and [NetworkStream](https://docs.microsoft.com/en-us/dotnet/api/system.net.sockets.networkstream?view=netframework-4.8#properties), and how to determine [length of incoming data to be read](https://stackoverflow.com/questions/7542059/most-efficient-way-of-reading-data-from-a-stream)

#### Sunday:
- did more documentation of Mancala app
- researched Network Streams and [serialization in .NET](https://stackoverflow.com/questions/4545439/difference-between-datacontract-attribute-and-serializable-attribute-in-net)
