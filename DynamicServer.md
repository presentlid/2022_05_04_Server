# 动态服务器
什么是动态服务器？请求了数据库的就是<strong>动态服务器</strong>，没有请求数据库就是<strong>静态服务器</strong>。

## JS 中模拟请求数据库
``` js
    const fs = require('fs'); // 必写
    const content = fs.readFileSync('文件相对本JS文件的路径'); // 读取文件
    fs.writeFileSync('文件相对本JS文件的路径', `要写进去的文件内容`); // 写文件
```