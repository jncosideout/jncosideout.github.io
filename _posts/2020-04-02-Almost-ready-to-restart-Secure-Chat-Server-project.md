---
tags: [Ubuntu, MySQL, Covid19, Secure Chat Server 2]
---
On Monday I looked at the first crashlog from my TestFlight tester. It appears that the game crashed when the game info text was trying to display a message, but unwrapped a nil optional.  So I added some error handling for that. I'm not sure if this was the root cause of the error so I'll need to wait for more testers to report crashes and submit crashlogs. TestFlight is supposed to include a crashlog with each report sent by a user who is on iOS13 but it doesn't seem to work all the time. I also started adding in-code documentation to my source files.

Tuesday I loaded the password database schema from Secure Chat Server 1 into MySQL on my Ubuntu machine. Soon I will need to set up Connector J/JDBC to connect my server to the database. Wednesday, April 1st, I spent most of the day trying to get the [systemd process][what is systemd] I made to [launch MySQL at start up][guide I followed], but it just wasn't working. I couldn't configure it's ExecStart but looking at the journalctl log helped with that. I still needed to figure out why mysqld could not access etc/my.cnf, but I took a break and went to hang out at the jiu-jitsu gym where I practice.

Last week, Texas was officially on lockdown. On March 19, Governor Abbot issued an executive order closing all gyms and certain "non-essential" establishments, so that included my BJJ gym. As an April Fool's Day prank I decided to bring my 5ft long training spear inside with me. When I stepped through the door I swung it around and said loudly "back up! I'm 'Social Distancing'!" I think if I didn't know the owner and other people there so well, I would have been kicked out.

So Thursday I got back to work on configuring my systemd script for MySQL. I have heard [people complain about systemd][controversial] but I am new to Ubuntu so to me it's just another challenge. I got some help for a [question I asked on Stack Exchange][my question], but it turns out that a systemd startup process was already created during MySQL's installation so I moved on. I'm glad I took the time to learn this stuff but I need to move on to actually writing code for my new project, which I am calling Secure Chat Server 2. That's why I'm installing MySQL in the first place.

[my question]: https://askubuntu.com/questions/1222156/how-do-i-create-systemd-service-unit-configuration-file-for-mysql-server "Me on askubuntu.com"
[guide I followed]:https://dev.mysql.com/doc/mysql-secure-deployment-guide/5.7/en/secure-deployment-post-install.html#secure-deployment-systemd-startup "MySQL official docs"
[controversial]:https://www.linux.com/training-tutorials/understanding-and-using-systemd/ "The Controversy"
[what is systemd]:https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files "What is systemd?"
