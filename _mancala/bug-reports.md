---
purpose: Support
description: Submit your bugs here
title: Bug Reports
---
I eat bugs for breakfast, so send as many as you can find to me. Thank you.

A 'bug' is a term software developers use to refer to problems in the software that were definitely not the fault of their own, even if they were the sole developer on the project.

If you are sure that the behavior you are experiencing is truly a bug and not how the app was intended to work, you can submit it as a bug. If you have looked over the [FAQ]({%- link _mancala/FAQ.md -%}) and [Troubleshooting]({%- link _mancala/troubleshooting.md -%}) pages and you found that the undesired behavior you have identified is actually normal behavior, please send a [Feature Request]({%- link _mancala/feature-request.md -%}) instead, along with your suggestions on how the app should behave in order to improve your experience with it.

* Send me an email by clicking the button below. It will open your email client and fill in my address (you can ignore any security warnings from Firefox).

* Please include 'Feature Request' in the subject line. Thanks.

{%- assign formAction = "mailto:" | append: site.email -%}
{% include form.html form_action = formAction button_title = "Submit Bug Report" %}
