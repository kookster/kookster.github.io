---
layout: post
status: publish
published: true
title: Yahoo pipes foray
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 60
wordpress_url: http://beginsinwonder.com/2007/02/10/yahoo-pipes-foray/
date: '2007-02-10 08:08:49 -0500'
date_gmt: '2007-02-10 02:08:49 -0500'
categories:
- code
- folly
tags: []
comments: []
---
<p><a href="http://pipes.yahoo.com">New free toys!</a><br />
Everyone can appreciate the Unix pipe concept, <a href="http://cm.bell-labs.com/cm/cs/who/dmr/hist.html">even if it was a slow start to get it added</a>. It's nice to see |s inspiring folks still, as with Yahoo pipes.<br />
<a href="http://pipes.yahoo.com/pipes/CBY_2Ui42xG8yCYUr_ymrA">Did my own based on prx and flickr, give it a run.</a><br />
I find it only works right about 50% of the time - seems like it doesn't retrieve all the feeds each time I request, so sometimes all I get are PRX  listings, other times I get prx with the associated flickr images based on the pieces.<br />
A few things I think could improve:</p>
<ul>
<li>When dragging the end of a control, like a Text Input, to be the input to another form value, like in a URLBuilder, the drag and drop is very imprecise.  In a list of three Query Parameters, I could never drop onto the middle element, it just wasn't able to only select that one middle parameter</li>
<li>Add a For Each: replace that does an element in a feed item, rather than the whole element. Or adds to it, hard to actually combine feedw without something like this</li>
<li>Have a smarter Union with options like interleaving rather than just putting all of one feed after another</li>
<li>The URLBuilder does not put the arguments into the query string in the order you have them in the form</li>
<li>While I love the debugger, there is no way to immediately run a pipe, you can only see debugger output, I want a way to preview the run</li>
<li>The output from a given source can only go to one widget - it would be great if the output of a fetch could be used for different processing, then recombined.  I did this, but needed 2 almost identical Fetch controls to make it work, and adds another request to the processing time
<li>
<li>Save is buggy - I have made changes to the URLBuilder, but Save would be disabled till I changed a different control.  I also had once where I had saved some changes, then gone back to edit after running, and the changes were goe...</li>
<li>Consistent behavior of the fetch/content analysis/for each replace.  I see times when I run it that no results come back, other times they work great.  I have often seen that running a Content Analysis operation would flake out and show no results, even though the fetch above it would have results when I debug it.  This same inconsistency seems possibly related to the general inconsistency of results mentioned above.</li>
<li>Also saw another bug after adding a For Each where I could not add the sub source to the For Each.  Had to save, close up, and come back in to get it to work.</li>
</ul>
<p>So all in all a good toy, but not ready for anything real - but I see the potential.  Really the UI is unbelievable, and while a bit buggy still, I do not know how they made it such a rich UI - the pipes alone are an amazing bit of work.<br />
Having used lots of GUI based tools like Informatica Powermart or the Weblogic Integration tools, or even just Rational Rose or Visio, I see where something like this is not far from being a very competitve interface, and incredibly light weight and responsive.<!--9b4fe5d49e8d88501d5b33b7db4f9c44--><!--ff1d3519715a267f3badf2ac0d9c94b2--><!--a5acc83603b036c1017624cbca6516c7--><!--5d2aa96b38b47fc59ea377622967057d--></p>
