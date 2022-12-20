---
title: 获取dom元素宽度
category: /小书匠/日记/2022-12
emoji: "😝"
grammar_cjkRuby: true
---


dom元素

``` javascript
<div ref="ele"></div>
```
宽度
获取宽度（内容宽度+padding）

``` javascript
let width=this.$refs.ele.clientWidth;
```
获取宽度（内容+padding+边框）

``` javascript
let width = this.$refs.ele.offsetWidth;
```
获取元素样式值

``` javascript
let width = window.getComputedStyle(this.$refs.ele).width;
```
获取元素内联样式值（非内联样式无法获取）

``` javascript
let width = this.$refs.ele.style.width;
```