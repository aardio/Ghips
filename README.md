# Ghips
GitHub 国内网速优化与修复工具。  
使用 GitHub 官方 API 获取当前系统访问速度最快的 IP ，并更新 hosts 文件。  

>[点这里下载 Ghips](https://github.com/aardio/Ghips/releases/download/1.0/Ghips.7z) 体积仅 600 KB  
支持 Win7，Win8，Win10，Win11 等操作系统。  

![Ghips](./screenshots/Ghips.gif)

可点上图下拉列表手动选择 IP。
>更新 IP 后首次访问 GitHub 可能会略慢，稍等就快了。 

本程序需要以管理权限运行才能修改 hosts。  
建议右键点 Ghips 托盘图标，在弹出菜单中勾选「开机启动」。

![Ghips](./screenshots/menu.png)

这样开机就会静默获取管理权限启动，不会再弹出警告。

访问速度快的 IP 经常变更，单击 Ghips 托盘图标能快速刷新 IP 测速结果。   

 
本软件使用 [aardio 编程语言 ](https://www.aardio.com) 开发。

![Ghips](./screenshots/Ghips.png)

调和 GitHub API 的方法请参考：  
[《魔法 web.rest ：自动封装任意 HTTP 接口为本地函数》](https://mp.weixin.qq.com/s/4mYRDnO49alwpQoBD_cILg)

修改 hosts 文件的文件夺权这些比较麻烦，
不过用 aardio 做这事很简单，关键源码如下：
```javascript
fsys.hosts.ownCacls();
fsys.hosts.update(githubIps)
```

用 aardio 实现软件开机静默获取管理权限也很简单，关键源码：
```javascript
import sys.runAsTask;
var sysTask = sys.runAsTask("Ghips","GitHub 优化与修复工具")
sysTask.register("/tray");
```