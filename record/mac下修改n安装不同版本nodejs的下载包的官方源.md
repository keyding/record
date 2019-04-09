## mac下修改n安装不同版本nodejs的下载包的官方源

- 打开终端，输入（或者其他编辑工具打开.bash_profile文件）

```sh
vi ~/.bash_profile
```

- 增加如下两行命令

```sh
export PROJECT_NAME="node"
export PROJECT_URL="https://npm.taobao.org/mirrors/node/"
```
- 保存文件后终端中输入

```sh
source ~/.bash_profile
```

- 使用命令 `n project x.x.x` 安装指定nodejs版本
