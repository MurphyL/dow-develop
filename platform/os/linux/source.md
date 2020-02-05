## Debian切换源

> 按照清华镜像站的说明修改文件内容后，`apt-get update`报错：Package ca-certificates is not available, but is referred to by another package.

1. 修改源配置中的`https`为`http`；
2. `apt update`；
3. `apt install ca-certificates`；
4. 现在你可以切换到`https`版本的`apt`配置了。

参考：[Ubuntu Docker Container update-ca-certificates: command not found](https://askubuntu.com/questions/792354/ubuntu-docker-container-update-ca-certificates-command-not-found)
