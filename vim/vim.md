
<!-- vim-markdown-toc GFM -->

* [vim config](#vim-config)
    * [基本界面美化](#基本界面美化)
    * [好用的插件收集](#好用的插件收集)
    * [自动不全YCM](#自动不全ycm)

<!-- vim-markdown-toc -->

## vim config
### 基本界面美化
1. 安装 vundle 用于管理插件,下次可以试试Plug
2. 安装各种美化插件


### 好用的插件收集
1. airline 状态栏美化
2. [markdown-toc](https://github.com/mzlogin/vim-markdown-toc) 可以生成针对 github gitlab 以及别的网站不同风格的目录.

### 自动不全YCM
1. 安装:可以选择使用 vundle 安装也可以使用 git clone 的方式,需要执行`git submodule update --init --recursive`

2. 配置: 

   ```bash
   ./install.py --clang-completer
   ```
