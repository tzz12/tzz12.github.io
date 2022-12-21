---
title: "2022-12-21记一次npm\_install报错"
tags: 
category: /日记/2022-12
emoji: "😛"
grammar_cjkRuby: true
---
环境
node 14
node-sass:4.12
报错

``` javascript
gyp verb check python checking for Python executable "python" in the PATH
gyp verb `which` failed Error: not found: python
```
node 与node-sass版本对应
![enter description here](./images/1671587882910.png)
最终解决方法：
降低node版本到与node-sass一致