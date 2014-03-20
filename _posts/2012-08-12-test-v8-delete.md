---
layout: default
title: v8 can not handle delete yet
categories: [技术, 前端]
tags: [v8, delete]
---
##{{ page.title }}
###{{ page.date | date_to_string }}

v8 delete操作存在的这个问题
![有帮助的截图](/assets/images/v8delete.jpeg)
测试地址在这里， http://jsperf.com/test-v8-delete，也可以用下面的代码在node中测试

```javascript
var begin = new Date();
function Foo() {}
Foo.prototype.x = 1;
Foo.prototype.y = 2;
      
//delete Foo.prototype.y;
      
var foo = new Foo();
      
var result = 0;
for (var i = 0; i < 100000; i++) {
    result = result + foo.x;
}
      
var end = new Date();
console.log(end - begin);
```