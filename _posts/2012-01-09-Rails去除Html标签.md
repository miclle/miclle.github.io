---
layout: post
title:  "Rails去除Html标签"
date:   2012-01-09 17:23:20
categories: [Ruby On Rails]
tags: [rails, html, helper]
---

#ModuleActionView::Helpers::SanitizeHelper

*[actionpack/lib/action_view/helpers/sanitize_helper.rb](http://api.rubyonrails.org/files/actionpack/lib/action_view/helpers/sanitize_helper_rb.html)strip_tags(html)Strips all 

[HTML](http://api.rubyonrails.org/classes/HTML.html) tags from the 

html, including comments. This uses the html-scanner tokenizer and so its 

[HTML](http://api.rubyonrails.org/classes/HTML.html) parsing ability is limited by that of html-scanner.Examplesstrip_tags(

"Strip <i>these</i> tags!")

# => Strip these tags!

strip_tags(

"<b>Bold</b> no more! <a href='more.html'>See more here</a>...")

# => Bold no more! See more here...

strip_tags(

"<div id='top-bar'>Welcome to my website!</div>")

# => Welcome to my website!Source: 

[hide]()# File actionpack/lib/action_view/helpers/sanitize_helper.rb, line 83

def 

strip_tags(

html)

self.

class.

full_sanitizer.

sanitize(

html).

try(

:html_safe)

endActionController::Base.helpers.strip_tags参考文章：

[http://rubyer.me/blog/1124](http://rubyer.me/blog/1124)