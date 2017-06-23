---
title: 'Jekyll Tips'
onlineImg: http://7xle3b.com1.z0.glb.clouddn.com/Jekyll.png
ref: about
image: true
time: 1
category: Tech
tags: [Jekyll]
--- 

Jekyll部署到Github之后，有时候会提示你Page Build Failed，但是却没有给出具体失败的原因。
很可能你本地使用`Bundle exec jekyll server`命令运行，一切正常。这时候要怎么排查问题呢？

你可以使用

    jekyll build --safe

命令来查看具体错误的原因，例如，我当时的问题为：
   
    WARN: Unresolved specs during Gem::Specification.reset:
          jekyll-watch (~> 1.1)
          rouge (~> 1.7)
    WARN: Clearing out unresolved specs.
    Please report a bug if this causes problems.
    Configuration file: /Users/apple/GitHub/Yogayu.github.io/Yogayu.github.io/_config.yml
                Source: /Users/apple/GitHub/Yogayu.github.io/Yogayu.github.io
           Destination: /Users/apple/GitHub/Yogayu.github.io/Yogayu.github.io/_site
     Incremental build: disabled. Enable with --incremental
          Generating...
      Liquid Exception: Liquid syntax error (line 50): Unknown tag 'feed_meta' in /Users/apple/GitHub/Yogayu.github.io/Yogayu.github.io/_includes/core/wikiHead.html, included in /_layouts/wikiDefault.html
    jekyll 3.4.3 | Error:  Liquid syntax error (line 50): Unknown tag 'feed_meta'

也就是在/Users/apple/GitHub/Yogayu.github.io/Yogayu.github.io/_includes/core/wikiHead.html，在此目录的文件wikiHead中，使用了没有定义的表情fedd_meta。

这样一来，问题就能很好的定位到了。