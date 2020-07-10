---
tags: [Jekyll]
date: 2020-06-07
---
{%- assign ghpages_img = site.static_files | where: "path", "/assets/img/ghpages_publish_source.png" -%}
{%- assign ghpages_img_path = ghpages_img | map: "path"  -%}
{%- include jsLog_MD.html toDump='ghpages_img_path' dumpExpression=ghpages_img_path -%}
## Jekyll site progress update
#### Monday:
As I mentioned at the end of [my progress report for May 31st]({%- post_url 2020-05-31-steam-burns-and-ffmpeg -%}), after finishing the App Preview videos for the App Store and successfully uploading them after many rejected submissions, I was ready to officially submit my app to the App Store. Of course, it got immediately auto-rejected for not having a link to a privacy policy. I have no idea how to write a privacy policy, though I'm sure my app respects privacy more than any commercial app on the market (I have no features that require private information, and I intentionally decided not to include any advertising).

It seems like my best options are:
1. Use a [Privacy Policy generator][best pp gens] for free online
2. Additionally, [set up an LLC][what is an LLC] for extra legal protection

I [researched][pp service 1] and [tried out][pp service 2] several [privacy policy generators][pp service 3]. Luckily, since my app is so limited in the data it collects (none) it was fairly straight forward to answer the questions which prepare the template. I only changed a few things, like replacing singular pronouns 'I, me, my' for collective 'Us, Our, We,' because I chose not to incorporate. I feel slightly more vulnerable without an LLC, but realistically I shouldn't need to worry about being sued. This is my first app, and I am not charging for it, nor handling personal information with it. I might consider it in the future.

Then I looked into using GitHub pages to host a "support url," which is the other condition that Apple requires. A ["support url" is what Apple calls a website][support url] for providing users a means of accessing information about your app, report bugs, submit feature requests, troubleshoot problems and contact the developer for assistance. It seems like a glorified email address, but in the long run it is better to have a website for your app. That way, users won't need to constantly bother the developer for common or Frequently Asked Questions, and the site itself can serve to promote the app as well.

#### Tuesday:
- set up [Ruby][ruby setup], Gems, [Jekyll][jekyll install]
- set up GitHub Pages repo to host this website
  - for a starting-from-scratch approach for building your own website with GithHub Pages *then* incorporating Jekyll, [I recommend this tutorial][start from scratch]
  - or if you are more interested in working with Jekyll out-of-the-box and getting to know all of it's features before diving in, [I recommend this video series.][Giraffe academy jekyll]

- published this Jekyll website to GitHub Pages
  - found out how `baseurl` works when testing on localhost:

    The way you organize your GitHub Pages repo affects your website's domain. If you [follow the Giraffe Academy tutorial][Giraffe academy jekyll], you would need to set `baseurl = <YourRepoName>`

    If you [follow this other tutorial][microwavesam tutorial], your website's GitHub repo name will be in the format `<UserName>.github.io` and you do not need to set `baseurl`.

    The first option is similar to how you would build a GitHub Pages site for a particular GitHub project. Let's say that you finished writing a node.js API that has a repo on GitHub. If you want a nice website for the documentation of the API, you would create a new branch called `gh_pages` and publish the GitHub Pages site with all your Jekyll files from there. [Then you would choose the `gh_pages` branch to publish the GitHub Pages site from.][choose publish branch]

    The second option creates a conventional, personal website (GitHub refers to it as a 'user' or 'organization' site). If you choose this option, you won't be able to choose which branch or folder to publish from

    If your site's source files are located in the default publishing source —master for user and organization sites— then you cannot choose another branch or folder to publish the site from.

    ![navigate to the Settings tab][gh_pages publish source]

    Otherwise if your repo is primarily for some other project and you just need a website for it, create a `gh_pages` branch and go to your settings to choose the `gh_pages` branch to publish from. Then you will need to use `baseurl` in Jekyll as described above.

#### Wednesday:
- got this [Jekyll site to use new theme][jekyll themes], a Gem plugin called *Time Machine*
- installed Atom to work on the project
  - [How to install terminal support in Atom][terminal Atom]
- mixed layouts from the default theme 'Minima' with 'Time Machine'
- went to martial arts class in the gym's new location
- attended Zoom meeting to learn the history of [Sayoc][sayoc]

#### Thursday:
- got a basic navigation menu to work
- purchased my name as a domain! www.alexbeaty.com from www.namecheap.com with free WhoIs Privacy Guard with no expiration
  - did you know that some [countries require their country's TLD][domain privacy] to preserve the owner's privacy?
  - OVH is a commercially registered TLD domain that also conforms to privacy by default
- worked on using 'layouts' for webpages with Jekyll

#### Friday:
- reorganized Minima SCSS files to work with this project, combined with Time Machine's styles
- studied [Jekyll with Giraffe Academy][Giraffe academy jekyll] on YouTube
- tried to configure CNAME for www.alexbeaty.com to [redirect][redirect CNAME] to this GitHub Pages website
- started implementing [pagination][pagination in jekyll] for indexing my blog posts, encountered build errors

#### Saturday:
- website is almost fully functional
- pagination to list blog posts, and navigation bar are complete

#### Sunday:
- learned how to use [code snippets in Atom][snippets in Atom] for Jekyll in order to call console.log() in javascript in Markdown files
- reorganized the 'Mancala' pages section of this website
- created PDF of privacy policy for Mancala Fantasy - Online
  - embedded pp onto website page and used CSS for center alignment

[best pp gens]: https://www.oberlo.com/blog/privacy-policy-generator
[what is an LLC]: https://www.incfile.com/blog/post/do-amateur-app-developers-need-to-form-an-llc/
[pp service 1]: https://app-privacy-policy-generator.firebaseapp.com/
[pp service 2]: https://www.shopify.com/tools/policy-generator
[pp service 3]: https://app.termly.io/builder/documents/new?template_id=12
[support url]: https://teamtreehouse.com/community/what-is-support-url
[jekyll install]: https://jekyllrb.com/docs/installation/
[ruby setup]: https://jekyllrb.com/docs/ruby-101/
[start from scratch]: http://jmcglone.com/guides/github-pages/
[Giraffe academy jekyll]: https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB
[microwavesam tutorial]: https://www.youtube.com/watch?v=FiOgz3nKpgk
[choose publish branch]: https://docs.github.com/en/github/working-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#choosing-a-publishing-source
[gh_pages publish source]: {{ ghpages_img_path | url }}
[jekyll themes]: http://jekyllthemes.org/
[terminal Atom]: https://stackoverflow.com/questions/43013195/how-to-open-the-terminal-in-atom
[sayoc]: https://sayoc.com/history/
[domain privacy]: https://en.wikipedia.org/wiki/Domain_privacy
[redirect CNAME]: https://www.namecheap.com/support/knowledgebase/article.aspx/385/2237/how-to-redirect-a-url-for-a-domain
[pagination in jekyll]: https://jekyllrb.com/docs/pagination/
[snippets in Atom]: https://flight-manual.atom.io/using-atom/sections/snippets/#platform-mac
