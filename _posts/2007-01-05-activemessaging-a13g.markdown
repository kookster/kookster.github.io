---
layout: post
status: publish
published: true
title: ActiveMessaging (a13g)
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 53
wordpress_url: http://beginsinwonder.com/2007/01/05/activemessaging-a13g/
date: '2007-01-05 00:16:30 -0500'
date_gmt: '2007-01-04 18:16:30 -0500'
categories:
- code
tags: []
comments: []
---
<p><a href="http://jutopia.tirsen.com/">Jon Tirsen</a> and friends created a great product, ActiveMessaging, to incorporate into Rails the ability to send and receive <a href="http://stomp.codehaus.org/">Stomp</a> messages - specifically, this seems to mostly be used with <a href="http://www.activemq.org/site/home.html">ActiveMQ</a> and its <a href="http://www.activemq.org/site/stomp.html">Stomp protocol support</a>, and depends on the <a href="http://stomp.codehaus.org/Ruby">Ruby Stomp client</a> courtesy <a href="http://kasparov.skife.org/blog/">Brian McCallister</a>.</p>
<p>Since I am using a13g quite actively at <a href="http://www.prx.org">prx</a>, Jon has been kind enough to let me help maintain this product, and hopefully even add some to it.  There is now a <a href="http://code.google.com/p/activemessaging/">google code site</a>, and a <a href="http://groups.google.com/group/activemessaging-discuss">mailing list</a>, thanks Jon.</p>
<p>First up are some bug fixes and quick enhancements - I sent a few in to Brian McCallister that will hopefully show up in a 1.0.3 release of the Ruby Stomp client.  I also have a few fixes and minor enhancements to make to a13g that should show up soon, and I will also be working on any issues logged on the new google code site.</p>
<p>But what to do after that? I have some examples I want to throw out there for doing synchronous messaging between a rails and a java app, and I want to add even more documentation to the wiki so folks can get going with this easier - what else do people want? Get on the mailing list and let's talk about it.<!--795c36f0bf6a930feaa59f873aeeefd4--><!--c7676276540c4c0f5b5cbdc388d6c9a8--></p>
