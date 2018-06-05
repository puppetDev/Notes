## HTTP 缓存
>缓存的种类有很多,其大致可归为两类：**私有与共享缓存**。共享缓存存储的响应能够被多个用户使用。私有缓存只能用于单独用户。  

### (私有)浏览器缓存
私有缓存只能用于单独用户。你可能已经见过浏览器设置中的“缓存”选项。浏览器缓存拥有用户通过 HTTP 下载的所有文档。这些缓存为浏览过的文档提供向后/向前导航，保存网页，查看源码等功能，可以避免再次向服务器发起多余的请求。它同样可以提供缓存内容的离线浏览。
### (共享)代理缓存
共享缓存可以被多个用户使用。例如，ISP 或你所在的公司可能会架设一个 web 代理来作为本地网络基础的一部分提供给用户。这样热门的资源就会被重复使用，减少网络拥堵与延迟。
>互联网服务供应商（英语：Internet Service Provider，簡稱ISP）
### 缓存控制

#### cache-control
请求头和响应头都支持这个属性。通过它提供的不同的值来定义缓存策略。

- 缓存请求指令
客户端可以在HTTP请求中使用的标准 Cache-Control 指令。

```js
Cache-Control: max-age=<seconds>
//设置缓存存储的最大周期，超过这个时间缓存被认为过期(单位秒)。与Expires相反，时间是相对于请求的时间。
Cache-Control: max-stale[=<seconds>]
Cache-Control: min-fresh=<seconds>
Cache-control: no-cache
//在释放缓存副本之前，强制高速缓存将请求提交给原始服务器进行验证。
Cache-control: no-store
//缓存不应存储有关客户端请求或服务器响应的任何内容。
Cache-control: no-transform
Cache-control: only-if-cached
```

- 缓存响应指令
服务器可以在响应中使用的标准 Cache-Control 指令。

```js
Cache-control: must-revalidate
//缓存必须在使用之前验证旧资源的状态，并且不可使用过期资源。
Cache-control: no-cache
//在释放缓存副本之前，强制高速缓存将请求提交给原始服务器进行验证。
Cache-control: no-store
//缓存不应存储有关客户端请求或服务器响应的任何内容。
Cache-control: no-transform
Cache-control: public
//表明响应可以被任何对象（包括：发送请求的客户端，代理服务器，等等）缓存。
Cache-control: private
//表明响应只能被单个用户缓存，不能作为共享缓存（即代理服务器不能缓存它）。
Cache-control: proxy-revalidate
//与must-revalidate作用相同，但它仅适用于共享缓存（例如代理），并被私有缓存忽略。
Cache-Control: max-age=<seconds>
Cache-control: s-maxage=<seconds>
```
