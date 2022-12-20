---
title: vue中三种for的用法
category: /小书匠/日记/2022-12
emoji: ""
grammar_cjkRuby: true
---
第一种：普通用法：

``` javascript
for(let i = 0;i<xx.length;i++){
//xx是数组
//获取数组中某个值
let item = xx[i]
}
```
第二种：for..in..
遍历数组/对象（一般用来遍历==对象 #4CAF50==）

``` javascript
for(let i in xx){
//i 是数组xx的索引
}
```
说明：

 - 遍历数组：结果是key，数组index
 - 遍历对象：结果是key，对象的键
 - 遍历字符串：结果是key，字符串的index（同数组）

第三种： for..of...
遍历数组
``` javascript
for(let item of xx){
//item直接是数组中的对象
}
```
说明：

 - 遍历数组：结果是value，数组项值
