---
location: https://www.mingdao.me/Hexo/hexo-tags-echarts/
---
[使用Hexo ECharts标签在文章中嵌入交互式图表 | 明道学苑](https://www.mingdao.me/Hexo/hexo-tags-echarts/)
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
