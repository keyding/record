## centos6.5安装node.js

```shell

yum repolist // 如果没有看到epel，通过rpm安装它

rpm -Uvh http://download-i2.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

sudo yum install nodejs npm --enablerepo=epel

```