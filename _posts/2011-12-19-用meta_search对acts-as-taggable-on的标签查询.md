---
layout: post
title:  "用meta_search对acts-as-taggable-on的标签查询"
date:   2011-12-19 15:39:51
categories: [Ruby On Rails]
tags: [rails, meta_search, acts-as-taggable-on, tag, search]
---

项目里有用到meta_search与acts-as-taggable-on这两个gem，后台录入的MM需要有通过标签查询的功能meta_search的文档好像没有提到类似这种需求的解决方法，GOOGLE之：找到如下解决方法http://stackoverflow.com/questions/5766427/combining-meta-search-with-acts-as-taggable-onPost.metasearch({:title_or_tag_taggings_tag_name_contains => params[:search]})在我项目中，acts-as-taggable-on :times 相应改成

<%= f.select :time_taggings_tag_name_contains, [["请选择",""]]+Tag::TIMES %>在console中测试能达到效果，但是生成的SQL，有些复杂ruby-1.9.2-p180 :004 > Solution.metasearch({:time_taggings_tag_name_contains => "XXX"})

Solution Load (6.6ms) SELECT `solutions`.* FROM `solutions` LEFT OUTER JOIN `taggings` ON `taggings`.`taggable_id` = `solutions`.`id` AND taggings.tagger_id IS NULL AND taggings.context = 'times' AND `taggings`.`taggable_type` = 'Solution' LEFT OUTER JOIN `tags` ON `tags`.`id` = `taggings`.`tag_id` WHERE (`tags`.`name` LIKE '%XXX%')

有个问题：我发布到服务器后测试报错：Mysql2::Error: Unknown column 'tags.id' in 'on clause': SELECT COUNT(DISTINCT `solutions`….......我比较了一下本机与服务器的MySQL版本：本机：

mysql5 Ver 14.14 Distrib 5.1.53, for apple-darwin10.5.0 (i386) using readline 6.1服务器：mysql Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (x86_64) using readline 6.1不知道是不是因为服务器版本的差异导致的这个问题。