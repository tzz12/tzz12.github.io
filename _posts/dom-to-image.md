---
title: dom-to-image
tags: 'js前端截图'
category: /小书匠/日记/2022-12
emoji: "小"
grammar_cjkRuby: true
---
[原理](https://www.jianshu.com/p/1628d41ec1ff)
安装

``` javascript
npm install dom-to-image
```
引入

``` javascript
import domtoimage from 'dom-to-image';
```

提供的Api介绍
```
toSvg
toPng
toJpeg
toBlob
toPixelData
```
顾名思义，都是将Dom节点转成svg、png、jpeg、blob以及PixelData格式

代码解读
toPng
```javascript
  function toPng(node, options) {
    return draw(node, options || {}).then(function (canvas) {
      return canvas.toDataURL();
    });
  }
```
实现的逻辑是：通过==draw #4CAF50==方法将dom转化为==canvas #4CAF50==，然后通过canvas方式获取图片地址
**注意：**
对于要转换的dom节点需要是==可见的 #4CAF50==，即display: none等设置不可见的样式会导致出图失败
若是目标node的子元素中包含display: none，可以使用filter属性过滤下

简单示例：

``` javascript
let node = document.getElementById('test');
let that = this
domtoimage.toPng(node)
	.then(function (dataUrl) {
		//console.log(dataUrl)
		that.dataUrl = dataUrl
	})
	.catch(function (error) {
		console.error('生成失败', error);
	});
```
可以添加参数

``` javascript
domtoimage.toJpeg(node, {
   width: 330,
    height: 155,
    cacheBust: true,
    style: {
      margin: 0,
      background: '#fff',
    }
  })

```

[属性]([dom-to-image](8c4665ef-b213-40fc-a5b7-6a4cce63980f#xsj_1671093263256))
filter

``` javascript
createImage() {
    let node = document.getElementById('test');
    let that = this
    domtoimage.toPng(node, { filter: that.filterTag })
        .then(function (dataUrl) {
            console.log(dataUrl)
            that.dataUrl = dataUrl
        })
        .catch(function (error) {
            console.error('生成失败', error);
        });
},
filterTag(node) {
    console.log(node, node.tagName)
    return node.tagName == 'IMG'
}
```
bgcolor

``` javascript
domtoimage.toPng(node, { bgcolor: '#ddd' })
 .then(function (dataUrl) {
     console.log(dataUrl)
     that.dataUrl = dataUrl
     // FileSaver.saveAs(dataUrl, 'a.png');
 })
 .catch(function (error) {
     console.error('生成失败', error);
 });

```
下载压缩的图片

``` javascript
domtoimage.toJpeg(document.getElementById('my-node'), { quality: 0.95 })
    .then(function (dataUrl) {
        var link = document.createElement('a');
        link.download = 'my-image-name.jpeg';
        link.href = dataUrl;
        link.click();
    });

```

参考：
https://blog.csdn.net/HYeeee/article/details/124878950