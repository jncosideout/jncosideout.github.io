---
date: 2020-04-12
tags: [xcode, git, mancala]
---
The last three days have been a mini-nightmare for my Mancala project. It started when I began to use git to manage my beta builds in TestFlight [in order to use crashlogs I receive in the future.]({%- post_url 2020-04-06-Crashlogs-in-Xcode -%})

So on Friday, I tested out using git to make a new branch for the next build, 1.2.3. After I branched, I got an [error saying my .pbxproj file was missing](https://stackoverflow.com/questions/12143281/project-xcodeproj-cannot-be-opened-because-it-is-missing-its-project-pbxproj), and my project could not be compiled. I didn't even know I had a .pbxproj file! So I created a new dummy project, took its .pbxproj file and injected it into my project and tried in vain to resolve my build errors.

Saturday, I kept trying but my simulator still wouldn't run my app. After wasting hours on trying to repair the workspace, and trying to start with a fresh workspace, I finally found the lost .pbxproj file of the original project. It had been committed to the master branch but had not been brought over to my new branch for Build_1.2.3. It appears that this will fix things.

This morning I confirmed that reinjecting the original project.pbxproj file into my original .xcodeproj archive allows everything to compile normally. I had to create new copies of some source files for my new branch but I was able to successfully build and run the project, which is a huge relief. I was so close to deleting my project, and at one point, Googling "how to uninstall xcode completely."!! I was able to reorganize git and continue updating documentation in my source code. Now I know to be careful to:

1. Always make a backup of the .xcodeproj and/or its internal .pbxproj archive
2. Commit the .pbxproj file and don't panic if nothing works anymore, you just need to commit a copy to the new branch.

### Helpful links
These links all show people with the same problem I had, but from different causes. They did not give me the solution but they helped me out. They may help you:

[cant find the .pbxproj file in xcode](https://stackoverflow.com/questions/30680796/cant-find-the-pbxproj-file-in-xcode)

[git cannot open .pbxproj file error after renaming xcode project and pulling](https://stackoverflow.com/questions/13768908/git-cannot-open-pbxproj-file-error-after-renaming-xcode-project-and-pulling-ch)

[how to resolve project.pbxproj file issue in xcode](http://burnignorance.com/iphone-development-tips/how-to-resolve-project-pbxproj-file-issue-in-xcode/)

[.xcodeproj cannot be opened because it is missing its project.pbxproj file](https://recalll.co/ask/v/topic/xcode-Project-UsersXDesktopXX.xcodeproj-cannot-be-opened-because-it-is-missing-its-project.pbxproj-file/55a10aac7d356308158b6f17)

[similar problem on vapor's github issues](https://github.com/vapor/vapor/issues/1620)

#### Permission errors
At one point I was trying to recreate my project in a new project, and I copied everything from the old workspace to the new one, so I was getting odd permission errors. I will include some of what I found here if anyone is interested, but be careful.

[the file myapp.app couldn't be opened because you don't have permission](https://stackoverflow.com/questions/24924809/the-file-myapp-app-couldnt-be-opened-because-you-dont-have-permission-to-vi)

[failed to chmod user library developer coresimulator devices no such file or dir](https://stackoverflow.com/questions/40485155/failed-to-chmod-user-library-developer-coresimulator-devices-no-such-file-or-dir)

[error while building project: xcode says you don't have permission](https://stackoverflow.com/questions/27355361/error-while-build-project-xcode-says-you-dont-have-permission/27355521)

[how to fix mac os x file permissions](https://dreamlight.com/how-to-fix-mac-os-x-file-permissions/)

[xcode 9.4 the file my app couldn't be opened because you don't have permission](https://stackoverflow.com/questions/50932339/xcode-9-4-the-file-my-app-couldn-t-be-opened-because-you-don-t-have-permission)
