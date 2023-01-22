# go_base_env
go 基础环境搭建，我只说一遍

# wsl 环境
1. windows 应用商城
   1. 安装 Windows terminal
   2. 下载 ubuntu


```
# 管理员 powershell 开启机器虚拟化feature
PS C:\WINDOWS\system32> dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

部署映像服务和管理工具
版本: 10.0.22621.1

映像版本: 10.0.22623.875

启用一个或多个功能
[==========================100.0%==========================]
操作成功完成。

# 安装 wsl
PS C:\WINDOWS\system32> wsl --install
正在安装: 虚拟机平台
已安装 虚拟机平台。
正在安装: 适用于 Linux 的 Windows 子系统
已安装 适用于 Linux 的 Windows 子系统。
正在安装: Ubuntu
已安装 Ubuntu。
请求的操作成功。直到重新启动系统前更改将不会生效。



# 设置 wsl 1
wsl --set-version Ubuntu-18.04 1

# 设置dns

nameserver 8.8.8.8
nameserver 8.8.4.4


# 配置代理
export https_proxy=http://127.0.0.1:10808 http_proxy=http://127.0.0.1:10808 all_proxy=socks5://127.0.0.1:10808

vscode配置代理
socks5://127.0.0.1:10808
```

# go 环境
安装 [gvm](https://github.com/moovweb/gvm) 和 go
```

# 安装 gvm
wget https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer
bash gvm-installer

# 先安装 gcc 环境，编译 go1.4
sudo apt-get update
sudo apt-get install curl git mercurial make binutils bison gcc build-essential

# 先安装go1.4 binary, go1.4+ 需要 go 编译器
gvm install go1.4 -B
gvm use go1.4
export GOROOT_BOOTSTRAP=$GOROOT

# 安装常用go版本 go1.16 1.17 1.18
gvm install go1.16
gvm install go1.17
gvm install go1.18

gvm use go1.18 --default

# 设置go代理
go env -w GOPROXY=https://goproxy.io,direct
# 设置 git 代理
git config --global http.proxy 'socks5://127.0.0.1:10808'
git config --global https.proxy 'socks5://127.0.0.1:10808'
```

# 安装 nvm/node
```
wget https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh
bash install.sh
bash
nvm install 17
nvm use 17
node -v

不建议装最新版，最新版会依赖比较高版本的glibc
```


# 安装 bud
```
wget https://raw.githubusercontent.com/livebud/bud/main/install.sh
bash install.sh
安装错误多试几次。可能是网络问题
```

# 建bud项目
```
gvm use go1.18
bud create ${project} --module github.com/wymli/forge_dashboard

```


