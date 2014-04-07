---
layout: post
status: publish
published: true
title: Comatose Extensions
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 70
wordpress_url: http://beginsinwonder.com/2007/05/02/comatose-extensions/
date: '2007-05-02 02:39:37 -0400'
date_gmt: '2007-05-01 20:39:37 -0400'
categories:
- code
tags: []
comments: []
---
<p><a href="http://comatose.rubyforge.org/">comatose</a> is a lovely terse cms that you can integrate into a web application - unlike other rails cms systems which are the application.  Thing is, terse is great until you need something it does not do.  </p>
<p>At PRX we wanted to be able to upload/resize/attach images and files, have a preview mode to see what the home page would look like before we publish parts of the content, and also we wanted to be able to access session info so we could make some content vary based on info in a user's session (this is also part of how the 'preview' mode works).</p>
<p><a href="http://rubyforge.org/forum/forum.php?thread_id=13826&forum_id=7970">Folks on the forums</a> also seem to be trying to figure this kind of thing out, so I humbly offer what I have gotten to work.</p>
<p>So without exposing all the work I am cleaning up on extending comatose, <a href="http://www.rorpaste.com/paste/details/743">here is a bit of code</a> showing how to add the session info to the comatose pages so it can be accessed and used.</p>
<p>As for the rest of my enhancements - well, I need to make it into a plugin I think, that gets installed on top of comatose.  That will have to wait, as I am too busy adding enhancements at the moment to stop and package it....<!--5a94a3cf7a2a4ffd083ebceb6a1f7f96--><!--20033d58cad75a6fb6457e144b78dd3f--><!--bdabb1e8ad3cf1c7a93af2a90e9262f6--></p>
