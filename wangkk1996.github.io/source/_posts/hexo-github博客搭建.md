---
title: hexo+github博客搭建
date: 2018-09-08 14:23:18
tags: [git, hexo]
categories: 日常瞎玩
---
刚开学没事干，所以想着来搭个博客吧。也是为了激励自己能够养成及时总结的习惯。

hexo+github的博客搭建教程网络上很多，我主要搜了知乎的这一篇，讲得很详细：<font color=blue>[GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)</font>
此外这个作者的汇总做的也不错：[Hexo+GithubPages&CodingPages搭建自己的个人博客](http://jmyblog.top/Hexo-GithubPages-CodingPages%E6%90%AD%E5%BB%BA%E8%87%AA%E5%B7%B1%E7%9A%84%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)
还有这个作者的汇总：[我的个人博客之旅：从jekyll到hexo](https://wordzzzz.github.io/2018/01/10/HEXO/)

<!--more-->

## 设置多个tags以及categories
在写这个blog的时候还发现，如果直接在tags后面写多个tags会显示成一个，这是不行的。
这里提供了解决方法：[hexo搭建博客--给文章添加多个tag或category](http://www.saberismywife.com/2016/06/28/hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2-%E7%BB%99%E6%96%87%E7%AB%A0%E6%B7%BB%E5%8A%A0%E5%A4%9A%E4%B8%AAtags%E6%88%96category/)
注意这里的categories是直接显示的侧边栏。

***

以下是一些常用个性化设置：
## 修改文本链接样式：
链接文本改为蓝色，鼠标划过时文字颜色加深：
找到文件 themes\next\source\css\_custom\custom.styl ，添加如下 css 样式：
```cmd
.post-body p a {
  color: #0593d3;
  border-bottom: none;
  &:hover {
    color: #0477ab;
  }
}
```

## 在侧边栏添加tags：
新建一个页面，命名为 tags：
```cmd
hexo new page tags
```
这会在blog的根目录的source下生成一个tags文件夹，文件夹里面带了一个index.md
点进去，修改：
```
---
title: tags
date: 2018-09-08 15:23:35
type: "tags"
---
```
注意不要忘记在冒号之后打半角空格

## 增加搜索框

### 以下是网络上的方法，但是我尝试了一下没啥用= =
首先安装hexo-generator-searchdb插件(在blog的根目录下)
```
npm install hexo-generator-searchdb --save
```
接着，找到站点配置的_config.yml文件，在任意位置添加：
```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```
### 以下是next主题配置自带的功能：
在next的_config.yml文件夹下，找到“local_search”这一栏，把默认的false改为“auto"(自动匹配)或者”manual"(手动匹配)即可。
```
local_search:
  enable: auto
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1
```

## 控制预览字数/博文缩略显示
* 在想要断页的地方添加：`<!--more-->`，可以精确控制字数；
* 或者在next的_config.yml文件中，找到`auto_excerpt`项，然后把底下的false改为true。这样可以控制每篇blog都显示相同的字数。


