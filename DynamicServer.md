# 动态服务器
什么是动态服务器？请求了数据库的就是<strong>动态服务器</strong>，没有请求数据库就是<strong>静态服务器</strong>。

## JS 中模拟请求数据库
``` js
    const fs = require('fs'); // 必写
    const content = fs.readFileSync('文件相对本JS文件的路径'); // 读取文件
    fs.writeFileSync('文件相对本JS文件的路径', `要写进去的文件内容`); // 写文件
```

## Cookie
* cookie 是服务器下发给浏览器的一段字符串
* 浏览器必须保存这个 cookie (除非用户删除)
* 之后发起<strong>相同二级域名</strong>请求时，浏览器必须附上 cookie

<strong>前端不要设置 cookie，cookie 是后台的事情！如果前端可以搞 cookie，那么登录信息用户就可以自己改了。</strong>

## cookie 安全
如果 cookie 不加工，那么用户可以随意篡改。以下有两种思路来改善问题：
1. 加密
    * 加密通讯，但有安全漏洞，比如别人窃取了你的加密id，别人不需要知道加密内容是什么，直接拿来用就得了。
    * 加密通讯升级：JWT
2. 把信息隐藏在服务器
    * 服务器拿到用户信息后，保存在session里，并且用随机数赋值id
    * 把随机id给浏览器，之后浏览器和服务器通过这个随机id通信
    * session(会话)是个文件，不能放内存里，因为内存断电会被清空

方法2对比方法1：随机id具有更短的时效，基本不存在加密通讯的安全漏洞问题，因为用户重新登录会获得新的随机id，或者后台每隔一段时间就重置id随机数。
