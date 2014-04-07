---
layout: post
status: publish
published: true
title: My first Rails patch
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 72
wordpress_url: http://beginsinwonder.com/2007/05/17/my-first-rails-patch/
date: '2007-05-17 00:56:02 -0400'
date_gmt: '2007-05-16 18:56:02 -0400'
categories:
- code
tags: []
comments:
- id: 129
  author: Chris Kuklewicz
  author_email: ends-in-tea@personal.mightyreason.com
  author_url: ''
  date: '2007-05-17 15:19:14 -0400'
  date_gmt: '2007-05-17 09:19:14 -0400'
  content: Hmmm...twitter.  Now I have to go look at that.
- id: 130
  author: Andrew Kuklewicz
  author_email: andrew@beginsinwonder.com
  author_url: http://
  date: '2007-05-17 15:28:16 -0400'
  date_gmt: '2007-05-17 09:28:16 -0400'
  content: tis a much discussed rails app, and an interesting micro-blog/instant messaging/rss
    combo.
- id: 60778
  author: search health children saving account on line www natural south bend indiana
  author_email: ''
  author_url: http://www.everyhealthplans.com/search-health-children-saving-account-on-line-www-natural-south-bend-indiana.html
  date: '2009-10-26 09:52:04 -0400'
  date_gmt: '2009-10-26 03:52:04 -0400'
  content: |-
    <strong>search health children saving account on line www natural south bend indiana...</strong>

    donate umbrella models salts.sterilization massed ...
---
<p>...it's small, but found a bug in the new filter code in the ActionController for rails edge.<br />
Showed up using habtm with ActiveScaffold - go figure.</p>
<p>Lesson learned - Array.insert should probably be named Array.insert! - it changes the underlying array, and sometimes that's not what you mean to do.</p>
<p><a href="http://dev.rubyonrails.org/ticket/8383">http://dev.rubyonrails.org/ticket/8383</a></p>
<p>Now we'll see if it gets committed.</p>
