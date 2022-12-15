---
title: dom-to-image
tags: 'js前端截图'
category: /小书匠/日记/2022-12
emoji: "小"
grammar_cjkRuby: true
---
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
```
  function toPng(node, options) {
    return draw(node, options || {}).then(function (canvas) {
      return canvas.toDataURL();
    });
  }
```
实现的逻辑是：通过==draw #4CAF50==方法将dom转化为==canvas #4CAF50==，然后通过canvas方式获取图片地址