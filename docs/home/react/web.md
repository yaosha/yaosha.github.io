---
title: web
---

{% capture article %}

## CSS

1. 盒模型

当对一个文档进行布局的时候，浏览器渲染引擎会根据CSS-Box模型将所有元素表示为一个矩形盒子。这个模型描述了元素所占空间的内容。每个盒子有四个边：外边距边, 边框边, 内填充边 与 内容边。 
内容区域是包含元素真实内容的区域。
内边距区域延伸到包围padding的边框。
边框区域是包含边框的区域，扩展了内边距区域。
外边距区域用空白区域扩展边框区域，以分开相邻的元素。

box-sizing 属性用于更改用于计算元素宽度和高度的默认的 CSS 盒子模型。
* content-box  默认值，标准盒子模型。 width 与 height 只包括内容的宽和高， 不包括边框（border），内边距（padding），外边距（margin）。
* border-box  width 和 height 属性包括内容，内边距和边框，但不包括外边距。

2.






{% endcapture %}

{% include templates/home.md %}
