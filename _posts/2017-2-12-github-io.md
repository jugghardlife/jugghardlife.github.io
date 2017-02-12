---
layout: post
title: github.io
---
2017年2月11日初次在github上建立自己的微博，并且在今天初次更新微博，就总结下自己建github微博从中的体会。

#抄微博

##第一步
到 Github 上创建 yourusername.github.io （注意是 .io 不要写 .com）这个仓库
##第二步
拷贝 https://github.com/happypeter/happypeter.github.com 这里的所有的文件，上传到你新建的这个仓库的 master 分支
##第三步
到 yourusername.github.io 这个域名下，就可以看到你自己的博客了，但是现在看起来肯定跟peter的 http://happypeter.github.io 是一样的。

#改微博

##学习Jekyll的原理了
想要知道从[https://github.com/happypeter/happypeter.github.com]克隆下来的代码的作用，可以通过这节视频[http://www.haoduoshipin.com/v/113.html]进行了解。

##个人体会

jekyll的一大作用是，利用markdown解析器可以把写成的markdown文本转变成html。

###markdown 解析器
默认的markdown转换器是
```
markdown: kramdown
```

默认配置的后缀下面列出的几种

```
markdown_ext:"markdown,mkdown,mkdn,mkd,md"
```
