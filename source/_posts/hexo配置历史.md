---
title: hexo配置历史
date: 2019-07-14 22:55:40
tags: hexo
---
1. ### 主题配置
    1. `_config.yml`中,配置主题为`theme: next`
    2. 采用Hexo方式配置主题：
    {% codeblock lang:yaml %}
    theme_config:
    scheme: Gemini
    menu:
        home: / || home
        about: /about/ || user
        tags: /tags/ || tags
        #categories: /categories/ || th
        archives: /archives/ || archive
        # Social Links
    {% endcodeblock %}
    方便升级主题
    {% blockquote %}
    使用这一方式，你的全部配置都将置于 hexo 主要配置文件中（hexo/_config.yml），并且不需要修改 next/_config.yml，或者创建什么其他的文件。但是所有的主题选项必须放置在 theme_config 后，并全部增加两个空格的缩进。
    {% endblockquote %}
2. ### 开启搜索
    1. 安装`npm install hexo-generator-searchdb --save`

    2. 修改站点配置`_config.yml`

    {% codeblock lang:yaml %}
    search:
      path: search.xml
      field: post
      format: html
      limit: 10000
    {% endcodeblock %}

    3. 修改主题配置
    
    {% codeblock lang:yaml %}
    local_search:
      enable: true
    {% endcodeblock %}
3. ### 开启侧边栏头像
  1. 上传文件到source/uploads文件夹(如果没有该文件夹则手动创建)
  2. 修改主题配置
   {% codeblock lang:yaml %}
    avatar:
      # In theme directory (source/images): /images/avatar.gif
      # In site directory (source/uploads): /uploads/avatar.gif
      # You can also use other linking images.
      url: /uploads/avatar.jpg
      # If true, the avatar would be dispalyed in circle.
      rounded: true
      # If true, the avatar would be rotated with the cursor.
      rotated: false
    {% endcodeblock %}