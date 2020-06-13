---
tags: mancala iOS
---

I finally uploaded my first build of Mancala to TestFlight. I can get up to 10,000 public testers and I don't think I can handle that amount of feedback on my own,
 so I will limit it to my coworkers, friends and family at first.

I actually thought I had uploaded it on Friday and expected Apple not to evaluate it until after the weekend, so I didn't check the results until Saturday.
That was when I realized it failed again because of an automatic validation concerning the screen orientation (my app is landscape only) on the iPad.
I decided to just forget iPads and only offer the app for iPhone. Bingo. It passed, and now I had to wait for the next validation to complete.

The validations take a while but not as long as I expected. Now I am not actually sure in TestFlight your app is code reviewed by a real person.
So by Tuesday I checked the status again and found that it had been automatically rejected for another reason having to do with cryptography export compliance.
All I had to do was [set a property in my the app.json](https://help.apple.com/xcode/mac/current/#/dev0dc15d044) about that, which was simple because my app has nothing to do with cryptography directly.
 All the networking is handled by Apple's Game Center which would handle it through TLS I assume.

 If my app used cryptography it would need to fall under the 'exempt' category to be legally downloaded outside the US. I would have needed to get an exemption from Apple in the form of an App Encryption Export Compliance Code.

I had been promoting the release on social media and that morning I sent out invitations to all my coworkers. About an hour after it was uploaded I got my first
crash report from my sister! She said "the game was over and I clicked on Menu to get the next game started. Crashed instead of displaying the Menu."
I frantically started debugging and quickly found that an index out-of-bounds exception was thrown when the game ended. Rookie mistake!
I was too excited to get the build uploaded that I forgot to thoroughly test recent changes I made.
