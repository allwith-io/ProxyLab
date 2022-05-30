# 快速开始

## 一、说明

您需要在浏览器里安装可以设置代理的插件，然后在里面设置 ProxyLab 所在的电脑的 IP 及 ProxyLab
的端口。这样浏览器的请求就会发送到 ProxyLab，由 ProxyLab 处理并转发。


如果是手机连接 ProxyLab，直接在手机
<a
target="_blank"
href="https://github.com/allwith-io/ProxyLab/blob/master/docs/zh/usage/mobile.md">修改网络设置即可</a>。


## 二、安装 chrome 插件


推荐安装 SwitchyOmega，Chrome 应用商店在线安装点
<a
href="https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif"
target="_blank">这里 </a>。


如果访问 Chrome 应用商店有问题，点
<a href="https://i.miaolu.com/proxylab/SwitchyOmega_2_5_21_0.zip">这里</a> 下载插件（.zip文件）解压，然后离线安装:


* 打开Chrome浏览器，地址栏输入 chrome://extensions/
* 勾择开发者模式，点击'加载已解压的扩展程序'，选择你刚刚解压的文件夹
* 点击确定。扩展程序列表出现你导入的扩展程序即为成功


## 二、配置插件

安装完插件后请设置插件代理地址为 127.0.0.1，代理协议: http，端口为 ProxyLab 代理端口(默认8001)。 如不清楚如何配置
SwitchyOmega，请查看 [chrome 代理设置指南](usage/chrome.md)


## 三、安装根证书
### 为什么要安装根证书
为了能让 ProxyLab 代理 https 请求，安装并信任了 ProxyLab 根证书后，ProxyLab
就可以根据这个根证书，为每个你访问的网址临时创建特定的 https 证书，以达到代理 https 请求的目的

### 1. 安装 ProxyLab 根证书

* 如果你用是 Mac，第一次打开 ProxyLab 的时候，会让你输入系统密码，之后会默认帮你安装证书，你就可以直接移步下面的第 2 步去信任该证书了

<img src="https://i.miaolu.com/proxylab/auto%20install%20cert.jpg" alt="" />

* 如果用的是其他电脑或发现证书并没有安装，请点击 ProxyLab 左侧 `快速开始`，打开管理后台的快速开始页面，里面可以找到证书下载地址

* 如果你用的是手机，也可以在上面提到的也没里找到二维码，手机扫码并有浏览器打开即可

### 2. 信任 ProxyLab 根证书
Mac: 打开软件 <span>Keychain Access</span>，搜索找到 ProxyLab 证书，双击，按下图所示操作
<img src="https://i.miaolu.com/proxylab/trust%20cert.jpg" />


手机、Windows 如何信任根证书，请查看：[根证书的安装与配置](install/root-ca.md)

<!-- ProxyLab 依赖 openssl 生成证书，使用前请确认已安装 openssl (版本建议在 0.9.8 以上，可通过：openssl version 命令查看)。 -->
## 四、使用

现在，你可以在 Chrome 里，用 SwitchyOmega 将代理指向 ProxyLab 了

接着，你可以：

* 在 `请求监控` 里看到所有请求数据，请查看：[使用请求监控](usage/monitor.md)
* 配置 Host
* 配置转发规则，将请求转发到本地文件或远程 url

更进一步，你可以配置多套环境——比如本地开发环境、测试环境、预发环境等，并一键切换，每套环境保护完整的 Host 和转发规则的配置。[了解更多](usage/environment.md)