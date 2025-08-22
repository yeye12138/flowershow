---
title: "Hexo如何增加站内文章链接"
source: "https://www.mingdao.me/Hexo/hexo-link-post/?streaming_load=1#anchor-sample"
author:
  - "[[明道言文明道，致用，事信，言文]]"
  - "[[明道言文]]"
published: 2021-03-01
created: 2025-08-18
description: "本文说明Hexo如何增加站内文章链接。"
tags:
  - "clippings"
---
> Hexo官方网站上没有明确说明如何增加站内文章链接，本文说明如何给文章增加站内链接。

### 使用markdown的链接语法

使用markdown的语法指定url创建站内链接，有绝对地址和相对地址两种方式，绝对地址与相对地址的区别在于是否以 `/` 开头：

#### 使用绝对地址

代码如下：

```md
<!-- 绝对地址 -->

[Ubuntu Linux上启用root账户](/Ubuntu/ubuntu-enable-root)
```

> 示例中， `ubuntu-enable-root` 使用的是文章对应的md文件名，使用hexo n创建post时，空格会转换为中划线-。 `Ubuntu` 是本站为了文章管理方便在 `_posts` 目录下增加的子目录， `ubuntu-enable-root.md` 位于 `_posts/Ubuntu` 目录下。

结果如下：

[Ubuntu Linux上启用root账户](https://www.mingdao.me/Ubuntu/ubuntu-enable-root)

Hexo对绝对抵制和相对地址的处理方式是不一样的。对于绝对地址 `/Ubuntu/ubuntu-enable-root` ，生成的目标url不会变化。

#### 使用相对地址

代码如下：

```md
<!-- 相对地址 -->

[Ubuntu Linux上启用root账户](Ubuntu/ubuntu-enable-root)
```

对于相对地址 `Ubuntu/ubuntu-enable-root` ，生成的目标URL会叠加文章的的URL，结果是 `/Hexo/hexo-link-post/Ubuntu/ubuntu-enable-root/` ，这显然不是期望的结果。但是如果是文章内的锚点链接，使用这种方式非常合适。

代码如下：

```md
<!-- 文章内锚点链接 -->

[anchor sample](#anchor-sample)
```

结果如下：  
[anchor sample](https://www.mingdao.me/Hexo/hexo-link-post/?streaming_load=1#anchor-sample)

生成的URL可以正确的跳转到文章内的锚点。注意，标题中的空格用 `-` 代替。

### 使用post\_link标签

由于Hexo文章的URL规则是可以配置的，在 `_config.yml` 中可以配置URL自动添加日期、目录等信息。如果使用markdown语法的链接规则多有不便，一方面需要知道目标URL，一方面如果规则修改或者站点迁移，对应的内容需要修改。

好在Hexo提供了 `post_link` 标签解决这个问题。

代码如下：

```md
{% post_link Ubuntu/ubuntu-enable-root 'Ubuntu Linux上启用root账户' %}
```

> 示例中， `ubuntu-enable-root` 使用的是文章对应的md文件名，使用hexo n创建post时，空格会转换为中划线-。 `Ubuntu` 是本站为了文章管理方便在 `_posts` 目录下增加的子目录， `ubuntu-enable-root.md` 位于 `_posts/Ubuntu` 目录下。

结果如下：

[Ubuntu Linux上启用root账户](https://www.mingdao.me/Ubuntu/ubuntu-enable-root/ "Ubuntu Linux上启用root账户")

这样的链接会自动适配 `_config.yml` 中的文章URL规则。

### 小结

对比markdown语法和 `post_link` 标签，推荐在文章链接到站内文章时优先使用 `post_link` ，链接到文章内锚点时优先使用markdown语法。

### anchor sample

文章内锚点跳转示例

1 评论

![](https://gravatar.loli.net/avatar/553f9e0f719254abcdf5b9bf51bc358c?d=wavatar&v=1.4.14)

2022-05-24 回复

e

![](https://gravatar.loli.net/avatar/d41d8cd98f00b204e9800998ecf8427e?d=wavatar&v=1.4.14)

2024-02-21 回复

[@pHqghUme](https://www.mingdao.me/Hexo/hexo-link-post/?streaming_load=1#628cb25185522162b911e9c1) , 本来想转next主题的，但是好多篇文章都用了butterfly的标签语法，生成会报错…不改了哈哈哈。Halo太占内存，Wordpress太慢，继续用Hexo。

Powered By [Valine](https://valine.js.org/)  
v1.4.14