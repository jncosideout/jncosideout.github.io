---
title: Data Contract vs Serializable
date: 2020-04-09 #14:29:58 -0500
tags: [C#, Java, .NET]
---
I've finally started writing the code to get my new project underway. I am learning C# as I go, but finding that it is nearly equivalent to Java. I have completed the basic networking client/server model that I used in my earlier project, [Secure Chat Server 1][secChat1], which uses a two-threads system on the client side and a multiple thread (1 + each thread-per-client) system on the server side. This sets up a chat room-style instant messaging model that echoes a message from a client to all other clients via that client's corresponding server thread.

In order to send more data than just a text string, I need a way to serialize objects to be sent through my socket streams. In Java, I simply relied on the ObjectOutput stream, a class that implemented Java's Serializable interface. Little did I know how much it abstracted to make my life easier.

C# has no equivalent to Serializable. The next best thing I have found is something called the Data Contract. It's not a class or interface, but rather an Attribute, and when you tag your properties with it, you are stating that these properties must be honored in serializing and deserializing your objects.

### Here are some of the Microsoft docs I found most useful

- Serialization Guidelines

  [How to choose which type of serialization to use] (https://docs.microsoft.com/en-us/dotnet/standard/serialization/serialization-guidelines)

- [How To Create a Basic Data Contract] (https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure)

- [Using Data Contracts] (https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/using-data-contracts)

- [DataContractAttribute Class] (https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.datacontractattribute?view=netframework-4.8)

- [DataContractSerializer Class] (https://docs.microsoft.com/en-us/dotnet/api/system.runtime.serialization.datacontractserializer?view=netframework-4.8)


Most efficient way of reading data from a stream

[secChat1]: {{ site.github_url | append: site.data.github["Secure Chat Server 1"].url }}
