---
layout: post
title:  "用rails-erd生成rails项目的实体关系图"
date:   2012-01-12 16:03:29
categories: [Ruby On Rails]
tags: [ERD]
---

有时候我们需要形象的展示实体间的关系(Entity-Relationship Diagrams)rails-erd 这个gem 可以帮我们实现：首先安装Graphviz

% brew install cairo pango graphviz # Homebrew on Mac OS X% sudo port install graphviz # Macports on Mac OS X% sudo aptitude install graphviz # Debian and Ubuntu 然后在开发环境中使用group :development do

gem "rails-erd"

end安装

% bundle install 

生成PDF

% rake erd

然后在项目根目录下就会生成ERD.pdf[http://rails-erd.rubyforge.org/](http://rails-erd.rubyforge.org/)