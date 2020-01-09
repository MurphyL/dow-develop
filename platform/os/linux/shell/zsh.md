# Zsh

> 切换`Shell`： chsh -s /bin/zsh

## 安装包管理器 - ‵antigen`

> 使用[`antigen`](https://github.com/zsh-users/antigen)管理插件

```sh
git clone https://github.com/zsh-users/antigen.git ~/.antigen/antigen
```

### 初始化 - `~/.zshrc`

```zsh
source ~/.antigen/antigen/antigen.zsh

antigen theme bhilburn/powerlevel9k

antigen bundle zsh-users/zsh-completions
antigen bundle zsh-users/zsh-autosuggestions
antigen bundle zsh-users/zsh-syntax-highlighting

antigen apply
```

### 手动安装插件

```sh
git clone $git_resp ~/.antigen/$plug_name
#  加载插件
source ~/.antigen/$plug_dir/$plug_name.zsh
```

### 参考资料

- [使用 antigen 管理 Zsh 配置](https://gythialy.github.io/zsh-config/)
- [zsh-users/antigen - Installation](https://github.com/zsh-users/antigen/wiki/Installation)