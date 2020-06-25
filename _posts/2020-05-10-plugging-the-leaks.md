---
tags: [mancala, iOS, Swift, xcode tools]
date: 2020-05-10
---
## Mancala Progress Update
#### Monday:
- added error handling to the main function that loads online games
  - tested error handling by trying to play Mancala online in a location with weak signal
- my local notifications are inconsistent, even with strong network signal
- used Memory Allocations to find memory leaks when loading online games

#### Tuesday:
Because many TestFlight testers have reported random crashes when changing between game modes or menu screens, I had thought this was a bug in my code. After using the Allocations Instrument, I have found that my app has memory leaks at every "scene change," which is the event of moving between screens in the app. This has a deeper cause than a simple bug.

The most likely cause is my SKScene objects are being captured in [closures][closures] that belong to the buttons that trigger a scene change. [These closures][escaping closure explanation 1] are [escaping][escaping closure explanation 2] and therefore hold references to the old scene when changing to a new scene. After enough scene changes, there are too many scene objects in memory that should be getting deallocated but are remaining, causing the app to crash at seemingly random points.

So I spent time relearning ARC and escaping closures. I found a special case that applied to my app regarding these two subjects and so I asked about it on Stack Overflow. [Closures can be confusing][closure within closure], and in Swift 3 and beyond, all [non-parameter closures are escaping by default][closures are escaping by default]. However, in my case I was _expecting_ the parameter closures of my buttons and other functions to be non-escaping as is normally the case, but it was not. The reason why my parameter closures broke this rule is that they were declared as optional. [I asked about this on Stack Overflow][my closure question] to find out why and was [redirected to this question.][my question duplicated this] The answer given there did not address the 'why,' but one of the comments there pointed to [this excellent article that gets to the bottom of the cause][good answer to my question].

#### Wednesday:
- Changed the navigation flow between my scenes to address the UX critiques I received from one of my TestFlight testers.
- Resolved most of the closure captures that caused memory leaks, except for the main MenuScene
- studied the difference between "weak" and "unowned" references

#### Thursday:
I tried to make a .gitignore for my branch on Build 1.2.3 to avoid committing the breakpoints.bkplist, but this resulted in an unstable state. I will just live with committing the bkplist.

My first attempt at rectifying the memory leaks problem was to continue breaking strong reference cycles in my buttons' escaping closures by using "weak" references, but I cannot eliminate them completely. I also tried to pass the main MenuScene to the other scenes so that I could always return to that instance when the user wanted to go back to the main menu. This didn't work completely. It allowed the MenuScene to have only one instance created, but each SKScenes following a transition from that MenuScene was getting captured.
<a name="scene-transition-overhaul">
So I created new branch for Build 1.2.5 to patch the memory leaks. I will be redesigning the entire scene-changing flow in my app to use Notification Center to handle presenting scenes in my GameView Controller. This will create a central dispatch to receive notifications from the active scene when the user taps a button that moves to another scene. The Game View Controller will receive the notification and display the scene that the user wants to see, and since closures aren't involved anymore, there will be no more reference cycles.

#### Friday:
Completed most of the work on patch_1.2.5, all SKScenes will now be presented from the GameView Controller. Either just one instance of each scene type will exist in memory, or the scene will be destroyed when transitioning, whichever way I choose for the situation.

I also talked to my sister on the phone. She had texted me to remind me that fifteen years ago on May 8th, which was Mother's Day that year, I had asked her to remind me of the conversation we had that day. Well lo and behold, her amazing long-term memory pulled through.

#### Saturday:
- fixed a bug in Mancala RE: redundant animations

#### Sunday:
- finished patch_1.2.5 for memory leaks
- celebrated Mother's Day with siblings in WA on the phone to participate long-distance

[closures]: https://docs.swift.org/swift-book/LanguageGuide/Closures.html#//apple_ref/doc/uid/TP40014097-CH11-ID546
[escaping closure explanation 1]: https://learnappmaking.com/escaping-closures-swift/
[escaping closure explanation 2]: https://www.andrewcbancroft.com/2017/04/26/what-in-the-world-is-an-escaping-closure-in-swift/
[closures are escaping by default]: https://stackoverflow.com/questions/39433221/why-do-closures-require-an-explicit-self-when-theyre-all-non-escaping-by-defa
[closure within closure]: https://stackoverflow.com/questions/40072918/how-to-call-non-escaping-closure-inside-a-local-closure?r=SearchResults&s=2|125.2290
[my closure question]: https://stackoverflow.com/questions/61625613/why-are-optional-function-type-parameters-treated-as-escaping-by-default?noredirect=1#comment109008721_61625613
[my question duplicated this]: https://stackoverflow.com/questions/39618803/swift-optional-escaping-closure-parameter
[good answer to my question]: https://oleb.net/blog/2016/10/optional-non-escaping-closures/
