---
layout: post
title: 网页重构的html规范
tags: [ Standard , html  ]
category: Frontend
description: 规范是前端工程师评判代码的一杆重要标尺，本文总结了一套的html规范，供各位看客取用。
---

#html代码规范：
###html基础设施
+ 如我们所知不同的Doctype声明，将会触发浏览器不同的渲染模式，主要分为遵循W3C规范的标准模式和[怪异模式](http://zh.wikipedia.org/wiki/%E6%80%AA%E5%BC%82%E6%A8%A1%E5%BC%8F)。而因为html5的流行，我们不需要去管因为遗留下原因的不同dtd，主需要统一的在文件的顶格开始声明"<!DOCTYPE html>"。
+ 必须申明文档的编码charset，且与文件本身编码保持一致，推荐使用UTF-8编码<meta charset="utf-8"/>。
+ 根据页面内容和需求填写适当的keywords和description。
+ 页面title是极为重要的不可缺少的一项。
+ 对于兼容性的处理可以考虑使用[IE注释法](http://www.veryhuo.com/a/view/50853.html)加上class锚点
<pre>
&lt;!DOCTYPE html&gt;
&lt;html&gt; 
&lt;head&gt;
&lt;meta charset="utf-8"/&gt; 
&lt;title&gt;文章标题&lt;/title&gt; 
&lt;meta name="keywords" content=""/&gt; 
&lt;meta name="description" content=""/&gt; 
&lt;meta name="viewport" content="width=device-width"/&gt; 
&lt;link rel="stylesheet" href="css/style.css"/&gt; 
&lt;link rel="shortcut icon" href="img/favicon.ico"/&gt; 
&lt;link rel="apple-touch-icon" href="img/touchicon.png"/&gt; 
&lt;/head&gt; 
&lt;body&gt; 
 
&lt;/body&gt; 
&lt;/html&gt;
</pre>
###结构、表现、行为三者分离，避免内联
+ 使用link将css文件引入，并置于head中。
+ 使用script将js文件引入，并置于body底部。
###保持良好的简洁的树形结构
+ 每一个块级元素都另起一行，每一行都使用Tab缩进对齐（head和body的子元素不需要缩进）。删除冗余的行尾的空格。
+ 使用4个空格代替1个Tab（大多数编辑器中可设置）。
+ 你也可以在大的模块之间用空行隔开，使模块更清晰。
+ 模块首尾使用注释标示
<pre>
&lt;body&gt; 
&lt;!-- S 侧栏内容区 --&gt; 
&lt;div class="m_side"&gt; 
    &lt;div class="side"&gt; 
        &lt;div class="sidein"&gt; 
            &lt;!-- 热门标签 --&gt; 
            &lt;div class="sideblk"&gt; 
                &lt;div class="m-hd3"&gt;&lt;h3 class="tit"&gt;热门标签&lt;/h3&gt; &lt;/div&gt; 
                ... 
            &lt;/div&gt; 
 
            &lt;!-- 最热TOP5 --&gt; 
            &lt;div class="sideblk"&gt; 
                &lt;div class="m-hd3"&gt;&lt;h3 class="tit"&gt;最热TOP5&lt;/h3&gt; &lt;a href="#" class="s-fc02 f-fr"&gt;更多&raquo;&lt;/a&gt;&lt;/div&gt; 
                ... 
            &lt;/div&gt; 
        &lt;/div&gt; 
    &lt;/div&gt; 
&lt;/div&gt; 
&lt;!-- E 侧栏内容区 --&gt; 
&lt;/body&gt; 
</pre>
###另外，请做到以下几点
+ 结构上如果可以并列书写，就不要嵌套。<br>
如果可以写成&lt;div&gt;&lt;/div&gt;&lt;div&gt;&lt;/div&gt;那么就不要写成&lt;div&gt;&lt;div&gt;&lt;/div&gt;&lt;/div&gt;
+ 如果结构已经可以满足视觉和语义的要求，那么就不要有额外的冗余的结构。<br>
比如&lt;div&gt;&lt;h2&gt;&lt;/h2&gt;&lt;/div&gt;已经能满足要求，那么就不要再写成&lt;div&gt;&lt;div&gt;&lt;h2&gt;&lt;/h2&gt;&lt;/div&gt;&lt;/div&gt;
+ 一个标签上引用的className不要过多，越少越好。<br>
比如不要出现这种情况：&lt;div class="class1 class2 class3 class4"&gt;&lt;/div&gt;
+ 对于一个语义化的内部标签，应尽量避免使用className。<br>
比如在这样一个列表中，li标签中的itm应去除：&lt;ul class="m-help"&gt;&lt;li class="itm"&gt;&lt;/li&gt;&lt;li class="itm"&gt;&lt;/li>&lt;/ul&gt;
###严格的嵌套
+ 尽可能以最严格的xhtml strict标准来嵌套，比如内联元素不能包含块级元素等等。
+ 正确闭合标签且必须闭合。
###严格的属性
+ 属性和值全部小写，每个属性都必须有一个值，每个值必须加双引号。
+ 没有值的属性必须使用自己的名称做为值（checked、disabled、readonly、selected等等）。
+ 可以省略style标签和script标签的type属性。
###内容类型决定使用的语义标签
+ 在网页中某种类型的内容必定需要某种特定的HTML标签来承载，也就是我们常常提到的根据你的内容语义化HTML结构。
###加强“资源型”内容的可访问性和可用性
+ 在资源型的内容上加入描述文案，比如给img添加alt属性，在audio内加入文案和链接等等。
###加强“不可见”内容的可访问性
+ 背景图上的文字应该同时写在html中，并使用css使其不可见，有利于搜索引擎抓取你的内容，也可以在css失效的情况下看到内容。
###适当使用实体
+ 以实体代替与HTML语法相同的字符，避免浏览解析错误。<br>
<table class="table table-bordered table-hover"> 
    <caption>常用HTML字符实体（建议使用实体）：</caption> 
    <thead> 
        <tr><th>字符</th><th>名称</th><th>实体名</th><th>实体数</th></tr> 
    </thead> 
    <tbody> 
        <tr><td>&quot;</td><td>双引号</td><td>&amp;quot;</td><td>&amp;#34;</td></tr> 
        <tr><td>&amp;</td><td>&amp;符</td><td>&amp;amp;</td><td>&amp;#38;</td></tr> 
        <tr><td>&lt;</td><td>左尖括号（小于号）</td><td>&amp;lt;</td><td>&amp;#60;</td></tr> 
        <tr><td>&gt;</td><td>右尖括号（大于号）</td><td>&amp;gt;</td><td>&amp;#62;</td></tr> 
        <tr><td>&nbsp;</td><td>空格</td><td>&amp;nbsp;</td><td>&amp;#160;</td></tr> 
    </tbody> 
</table> 
<table class="table table-bordered table-hover"> 
    <caption>常用特殊字符实体（不建议使用实体）：</caption> 
    <thead> 
        <tr><th>字符</th><th>名称</th><th>实体名</th><th>实体数</th></tr> 
    </thead> 
    <tbody> 
        <tr><td>&yen;</td><td>元</td><td>&amp;yen;</td><td>&amp;#165;</td></tr> 
        <tr><td>&brvbar;</td><td>断竖线</td><td>&amp;brvbar;</td><td>&amp;#166;</td></tr> 
        <tr><td>&copy;</td><td>版权</td><td>&amp;copy;</td><td>&amp;#169;</td></tr> 
        <tr><td>&reg;</td><td>注册商标R</td><td>&amp;reg;</td><td>&amp;#174;</td></tr> 
        <tr><td>&trade;</td><td>商标TM</td><td>&amp;trade;</td><td>&amp;#8482;</td></tr> 
        <tr><td>&middot;</td><td>间隔符</td><td>&amp;middot;</td><td>&amp;#183;</td></tr> 
        <tr><td>&laquo;</td><td>左双尖括号</td><td>&amp;laquo;</td><td>&amp;#171;</td></tr> 
        <tr><td>&raquo;</td><td>右双尖括号</td><td>&amp;raquo;</td><td>&amp;#187;</td></tr> 
        <tr><td>&deg;</td><td>度</td><td>&amp;deg;</td><td>&amp;#176;</td></tr> 
        <tr><td>&times;</td><td>乘</td><td>&amp;times;</td><td>&amp;#215;</td></tr> 
        <tr><td>&divide;</td><td>除</td><td>&amp;divide;</td><td>&amp;#247;</td></tr> 
        <tr><td>&permil;</td><td>千分比</td><td>&amp;permil;</td><td>&amp;#8240;</td></tr> 
    </tbody> 
</table> 