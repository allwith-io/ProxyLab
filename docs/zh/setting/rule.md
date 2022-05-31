# 接口转发规则的配置

可点击管理页面主菜单上的`转发规则`进行转发规则的管理

<img src="https://img.yzcdn.cn/public_files/2018/03/30/3a7f3c2c682180c496f2e748cf05851e.png" />

## 主要功能

### 规则导入
可以导入远程规则（比如 Gitlab/Github 上的一个文件地址）、本地规则文件。方便团队之间共享规则文件。导入的`远程规则`会在服务器启动时自动同步。

### 规则导出
将规则文件导出，可以放到服务器上，方便别人导入。  

### 规则配置
ProxyLab 中一个规则集可对应多个规则，每个规则集和每个规则都可单独配置是否生效。(如a规则在A规则集下，当A规则不生效时，无论a规则是否被勾选，都不生效)。

<img src="https://img.yzcdn.cn/public_files/2018/03/30/3a7f3c2c682180c496f2e748cf05851e.png" />

### 规则编辑

![](https://img.yzcdn.cn/public_files/2018/03/30/4e6849fa6536d5c067e7dfb8fe732c6b.png)

其中，URL 特征字段可以是简单的 URL 字符串片段，也可以是正则表达式

#### URL 特征配置项详解

URL特征为该请求是否被 ProxyLab 所转发的主要判定方式。其判定规则如下：

1. 优先将 URL 特征当成一个字符去匹配所有请求，当某一请求的 URL 中包含URL特征，则视为该请求符合该URL特征。

2. 当规则1无法匹配时，将该URL特征实例化为一个正则表达式，再对所有请求进行匹配。

#### 请求动作配置项详解

请求动作会根据添加顺序依次执行

* 转发请求：将请求转发到本地、或者另一个地址
* 返回自定义数据：将指定的数据文件返回给浏览器
* 增加请求头：增加请求的header，常见的如cookie、user-agent等
* 增加响应头：增加服务器响应的header，常见的如access-control-allow-origin

## 进阶

### 域名替换
在使用正则写URL特征时，ProxyLab 支持在处理类型的转发中写 $ 占位符，用于替换为正则匹配后第N个获取组。

上面的图片中例子，会把所有 mytest.com 及 mytest.com/xxxx 都转变成访问 http://localhost, 这显然不是大部分情况下想要的。所以需要使用正则：

比如，如果你需要将所有 www.mytest.com 域名替换为 127.0.0.1:8000
1. 那么URL特征填：www\.mytest\.com(.*)
2. 下面转发请求填：http://127.0.0.1:8080$1

安装正则的规则，$1 对应上面第一个括号匹配的内容，一次类推，如果URL特征是： www\.mytest\.com(.*)\/(.*).html ,那么 &2 对应第二个括号匹配的内容

### URL 路径替换

请求url为：https://a.cdn.com/v2/build/wap/showcase/sku_58590c11af.js  
要拦截的请求的url特征为：build/wap/(.*?)_[^_]*$  
请求转发路径为：<%=wapproject%>/js/$1/main.js。  
则最终请求路径中的$1将被替换为 showcase/sku

### 过滤请求参数

在使用正则写URL特征时，ProxyLab 在处理时会对完整的请求路径**包括请求参数**进行处理。

请求url为：https://a.cdn.com/v2/build/wap/showcase/sku_58590c11af.js?date=12345

要拦截的请求的url特征为：build/wap/(.*)

请求转发路径为：/my/project/js/$1

则最终实际的转发路径会是：/my/project/js/showcase/sku_58590c11af.js?date=12345

如需你不需要后面的请求参数，请使用正则进行过滤。

1. 把URL特征改为：`build/wap/(.*)(?:\?.*)` —— 等于把后面参数部分包到第二个括号里去匹配了,
2. 请求转发依旧是：/my/project/js/$1

这样实际的转发路径就会变成 `/my/project/js/showcase/sku_58590c11af.js`，不再包含后面的请求参数。
