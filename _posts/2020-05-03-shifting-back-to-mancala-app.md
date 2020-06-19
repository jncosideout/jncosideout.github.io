---
tags: [Secure Chat Server 2, mancala, Ubuntu, Congressional Dish, .NET]
date: 2020-05-03
---
### My Week in Review
#### Monday:
- improved the AI in Mancala app
- Ubuntu LivePatch error, fixed after manual updates

#### Tuesday:
- wrote more documentation for Mancala
- listened to [Congressional Dish episode 213 "CARES Act"](https://congressionaldish.com/cd213-cares-act-the-trillions-for-covid-19-law/)

#### Wednesday:
- got TestFlight feedback saying "the moving colors could make someone sick"
- made the Chat Server C# prototype work after changing my Message class to a struct, now uses ["Nullables" which are just like "Optionals" in Swift](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/nullable-value-types)
- setup Git for Secure Chat Server 2, learned how to use .gitignore (hint: files that already have been added to Git will not be ignored)
- Thunderbird updated to support Enigmail (or vice-versa, not sure)

#### Thursday:
- more documentation in Mancala
- got my Chat Server prototype to relay messages to multiple clients
- began research on [SSL for C# / .NET](https://docs.microsoft.com/en-us/dotnet/framework/network-programming/certificate-selection-and-validation)
  - [What is the difference between X509Certificate2 and X509Certificate in .NET?](https://stackoverflow.com/questions/1182612/what-is-the-difference-between-x509certificate2-and-x509certificate-in-net)

#### Friday:
- Governor Abbot opens Texas retail businesses after Covid19 lockdown
- finished all Mancala documentation
  - uploaded Build_1.2.4 to TestFlight
- helped Mom bathe three cats!

#### Saturday:
- responded to TestFlight feedback from a graphic designer who tested Mancala and had UI critiques
- started learning about [Instruments](https://www.raywenderlich.com/397-instruments-tutorial-with-swift-getting-started) and [Time Profiler](https://developer.apple.com/videos/play/wwdc2016/418/)

#### Sunday:
- used Time Profiler on Mancala while playing against my youngest sister [to stress test the app](https://www.hackingwithswift.com/articles/81/how-to-find-and-fix-slow-code-using-instruments)
  - found abnormally high, sustained CPU usage at the end of the game when I was expecting very little
