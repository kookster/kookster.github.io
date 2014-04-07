---
layout: post
status: publish
published: true
title: 'Installing Apache 2 and PHP 5 on Mac OS X   '
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 63
wordpress_url: http://beginsinwonder.com/2007/03/04/installing-apache-2-and-php-5-on-mac-os-x/
date: '2007-03-04 05:05:01 -0500'
date_gmt: '2007-03-03 23:05:01 -0500'
categories:
- code
tags: []
comments: []
---
<p>Long ago I installed apache 2 instead of the lame-o version of apache that comes with OS X so I could use it to test rails configurations.  Lately, I have been doing more work with Drupal (e.g. <a href="http://publicradioquest.com/aff/23/2">Public Radio Talent Quest</a>), and messing with WordPress, so I wanted to run them locally to make my development much easier.</p>
<p>Also, I should mention, I try to avoid installing anything using fink or mac ports.  Not because there is anything wrong with them per se, but I like control over what I install and where it goes, and as 9 times out of 10 I am going to be installing the same thing on at least 1 other OS, I want to do it from scratch.  I am probably insane.</p>
<p>When I went to search for some easy instructions for installing php5 and apache2, <a href="http://www.phpmac.com/articles.php?view=252">best thing I could find was here</a>.  Wasn't bad, just change the instructions to prefix under "/usr/local/", and all went well.</p>
<p>Then I hit the PHP5 make, and it died, <a href="http://www.maclife.com/forums/topic/83340">the error turns out to be pretty well known</a>, and is related to PHP5 only compiling against MySql 4, whereas I live in this century and run MySql 5.  <a href="http://bugs.mysql.com/bug.php?id=19575">Apparently there is a bug report for this</a>.  A quick install of mysql 4 from the tar.gz package, and updating the softlink for /usr/local/mysql, and everything compiled.  Flip the soft link back to MySql 5, and so far everything runs fine.</p>
<p>So once again, with a bit more work, compiling from src triumphs!</p>
