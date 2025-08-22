---
title: "使用Hexo ECharts标签在文章中嵌入交互式图表"
source: "https://www.mingdao.me/Hexo/hexo-tags-echarts/"
author:
  - "[[明道言文明道，致用，事信，言文]]"
  - "[[明道言文]]"
published: 2020-10-01
created: 2025-08-18
description: "本文说明如何使用本站编写的Hexo EChart Tags ，往文章中嵌入交互式ECharts图表。                               // 基于准备好的dom，初始化echarts实例             var myChart = echarts.init(document.getElementById('echarts740'));             /"
tags:
  - "clippings"
---
> 本文说明如何使用本站编写的Hexo EChart Tags ，往文章中嵌入交互式 [ECharts](http://echarts.apache.org/zh/index.html) 图表。

为了在文章中显示如上所示的交互式ECharts图表，需要使用本站开发的ECharts标签库。

### 下载配置ECharts标签库

由于使用方法简单，本站目前未特别开发专门的Hexo插件。

首先需要下载本站开发的 [ECharts标签库](https://www.mingdao.me/downloads/code/echarts_tags.js) 。

将下载到的 `echarts_tags.js` 直接复制到Hexo站点根目录下的 `scripts` 目录下即可。

然后就可以使用 `{% echarts %}` 标签在md文件中嵌入ECharts可交互图表了。

### ECharts标签源代码

示例数据修改自官方教程 [5 分钟上手 ECharts](https://echarts.apache.org/zh/tutorial.html#5%20%E5%88%86%E9%92%9F%E4%B8%8A%E6%89%8B%20ECharts) 。

```javascript
{% echarts %}

// 指定图表的配置项和数据

var option = {

    title: {

        text: 'ECharts 标签示例'

    },

    tooltip: {},

    legend: {

        data:['销量']

    },

    xAxis: {

        data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]

    },

    yAxis: {},

    series: [{

        name: '销量',

        type: 'bar',

        data: [5, 20, 36, 10, 10, 20]

    }]

};

{% endecharts %}
```

### 分离数据和文章

可以使用 `{% ecr %}` 标签实现数据和文章的分离。以实现数据的共享，也方便日后数据的更新。

把内容如下所示的json格式文件 `sample.json` 放到 `source/data` 目录下。

```json
{

    "title": {

        "text": "ECharts 标签示例"

    },

    "tooltip": {},

    "legend": {

        "data":["销量"]

    },

    "xAxis": {

        "data": ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]

    },

    "yAxis": {},

    "series": [{

        "name": "销量",

        "type": "bar",

        "data": [5, 20, 36, 10, 10, 20]

    }]

}
```

在 `md` 文件中通过 `{% ecr %}` 来展示图表，如下所示，注意json文件名称只需要使用 `source/data` 相对文件路径即可。

```markdown
{% ecr sample.json %}
```

图表显示效果如下：

1 评论

![](https://gravatar.loli.net/avatar/553f9e0f719254abcdf5b9bf51bc358c?d=wavatar&v=1.4.14)

2022-05-24 回复

e

Powered By [Valine](https://valine.js.org/)  
v1.4.14