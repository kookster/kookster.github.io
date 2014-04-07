---
layout: post
status: publish
published: true
title: ruby stomp gem version 1.0.3 released
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 54
wordpress_url: http://beginsinwonder.com/2007/01/05/ruby-stomp-gem-version-103-released/
date: '2007-01-05 22:18:36 -0500'
date_gmt: '2007-01-05 16:18:36 -0500'
categories:
- code
tags: []
comments: []
---
<p>Thanks to <a href="http://kasparov.skife.org/blog/">Brian McCallister</a>, he put in the changes <a href="http://www.nabble.com/Re%3A-stomp.rb-changes-please--tf2922761.html">I mentioned</a>.</p>
<p>This should make the changes to a13g cleaner, and we can now take advantage of having the reconnect wait time configurable.<br />
All in all, it makes a13g closer to implementing a 'reliable' listening service.</p>
<p>There is one sorta ugly bit, the <code>__old_receive</code> method was a fine way to do this when I was extending the Connection class, but could use refactoring...after I get a good check in of fixes to a13g, I'll submit something prettier.  But as we used to say back in <a href="http://www.cs.yale.edu/people/eisenstat.html">Stanley Eisenstat</a>'s classes (which I wish I had taken more of): <a href="http://www.joelonsoftware.com/articles/HighNotes.html">good is great, but done is better</a>.<!--bc0897c6c021adc82d228b2cfbeeaaf4--><!--6a17968c0ce41bd53f792a7ba7e27e44--></p>
