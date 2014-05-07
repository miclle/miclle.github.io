---
layout: post
title:  "rails中的html_escape,escape_javascript"
date:   2011-12-17 14:27:50
categories: [Ruby On Rails]
tags: [ruby, rails, JavaScript, gsub, html]
---

ERB::Util activesupport/lib/active_support/core_ext/string/output_safety.rbhtml_escape(s)A utility method for escaping 

[HTML](http://api.rubyonrails.org/classes/HTML.html) tag characters. This method is also aliased as 

h.In your 

[ERB](http://api.rubyonrails.org/classes/ERB.html) templates, use this method to escape any unsafe content. For example:<%=

h 

@person.

name %>Example:puts 

html_escape(

"is a > 0 & a < 10?")

# => is a &gt; 0 &amp; a &lt; 10?Also aliased as: 

[h](http://api.rubyonrails.org/classes/ERB/Util.html#method-i-h)Source: 

[hide]()# File activesupport/lib/active_support/core_ext/string/output_safety.rb, line 18

def 

html_escape(

s)

s = 

s.

to_s

if 

s.

html_safe?

s

else

s.

gsub(

/&/, 

"&amp;").

gsub(

/\"/, 

"&quot;").

gsub(

/>/, 

"&gt;").

gsub(

/</, 

"&lt;").

html_safe

end

end

ActionView::Helpers::JavaScriptHelper actionpack/lib/action_view/helpers/javascript_helper.rb

escape_javascript(javascript)Escape carrier returns and single and double quotes for JavaScript segments. Also available through the alias j(). This is particularly helpful in JavaScript responses, like:$('some_element').

replaceWith(

'<%=j render 'some/

element_template' %>');Also aliased as: 

[j](http://api.rubyonrails.org/classes/ActionView/Helpers/JavaScriptHelper.html#method-i-j)Source: 

[hide]()# File actionpack/lib/action_view/helpers/javascript_helper.rb, line 19

def 

escape_javascript(

javascript)

if 

javascript

result = 

javascript.

gsub(

/(\\|<\/|\r\n|[\n\r"'])/) {

|match| 

JS_ESCAPE_MAP[

match] }

javascript.

html_safe? 

? 

result.

html_safe 

: 

result

else

''

end

end