# 安装Windows之后的操作

安装`Chrome`替换`Edge`：

> 下载链接： [https://www.google.com/intl/zh-CN/chrome/](https://www.google.com/intl/zh-CN/chrome/)

安装`Notepad++`替换`Notepad`：

> 下载链接： [https://notepad-plus-plus.org/](https://notepad-plus-plus.org/)

安装`InfanView`替换`Photo`应用：

> 下载链接： [https://www.irfanview.com/](https://www.irfanview.com/)

移出资源管理器中的`3D Object`库：

```text
@echo off
REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}" /f
exit
```
## 其他

Office365 [https://portal.office.com/](https://portal.office.com/)

## Windows工作环境



### 必选软件

1. [WSL - Debian](https://www.microsoft.com/en-us/p/debian/9msvkqc78pk6) - 配置内容参考`Linux`模块；
1. [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal-preview/9n0dx20hk701)；
1. [编程字体 - Fira Code](https://github.com/tonsky/FiraCode)；
1. [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/all/#product-desktop-release)；
1. [Google Chromium](https://download-chromium.appspot.com/)；
1. [Docker Desktop](https://www.docker.com/products/docker-desktop)；
1. [MicroSoft Onenote](https://www.microsoft.com/en-us/p/onenote/9wzdncrfhvjl)；
1. [Intelij IDEA](https://www.jetbrains.com/idea/download/index.html)；
1. XShell / MobaXterm；

### 其他软件

1. [记事本替代 - Notepad3](https://www.rizonesoft.com/downloads/notepad3/)
2. [文本编辑器 - VS Code](https://code.visualstudio.com/)
3. [图片浏览器 - InfraView](https://www.microsoft.com/en-us/p/irfanview/9nl0r0jnnzm0)
4. [密码管理器 - Enpass](https://www.microsoft.com/en-us/p/enpass-password-manager/9nj3kmh29vgj)

