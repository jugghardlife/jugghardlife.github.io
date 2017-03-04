---
layout: post
title: body,documentElement
---

### body与documentElement的区别。

1. 网页中获取滚动条卷去部分的高度，可以通过 document.body.scrollTop 来获取，比如使div跟着滚动条滚动：

```
<div id="div" style="width:100px;height:100px;
background:#ccc;position:absolute;"></div>
window.onscroll = function ()
  {
    var div = document.getElementById("div");
    div.style.top = document.body.scrollTop + "px";
  }
```

2. 运行后没有达到预期效果，输出 document.body.scrollTop 的值一看，一直都是 0。一翻折腾，原来是 DTD 的问题，要是页面直接用 <html> 开头的话就没有问题了。但是要符合 web 标准，DTD 当然是不能少的。如果有 DTD 时用，那就用 document.documentElement.scrollTop 代替 document.body.scrollTop 就可以了。

```
window.onscroll = function ()
  {
      var oFix = document.getElementById("divfix");
      oFix.style.top = document.documentElement.scrollTop + "px";
  }
```

### DTD相关说明：

1. 页面具有 DTD，或者说指定了 DOCTYPE 时，使用 document.documentElement。页面不具有 DTD，或者说没有指定了 DOCTYPE，时，使用 document.body。在 IE 和 Firefox 中均是如此。为了兼容，不管有没有 DTD，可以使用如下代码：

```
var scrollTop = window.pageYOffset  //用于FF
                || document.documentElement.scrollTop  
                || document.body.scrollTop  
                || 0;
```
### documentElement 和 body 相关说明：

body是DOM对象里的body子节点，即 <body> 标签；
documentElement 是整个节点树的根节点root，即<html> 标签；
DOM把层次中的每一个对象都称之为节点，就是一个层次结构，你可以理解为一个树形结构，就像我们的目录一样，一个根目录，根目录下有子目录，子目录下还有子目录。以HTML超文本标记语言为例：整个文档的一个根就是,在DOM中可以使用document.documentElement来访问它，它就是整个节点树的根节点。而body是子节点，要访问到body标签，在脚本中应该写：document.body。

在设计页面时可能经常会用到固定层的位置，这就需要获取一些html对象的坐标以更灵活的设置目标层的坐标，这里可能就会用到document.body.scrollTop等属性，但是此属性在xhtml标准网页或者更简单的说是带<!DOCTYPE ..>标签的页面里得到的结果是0，如果不要此标签则一切正常，那么在xhtml页面怎么获得body的坐标呢，当然有办法-使用document.documentElement来取代document.body,可以这样写
例：

```
var top = document.documentElement.scrollTop ||
document.body.scrollTop;
```

在JavaScript里||是个好东西，除了能用在if等条件判断里，还能用在变量赋值上。那么上例等同于下例。
例：

```
var top = document.documentElement.scrollTop ?
document.documentElement.scrollTop : document.body.scrollTop;
```
这么写可以得到很好的兼容性。

相反，如果不做声明的话，document.documentElement.scrollTop反而会显示为0。
