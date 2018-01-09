# Chrome

## JSONView


## Postman


## Referer Control

该插件用于控制http请求头部的Referer字段。

#### 使用示例

图片URL无法打开，原因是请求头部中没有携带Referer字段，被服务器回了403错误页面。可以增加一条Referer Control配置解决该问题。

图片URL的链接为：http://t11.baidu.com/it/u=570057283,3087826461&fm=170&s=9CFF7E9618693A8242524D6C0300A03E&w=218&h=146&img.PNG

对应配置如下：

```
site filter: http://t11.baidu.com
referer setting (Custom): http://t11.baidu.com
```


## SwitchyOmega

###### 

代理服务器设置工具。

### 

#### 示例：设置whistle代理（情景模式：代理服务器）

|代理协议		|代理服务器 		|代理端口			|
|-----------|---------------|---------------|
|HTTP 		|127.0.0.1		|8899			|


#### 示例：设置pac代理（情景模式：PAC情景模式）

PAC网址：http://pac.internal.baidu.com/bdnew.pac


#### 示例：设置自动切换代理模式（情景模式：自动切换模式）

设置切换规则即可，如：某些域名使用whistle代理，某些域名使用pac代理，某些域名使用直连方式（不使用代理）等等。


## Whistle

配合Whistle抓包工具使用，提供代理自动设置功能，在不知道怎么配置代理的场景下使用。

知道如何配置代理的话，使用SwitchyOmega即可。


## FAQ

### Q: 如何在刷新页面的时候清除浏览器缓存？

使用快捷键<Ctrl+F5>即可，快捷键<F5>不会清除缓存。

关于<F5>和<Ctrl+F5>的区别可以参考：[网页](http://weizhifeng.net/difference-between-f5-and-ctrl-f5.html)。

