## 问题描述

今天在搭建自己博客的时候，接入gitalk系统，但是在登录后显示`Error: Validation Failed` 错误。


## 问题分析

经过google可以知道是文章的标题过长，而gitalk的每个文章的id是由文章标题确定的，需要保持唯一性，且不能超过50个字符。


## 解决办法

我们可以将id经过md5处理，处理后的id保持在32个字符，且唯一。

首先在博客codes的`_includes`目录下，找到`gitalk.html`文件，然后打开文件后修改如下：

``` html
{% if site.gitalk.clientID %}
<div class="comments">
    <div id="gitalk-container"></div>
    <!--1、新增md5.min.js-->
    <script src="https://cdn.bootcss.com/blueimp-md5/2.13.0/js/md5.min.js"></script>
    <script>
        const gitalk = new Gitalk({
          clientID: "{{ site.gitalk.clientID }}",
          clientSecret: "{{ site.gitalk.clientSecret }}",
          repo: "{{ site.gitalk.repo }}",
          owner: "{{ site.gitalk.owner }}",
          admin: ["{{ site.gitalk.owner }}"],
            // 2、将文章名用md5处理
          id: md5(window.location.pathname),      // Ensure uniqueness and length less than 50
          //  id: window.location.pathname,      // Ensure uniqueness and length less than 50
          distractionFreeMode: false,  // Facebook-like distraction free mode
          title: "{{ page.title }}",
          language: "zh-CN",

        })
        
        gitalk.render('gitalk-container')
    </script>
</div>
{% endif %}
```

搞定！

