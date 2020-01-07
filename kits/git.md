### Git

```shell
# set git user
set_git_user(){
    git config --global user.name "$1"
    git config --global user.email "$2"
    echo "Git user is: $1 - $2"
}

huoa(){
    set_git_user "huoa" "huoa.x@qq.com"
}
murph(){
    set_git_user "murph" "murphyl@outlook.com"
}

hcommit(){
    huoa
    git commit
}

mcommit(){
    murph
    git commit
}
```