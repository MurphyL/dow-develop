# 发行版 - Ubuntu

## 环境搭建

- 免密登陆远程机器

```sh
# 检查SSH keys是否已存在
ls -al ~/.ssh
# 生成SSH keys
ssh-keygen -t rsa -C "example@email.com"
# 拷贝SSH公钥到远程
ssh-copy-id remote_user@remote_host
```

## 后台运行程序

```sh
nohup command >> /dev/null 2>&1 &
```

## Zsh

> 切换`Shell`： chsh -s /bin/zsh

- [bash](./bash.md)
- [zsh](./zsh.md)

## 参考文档

- https://man.linuxde.net/
- http://billie66.github.io/TLCL/book/
- https://github.com/jlevy/the-art-of-command-line
- https://github.com/alebcay/awesome-shell
- https://github.com/wuzhouhui/awk/blob/master/- The_AWK_Programming_Language_zh_CN.pdf
- https://github.com/skywind3000/awesome-cheatsheets
- https://github.com/skywind3000/awesome-cheatsheets/blob/master/languages/- bash.sh
- https://mirrors.tuna.tsinghua.edu.cn/help/debian/
- https://www.linuxcool.com/
- http://www.pathname.com/fhs/
- http://lists.busybox.net/pipermail/busybox/2010-December/074114.html