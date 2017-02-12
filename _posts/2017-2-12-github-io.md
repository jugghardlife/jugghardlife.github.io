---
layout: post
title: github.io
---
2017年2月11日初次在github上建立自己的微博，并且在今天初次更新微博，就总结下自己建github微博从中的体会。

## 抄微博

### 第一步

到 Github 上创建 yourusername.github.io （注意是 .io 不要写 .com）这个仓库

### 第二步

拷贝 [ https://github.com/happypeter/happypeter.github.com ] 这里的所有的文件，上传到你新建的这个仓库的 master 分支

### 第三步

到 yourusername.github.io 这个域名下，就可以看到你自己的博客了，但是现在看起来肯定跟peter的 [ http://happypeter.github.io ] 是一样的。

## 改微博

### 学习Jekyll的原理了
想要知道从[https://github.com/happypeter/happypeter.github.com]克隆下来的代码的作用，可以通过这节视频[http://www.haoduoshipin.com/v/113.html]进行了解。

### 个人体会

jekyll的一大作用是，利用markdown解析器可以把写成的markdown文本转变成html。

#### markdown 解析器
默认的markdown转换器是
```
markdown: kramdown
```

默认配置的后缀下面列出的几种

```
markdown_ext:"markdown,mkdown,mkdn,mkd,md"
```
#### 头设置

正文开始之前，一定要加上下面这样的"头设置"(jekyll要求的)。

```
---
layout: xxx
title: xxx
---
```
没有具体内容也得加上

```
---
---
```

#### 布局文件

布局文件_layouts,创建一个_layouts/default.html,布局文件的名字可以任意取，一般都取default.html，在default.html中就放一个页面的骨架，其中关键是在里面添加｛｛ content ｝｝ markdown文件中的信息填充到content中

在_config.yml文件中设置

```
defaults:
  -
    values:
      layout: "default"

```
相当于为每个页面都默认设置了布局文件。但是要注意，即使有了这个设置，front matter 部分也不能完全删除。没有内容要设置，也要给一个空的 front matter
```
---
---
```

另外，个别页面如果不用这个 layout 文件，可以到 front matter 中去覆盖，例如

```
---
layout: post
---
```

这样这个页面就使用 post.html 做布局文件了。

#### 片段文件

片段文件_includes,创建一个_includes/xxx.html,写后想在哪个页面中使用就写
```
｛　% inlude xxx.html　｝
```

#### 代码高亮
想使用高亮的效果应该包裹在下面的标签中:

```
｛　% highlight console %　｝
$ git clone ...
｛　% endhighlight %　｝
```
上面console在html中就转换为class='language-console'的标签了。

1.
可以在_config.yml中，添加
```
highlighter:pygments
```

2.
也可自己找到仔细喜欢的css样式进行覆盖，在html中link 导入就可以啦。

3.
jekyll默认有sass支持的，可以新建一个目录_sass,把需要的sass下载下来，然后创建css/main.scss,然后在其中添加下面代码
```
---
# Only the main Sass file needs front matter (the dashes are enough)
---
@charset "utf-8";

// Import partials from `sass_dir` (defaults to `_sass`)
@Import
 "下载的sass",
 "下载的sass"
;
```
作用是把下载的sass都导入进来，然后在想添加的页面中淡入<link rel="stylesheet" href="css/main.css">

#### 自带变量

变量的好处，可以在多个地方取出这个值。
```
---
title:test
---
```
取出变量的方法
```
｛｛　page.title　｝｝
```
以上是今天在创建githun.io中的体会，体会很浅薄，以后要有进一步理解，会不断完善此条微博的。
