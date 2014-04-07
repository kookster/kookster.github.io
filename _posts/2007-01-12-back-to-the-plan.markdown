---
layout: post
status: publish
published: true
title: Amazon Web Services (AWS) S3 working, now back to the plan
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 55
wordpress_url: http://beginsinwonder.com/2007/01/12/back-to-the-plan/
date: '2007-01-12 03:43:48 -0500'
date_gmt: '2007-01-11 21:43:48 -0500'
categories:
- code
tags: []
comments: []
---
<p>I've been spending the last few days working with the <a href="http://amazon.rubyforge.org/">AWS::S3 library</a>.</p>
<p>Works well - we are streaming large audio files over it, so we needed something better than the ruby s3 bindings amazon released (though they are very clear in their code that they do not handle big files well).</p>
<p>Only hitch was setting metadata when creating an AWS::S3::S3Object - couldn't get it to work.<br />
Tried creating a 1 byte file to start, then updating with metadata, that was fine, but the initial create was erroring out, or the metadata would not take.</p>
<p>Luckily, <a href="http://rubyforge.org/pipermail/amazon-s3-dev/2006-December/000007.html">there is a patch offered by 'Lars'</a> which makes it all work for me now.</p>
<p>I posted this to the list, but here is some sample working code for setting metadata on create (once the patch is applied):</p>
<p>1) Using the store class method:<br />
<code><br />
AWS::S3::S3Object.store(<br />
    'myfile-81805',<br />
    open('/data/production/amazon/myfolder/myfile-81805'),<br />
    'my-s3-bucket',<br />
    :content_type=>'audio/mpeg',<br />
    'x-amz-meta-my-file-name'=>'my.mp3')<br />
</code></p>
<p>2) Using the Bucket new_object method, and then store, you don't have to include the metadata prefix 'x-amz-meta-':<br />
<code><br />
my_bucket = AWS::S3::Bucket.find('my-s3-bucket')<br />
s3o = my_bucket.new_object<br />
s3o.key = 'myfile-81805'<br />
s3o.value = open('/data/production/amazon/myfolder/myfile-81805')<br />
s3o.content_type = 'audio/mpeg'<br />
s3o.metadata['my-file-name'] = 'my.mp3'<br />
s3o.store<br />
</code></p>
<p>So with that working, back to ActiveMessaging, and getting changes fully tested and checked in.<!--2ccedceac1fe62e583fce14fb1d62b4d--><!--38c043bba319681f1656259cf286352d--><!--f39502ca91b1459a52101390f25b8979--></p>
