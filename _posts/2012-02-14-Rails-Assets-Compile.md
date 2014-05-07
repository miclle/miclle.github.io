---
layout: post
title:  "Rails Assets Compile"
date:   2012-02-14 17:20:38
categories: [Ruby On Rails]
tags: [Assets, Compile]
---

By default Rails assumes that you have your files precompiled in the production environment, if you want use live compiling (compile your assets during runtime) in production you must set the

**config.assets.compile to true**

.# config/environments/production.rb...config.assets.compile=true...You can use this option to fallback to Sprockets when you are using precompiled assets but there are any missing precompiled files.If 

config.assets.compile option is set to false and there are missing precompiled files you will get an "AssetNoPrecompiledError" indicating the name of the missing file.____________________________________________________You will get better performance in production if you set config.assets.compile to false in production.rb and precompile your assets. You can precompile with this rake task:bundleexecrake assets:precompileIf you are using Capistrano, version 2.8.0 has a recipe to handle this at deploy time. For more info, see the "In Production" section of the Asset Pipeline Guide: 

[http://guides.rubyonrails.org/asset_pipeline.html](http://guides.rubyonrails.org/asset_pipeline.html)[http://stackoverflow.com/questions/7275636/rails-3-1-0-actionviewtemplateerrror-application-css-isnt-precompiled](http://stackoverflow.com/questions/7275636/rails-3-1-0-actionviewtemplateerrror-application-css-isnt-precompiled)