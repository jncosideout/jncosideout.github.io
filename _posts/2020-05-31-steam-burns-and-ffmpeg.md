---
title: Don't Play With Steam
tags: [mancala, ffmpeg, homebrew, xcode tools]
date: 2020-05-31
---
## My Week in Review
#### Monday:
We had another grill out at my parents' house on Memorial Day. This time we cooked chicken breasts. I like to coat my grill with onion and then olive oil before cooking. Usually I heat the grill first and then rub half an onion on the hot surface. Next, I like to take a rag soaked in olive oil and brush that on the grill after the onion. But last Saturday when we grilled, the meats still stuck to the grill despite doing this treatment. So this time, we applied onion and olive oil before heating the grill. We also juiced the onion and mixed that with the olive oil instead and brushed the mixture on.

When it was time to take the chicken off the grill, the temperature gauge read about 600 deg. Despite that warning, I proceeded to open the hatch of the egg-shaped grill, and the steam that escaped burned my knuckles as I gripped the front handle, causing me to drop the hatch with a heavy 'thud.' My burns were very painful and for the remainder of the night I had to tend to them rather than join my family for the dinner I had prepared. Luckily, we have aloe vera growing in the backyard that I could apply directly to the burns on my fingers. I was still able to enjoy the [dessert that was prepared with ice cream, peaches and Chardonnay][ice cream recipe]. Hopefully my fingers will heal up without outside medical attention since I am uninsured.

##### Mancala Progress Monday:
Reviewed gameplay videos I created Sunday, discovered that just one image in the animation was being rendered larger than the rest. I have created images for every possible number of beads that can occupy a pit on the Mancala gameboard and the animations just switch between these images. Images in iOS apps must conform to the [retina display resolutions](https://developer.apple.com/design/human-interface-guidelines/ios/icons-and-images/image-size-and-resolution/), and so I provided three versions for every image in my app.

It just so happens that only one of my images, "Pit \#40", has a @3 size version that is 213x213 while all the other pit images are 225x225. I changed Pit \#40's size to 225x225 but it still would not render at the correct size. After some research, I found that I could get rid of all my @2 and @3 images if I set ['Scales' = "single scale" mode][vector scaling] for all of my images and Xcode will create the necessary sizes for me when building my app, as long I am using vector images like pdf or png (the reference I linked to has diferrent names for those values because it was dealing with Xcode ver. 6)

#### Tuesday:
Modified the layout of the 'player labels' (P1 & P2) in the GameScene. Previously they were in the top-left and bottom-right corners of the screen, now they are inside the game board, vertically aligned in the center. All changes were made in-code since I am not using Interface Builder to layout my views. So to get the proper placement on the screen, I have to programmatically position them in the view. This involved saving the anonymous nodes created at the time the board's frame is drawn and using them later to position the 'player labels.'

<h4 id="making-app-preview-videos">Wednesday:</h4>
The videos that I made last Sunday by taking screen captures of the simulator failed to upload to App Store Connect. They were automatically rejected for not having the correct dimensions. I assumed that since the simulators were set to display on my Mac with the actual sizes of the iPhone models I was using, iPhone 8 Plus and iPhone 11 Pro Max, the output of the screen recordings would be 1-to-1 with the screen dimensions of those models. The best solution seems to be using the 'xcrun simctl io' cli tool to record the video. [simctl can do many other things][xcrun simctl tips] that may help you when it comes to the Xcode Simulator.

The output will be in the Native Resolution of the device model running on the simulator, but App Store Connect has 'Accepted Resolutions' that are proportional but different from the Native Resolutions. Therefore, the output videos must be resized. I used the cli tool ffmpeg for this and installed it via [homebrew][homebrew], a [package management][hb basics] system for macOS. I have used ffmpeg to make a few demo videos of my Mancala app for promotional purposes, and was informed that it is used in the backend of most video editing GUI-based programs. So I may as well learn it.

##### Martial Arts class in the rain
Wednesday night at 8pm, I went to my Sayoc class and found that our gym had a power outage from the recent storms. The judo class was still training despite having the lights off. The doors were wide open to let the dying ambient light in. My instructor is such a determined individual, that when we could not find alternate accommodations, we trained outside behind the gym. There was a large open field back there with a line of trees on two sides of the perimeter and houses on the right. It was a bit muddy but the breeze was nice, temperature just slightly cool for a Texas summer and enough light to see. We all wore gloves as a Covid19 precaution.

The gym owner and top BJJ instructor, Prof. Eddie came out to say 'hi' and told us he is moving the gym to a new, much larger location down the street. The gym will be broken down this weekend and they need help moving the mats and equipment. Not long after that it began to rain, and I noticed it was getting harder to see. We disregarded the rain and kept training, but soon the rain got heavier and the wind picked up.

All four of us quietly told each other we were getting cold, but nobody spoke up to the instructor about it. Finally, I said "I quit," and walked inside. I knew I would catch a cold if I stayed any longer, and getting sick is exactly what everyone has been trying to avoid during this Covid19 lockdown!

Inside the gym, we positioned our flashlights to spotlight our training area, and continued the class in the dimly lit space. When I started to warm up I began to enjoy the experience of practicing in low-light conditions. It was fun and memorable. A good way of practicing self-defense in a difficult situation.

#### Thursday:
Used ffmpeg and xcrun simctl to upload more videos to App Store Connect. Finished all 8 Plus videos, tomorrow I will work on 11 Pro Max videos. I am [putting together a guide]({%- post_url 2020-06-01-the-bare-min-ffmpeg-guide-for-ios-devs -%}) for getting these App Preview videos formatted correctly to be accepted by Apple, because it is not easy and I'm sure I'll need to reference this information again.

#### Friday:
Videos recorded on simulator for iPhone 11 Pro Max always has a lower frame rate, likely because the simulator cannot render at a high fps for this particular iPhone model (either poorly designed or my Mac does not have enought RAM).
I could not convert dimensions of my videos to accepted scales for App Store Connect, until I found out that it wasn't my fault, it was macOS's.

#### Saturday:
- finished uploading and making App Preview videos for iPhone11 6.5"
- started making new options for background animations in Mancala

I kept all my notes for each error I encountered while trying to produce videos that App Store Connect would not reject, including the solution to the major problem I encountered on Friday while formatting videos made with xcrun and the 11 Pro Max simulator.
If you think you're having the same problem, it could be that macOS recognizes imensions based on SAR of the video, <a href="{%- post_url 2020-06-01-the-bare-min-ffmpeg-guide-for-ios-devs -%}#macos-sar-scaling">which I explain here.</a>


#### Sunday:
- finalized background animations, asked friends for input
- submitted final build 1.3 to the App Store, rejected for missing a privacy policy
- need to extend background animations to provide options w/o swirling colors that "could make someone sick," according to my TestFlight feedback

[ice cream recipe]: https://www.allrecipes.com/recipe/264010/chef-jimmie-joness-drunken-peaches/?utm_source=emailshare&utm_medium=email&utm_campaign=email-share-recipe&utm_content=20200623
[vector scaling]: https://krakendev.io/blog/4-xcode-asset-catalog-secrets-you-need-to-know#nuisancenumba2brdatapreservehtmlnodetruecouldigetthisimagein3xresolution
[xcrun simctl tips]: https://www.iosdev.recipes/simctl/
[homebrew]: https://brew.sh
[hb basics]: https://dev.to/code2bits/homebrew---basics--cheatsheet-3a3n
[scale videos SAR]: https://stackoverflow.com/questions/53573468/using-ffmpeg-to-scale-app-preview-videos-for-the-appstore
