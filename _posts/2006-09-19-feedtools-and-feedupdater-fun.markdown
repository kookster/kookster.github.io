---
layout: post
status: publish
published: true
title: FeedTools and FeedUpdater fun
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 8
wordpress_url: http://beginsinwonder.com/2006/09/19/feedtools-and-feedupdater-fun/
date: '2006-09-19 20:55:00 -0400'
date_gmt: '2006-09-19 14:55:00 -0400'
categories:
- code
tags: []
comments: []
---
<p>Playing around with<a href="http://sporkmonger.com/projects/feedtools/"> FeedTools and FeedUpdater</a>.<br />
<a href="http://sporkmonger.com/articles/2005/08/11/tutorial/">Fun stuff</a>.</p>
<p>Had a few lessons learned I wanted to share:</p>
<h4>1) load the rails app feed config file</h4>
<p>To get FeedUpdater to find my 'feed_updater.yml' file, I had to make a small change to some of the file loading logic.  It kept loading the example/default comfig - so I changed the list of paths to look for my file first, by climbing out of the vendor directory, and getting the file in the regular rails app config directory.<br />
<code><br />
config_file = FileStalker.hunt([<br />
"./feed_updater.yml",<br />
"../config/feed_updater.yml"<br />
])<br />
</code><br />
to:<br />
<code><br />
config_file = FileStalker.hunt([<br />
"../../../config/feed_updater.yml",<br />
"./feed_updater.yml",<br />
"../config/feed_updater.yml"])<br />
</code></p>
<h4>2) Use the rails app model objects in the custom updater script.</h4>
<p>This took some experimentation to figure out.</p>
<p>As the <a href="http://wiki.rubyonrails.com/rails/pages/HowToUseActiveRecordThroughStandAloneScript">rails wiki says</a>, you need to require the environment script to be able to use the rails app goodies in a standalone script.  But where, pray-tell, should you put this require?</p>
<p>Use the on_begin method of the custom script.<br />
So if you have in your 'feed_updater.yml':</p>
<pre>load_script: lib/my_feed_updater.rb</pre>
<p>Then in this file, you need something like the following:<br />
<code><br />
class MyFeedUpdater < FeedTools::FeedUpdater</p>
<p>  on_begin do<br />
    #load all thing needed to use rails app stuff<br />
    require File.dirname(__FILE__) + '/../config/environment'</p>
<p>    #use your model like its going out of style<br />
  end</p>
<p>  on_update do |feed, seconds|<br />
    self.logger.info("Loaded '#{feed.href}'. Updated (#{feed.title}) in #{seconds} seconds.")<br />
  end</p>
<p>  on_error do |href, error|<br />
    self.logger.info("Error updating '#{href}':")<br />
    self.logger.info(error)<br />
  end</p>
<p>  on_complete do |updated_feed_hrefs|<br />
  end<br />
end<br />
</code><br />
Hope someone else gets some fun out of this.<!--2354f77e0c08687c0d3670ac02f56fe6--><!--459e65add9b2e5f0606b83b6d2b88a92--></p>
