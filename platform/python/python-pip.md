## Python包管理器

> python3-pip

### 使用镜像安装包

```sh
pip3 install --user --trusted-host pypi.douban.com -i http://pypi.douban.com/simple/ pandas
```

Pip的配置文件为用户根目录下的：~/.pip/pip.conf（Windows路径为：C:\Users\<UserName>\pip\pip.ini）, 您可以配置如下内容：

```conf
[global]
index-url = https://mirrors.huaweicloud.com/repository/pypi/simple
trusted-host = mirrors.huaweicloud.com
timeout = 120 
```

### 资料

- [清华大学开源软件镜像站 - pypi](https://mirrors.tuna.tsinghua.edu.cn/help/pypi/)
- [PIP - 华为开源镜像站](https://mirrors.huaweicloud.com/python/)