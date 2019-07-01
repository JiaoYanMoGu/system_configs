自定义的一些alias
```shell
alias git_set_proxy="git_set(){ git config --global http.proxy 'socks5://127.0.0.1:1080';git config --global https.proxy 'socks5://127.0.0.1:1080'};git_set"
alias git_unset_proxy="git_unset(){git config --global --unset http.proxy; git config --global --unset https.proxy};git_unset"

#git config --global https.proxy http://127.0.0.1:1080

#git config --global https.proxy https://127.0.0.1:1080
```

