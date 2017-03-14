## electron安装时,node install.js长时间无响应的解决办法

编辑器打开用户目录下（Mac）的 ~/.npmrc

```sh
registry=https://registry.npm.taobao.org   
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
phantomjs_cdnurl=http://npm.taobao.org/mirrors/phantomjs
ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/
```

保存，然后正常安装electron