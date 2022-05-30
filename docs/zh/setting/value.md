# 变量设置

变量，主要用于配置转发规则的转发请求目的地的时候，可以用在这里事先设置好的变量，替代一些常用的冗长的字符串，比如本地项目的绝对路径、远程服务器的域名等

可点击管理页面主菜单上的 `变量设置` 进行变量的管理

**示例：**

![](/docs/assets/images/value.png)

转发配置

<img src="https://img.yzcdn.cn/public_files/2018/03/30/6c15d8b078542bb9afbad375aefb866c.png" />

这样通过代理请求线上文件 myfile.json 的时候，响应的内容就会变成 /path/to/myproject/myfile.json 的内容。