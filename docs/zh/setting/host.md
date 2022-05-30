# Host 配置

可点击管理页面主菜单上的`Host管理`进行Host文件的管理。

<img src="https://img.yzcdn.cn/public_files/2018/04/18/7c182e87331c2300edc23fe707a74024.png" />


## 修改单个Host

Host 规则支持简单的*号匹配。(注意，目前仅支持在规则头部出现*号)。  
当出现 *.mydomain.com 和 h5.mydomain.com 时，如果一个请求同时匹配两者（比如h5.mydomain.com），则优先级是 h5.mydomain.com > *.mydomain.com。


## 跟系统Host文件的关系

你在 ProxyLab 里配置的 Host 仅在请求通过 ProxyLab 代理的时候使用。ProxyLab 不会更改系统 Host。在确定一个域名改用哪个 IP 的时候，ProxyLab 优先匹配内部 Host 列表，没有匹配的情况下再根据系统 Host 文件的内容来匹配。
