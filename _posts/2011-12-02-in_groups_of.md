---
layout: post
title:  "in_groups_of"
date:   2011-12-02 07:18:10
categories: [Ruby On Rails]
tags: [ruby, rails, group]
---

in_groups_of 这个方法可以将数组分组，的第一个参数指示几个元素一组，而第二个参数指示了当最后一组缺元素时用什么填补位置%w(1 2 3 4 5 6 7).in_groups_of(3) {|g| p g}

["1", "2", "3"]

["4", "5", "6"]

["7", nil, nil]

%w(1 2 3).in_groups_of(2, ' ') {|g| p g}

["1", "2"]

["3", " "]

%w(1 2 3).in_groups_of(2, false) {|g| p g}

["1", "2"]

["3"]

<table>

<% @tasks.in_groups_of(4) do |row_tasks| %>

<tr>

<% for task in row_tasks %>

<td><%= task.name %></td>

<% end %>

</tr>

<% end %>

</table>