共享缓存



#### 缓存的位置

1. ServiceWorker

   非内建 可自由控制目标和方式，持久性缓存

2. Memory Cache

   短期缓存

3. Disk Cache

   空间更大

4. Push Cashe



#### 缓存策略

响应头中带有

**强缓存**

Cache-control;max-age/s-maxage

> HTTP/1.1 资源有效期

Exprires

> HTTP/1.0 资源失效的时间
>
> Dis: 1.时间误差 2.过期后必定重载

**协商缓存**

Last-Modified 响应头

> 文件在服务器最后修改时间

If-Modified-Since 请求头

> 等于上一次的Last-modified

Etag、If-None-Match

> 文件唯一标记，Etag分强弱，弱Etag字段值前会带 `W/`



#### **其他字段**

**Cache-Control**

- max-age = [秒]
- no-store 禁止缓存
- no-cache 可以缓存，但是必须服务器验证
- must-revalidate 不过期就能用

**服务器缓存控制**

- Accept <—> Content-Type
- Accept-Language <—> Content-Language
- Accept-Charset <—> Content-Type
- Accept-Encoding <—> Content-Encoding



#### 用户行为

超链接重新输入 —>强缓存-协商缓存

F5 / Cmd+R —> Cache-Control:max-age = 0

Ctrl+F5 / Cmd+Shift —> Cache-Control:no-cache

