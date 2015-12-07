---
layout: default
title:  "node start"
date:   2014-12-07 20:51:22
categories: jekyll 
---

# node start

看到node start让我首先想起了npm start，通过这个也看出我的基础实在不劳。想起了《三傻》，主演随便的写了他朋友的名字，标题只想表达，又要学node了，同时博客记录下来。

```javascript
    // app.js

    // Load the built-in 'http' module.
    var http = require('http');
    
    // Create an http.Server object, and provide a callback that fires after 'request' events.
    var server = http.createServer(function (request, response)     {
            // Respond to the http request with "Hello World" and a basic header.
            response.writeHead(200, {'Content-Type': 'text/plain'});
            response.end('Hello World!\n');
        });
    
    // Try retrieving a port from an environment variable, otherwise fallback to 8080.
        var port = process.env.PORT || 8080;
    
    // Start listening on the specified port and print out a url to visit.
        server.listen(port);
        console.log('Listening on http://localhost:' + port);
```
使用node简单的构建了一个server，但是怎么才能起服务呢？node xxx.js吗？也可以使用 PORT=1234 node xxx.js || export PORT=1234 && node xxx.js，这个就是process.env.PORT的的作用了。

+ 第二个有意思的就是[nodemon](http://nodemon.io/)，可以监听工程中的文件变化，然后自动的执行。

参考：
+ https://github.com/Microsoft/nodejs-guidelines
