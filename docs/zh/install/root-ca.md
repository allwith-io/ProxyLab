# 根证书的安装与配置

为什么要安装根证书
为了能让 ProxyLab 代理 https 请求，安装并信任了 ProxyLab 根证书后，ProxyLab 就可以根据这个根证书，为每个你访问的网址临时创建特定的 https 证书，以达到代理 https 请求的目的。

## Mac，手动安装并信任根证书
1. 下载证书
点击 ProxyLab 左侧的 `快速开始`，在打开页面里找到证书下载链接并下载。

2. 安装并信任证书
参考：https://www.cnblogs.com/reachos/p/12201389.html

### iOS、Android ，安装并信任根证书

1. 下载证书
点击 ProxyLab 左侧的 `快速开始`，在打开页面里可以看到一个二维码，通过微信扫描获得证书下载链接，然后选择用系统自带的浏览器打开链接（iOS 下系统自带的浏览器是 safari, Android 需要自己判断），会自动下载证书.

2. 安装并信任证书
* 系统自带的浏览器打开证书链接后会自动下载、进入安装界面。
* Android 种类繁多，安装和信任证书没有统一的步骤，请按照界面提示操作。
* iOS下，在安装界面上点 Install 后，按照提示进行操作。

** 注：iOS 10.3以上的系统在安装根证书后，需要进入Settings > General > About > Certificate Trust Testings 里面进行证书信任，新安装的根证书才生效。信任界面如下图：

<img src="https://img.yzcdn.cn/public_files/2018/04/18/5ee4efa065596389eda0b5443ce63767.png" width="300" />

## 