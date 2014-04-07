---
layout: post
status: publish
published: true
title: Ruby on Rails plugin configuration
author: Andrew Kuklewicz
author_login: admin
author_email: andrew@beginsinwonder.com
author_url: http://
wordpress_id: 76
wordpress_url: http://beginsinwonder.com/2007/10/15/ruby-on-rails-plugin-configuration/
date: '2007-10-15 08:07:23 -0400'
date_gmt: '2007-10-15 02:07:23 -0400'
categories:
- Uncategorized
tags: []
comments:
- id: 166
  author: Daniel
  author_email: daniel@jarmark.org
  author_url: http://jarmark.org/
  date: '2007-10-21 06:44:52 -0400'
  date_gmt: '2007-10-21 00:44:52 -0400'
  content: 'I''m  wondering  maybe my plugin AppConfig will be usefull for You vide:
    http://jarmark.org/projects/app-config'
- id: 167
  author: Andrew Kuklewicz
  author_email: andrew@beginsinwonder.com
  author_url: http://
  date: '2007-10-21 08:17:20 -0400'
  date_gmt: '2007-10-21 02:17:20 -0400'
  content: I like AppConfig - and I've used it on 2 apps now - but I don't think I
    want to embed that plugin in another plugin. It is another interesting approach
    - requires an  environment.rb include to then be able to put your own config into
    the regular rails initializer (if I recall right).
---
<p>I work on Ruby on Rails plugins fairly often, and I'm always curious how people make their plugins configurable.</p>
<p>For example, <a href="http://code.google.com/p/activemessaging/">ActiveMessaging</a> uses several config files - some are yaml, some are ruby - all of them get loaded when the plugin gets initialized.  ActiveMessaging has more than a bit of configuration, so distinct files for it makes sense.  Also, it has less singular values that get set, and more sets of configuration values (e.g. all the values for a message broker connection).</p>
<p><a href="http://comatose.rubyforge.org/index.html">Comatose</a> uses a singleton with attributes that get defined in a block - so like the Rails initializer, you can call this define method in an environment.rb.  Again, this makes sense, there are only a few values to fiddle with, and you very often don't have to mess with them at all.</p>
<p>Not sure if I'll use it, but I've been playing with an idea where you can use constants to override config values using constants.  Makes sense for a plugin where you have default values that would rarely, and often individually, be overridden.  Nice thing about this is that constants can be defined even before the config class, so if you need them to be set before the plugin is loaded, this provides a way.  </p>
<p>Anyway, to make it easier, I wrote a little helper method to define class attributes, set the default value, and check for constants to override the default, all at one time.</p>
<p><code><br />
class Config</p>
<p>  class <<self<br />
    def set_config_value(var_sym, default=nil)<br />
      cattr_accessor var_sym<br />
      const_name = var_sym.to_s.upcase<br />
      value = (Object.constants.include?(const_name)) ? Object.const_get(const_name): default<br />
      class_variable_set("@@#{var_sym}".intern, value)<br />
    end<br />
  end</p>
<p>  # SOME_CONFIG_VALUE set as a constant will override the default<br />
  set_config_value :some_config_value, "this is a default"</p>
<p>end<br />
</code></p>
