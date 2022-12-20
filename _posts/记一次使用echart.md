---
title: 记一次使用echart
category: /小书匠/日记/2022-12
emoji: "😙"
grammar_cjkRuby: true
---


使用骨架（[官网](https://echarts.apache.org/handbook/zh/get-started/)）

``` javascript
<div class="echartsBox" id="entity-main" style="width:100%"
></div>
```

``` javascript
const entityCharts = echarts.init(document.getElementById('entity-main'))
//设置option
var option = {}
entityCharts .setOption(option);
```


使用v-show造成echart宽度变成100px
解决方法：使用==this.$nextTick #4CAF50==
``` javascript
this.$nextTick(() => {
  const ChartsDom = document.getElementById('entity-main')
  const autoWidth = ChartsDom.parentNode.clientWidth + 'px'
  this.entityCharts.getDom().style.width = autoWidth
  this.entityCharts.resize()
})
```