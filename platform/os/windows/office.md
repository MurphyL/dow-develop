### 清除Office授权

授权方面，您可以尝试win+S后输入CMD，右键命令提示符，选择以管理员身份运行，之后用下面的命令来进行查询：

- 64位软件
> C:\Program Files\Microsoft Office\Office16

- 32位软件

> C:\Program Files(x86)\Microsoft Office\Office16 

列出已在本机注册的授权：

> 若已安装的目标软件没有显示在结果列表中，运行对应的软件，稍等几分钟。

```cmd
cscript ospp.vbs /dstatus
```


返回的条目中会有对应的条目，记下其提供的最后5位秘钥，使用下面的命令进行清除：

```cmd
cscript ospp.vbs /unpkey:xxxxx
```
其中xxxxx为上面记录的最后5位秘钥。

### 参考资料

- [绑定微软账户的visio2016无法在新电脑上激活，旧电脑已与账户解绑，visio仍无法安装](https://answers.microsoft.com/zh-hans/msoffice/forum/all/%E7%BB%91%E5%AE%9A%E5%BE%AE%E8%BD%AF%E8%B4%A6/337af04f-f0b7-4cc7-a22f-cd547c32ee58?auth=1)