---
layout: post
status: publish
published: true
title: WLST fun
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 22
wordpress_url: http://beginsinwonder.com/2005/07/24/wlst-funive-been-having-somefun-of-late-with-be/
date: '2005-07-24 15:46:00 -0400'
date_gmt: '2005-07-24 09:46:00 -0400'
categories:
- code
tags: []
comments: []
---
<p>I've been having some fun of late with BEA's WLST tools.  I'm using 8.1 so the fun is that there are 2  versions, one online (while connected to a running admin server or instance), and one offline for doing configuration and creation of instances much as you would  through the configuration wizard application.</p>
<p>So here's the fun - it's jython based, but the tools start their own interpreter by default, but if you want to, you can create an ini file so you can import WLST as a module into a regular jython script.<br />
But, for whatever reason, the offline version does not work for this...you always have to run the wlst offline class as the interpreter.  I am testing a workaround, which since it is not particularly well documented, I am not quite ready to release into the  world, but I am hopeful :)<!--0e47502dd154789973a16943f4c4d9e4--></p>
