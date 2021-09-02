---
title: js获取下周一日期
date: 2020-03-05
updated: 2020-03-05
description: ""
tags: '小知识'
---
```
    // 获取下周一日期
    var date = new Date();
        date.setDate(date.getDate() + (8 - date.getDay()));
    var y = date.getFullYear(); 
    var m = date.getMonth() + 1; 
    var d = date.getDate();
    var mvar = '',dvar = '';
    m < 10 ? mvar = '0' + m : mvar = m;
    d < 10 ? dvar = '0' + d : dvar = d;
    console.log(y + "-" + mvar + '-' + dvar)
```
