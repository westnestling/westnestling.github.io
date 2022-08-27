---
title: "mac OS 安装 homebrew 失败解决方案"
date: 2022-08-27T13:34:49+08:00
draft: true
---




# [mac OS 安装 homebrew 失败解决方案](https://www.cnblogs.com/mizhifei/p/16558406.html)

1.查看[homebrew官网](https://www.cnblogs.com/mizhifei/p/brew.sh)的安装教程，复制安装命令。

![img](img/MacOs%20homeBrew%E5%AE%89%E8%A3%85/1595751-20220807081317482-116967477.png)

 

 

2.打开mac OS终端Terminal，输入安装命令，输入密码，回车确认安装。

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

 

 3.然后你可能会得到一个错误：

```
fatal: unable to access 'https://github.com/Homebrew/brew/': LibreSSL SSL_read: error:02FFF03C:system library:func(4095):Operation timed out, errno 60
Failed during: git fetch --force origin
```

![img](img/MacOs%20homeBrew%E5%AE%89%E8%A3%85/1595751-20220807082006923-2042878586.png)

也可能是这个错误：

```
error: RPC failed; curl 28 LibreSSL SSL_read: error:02FFF03C:system library:func(4095):Operation timed out, errno 60
fatal: expected flush after ref listing
Error: Fetching /opt/homebrew/Library/Taps/homebrew/homebrew-core failed!
Failed during: /opt/homebrew/bin/brew update --force --quiet
```

**![img](img/MacOs%20homeBrew%E5%AE%89%E8%A3%85/1595751-20220807081618001-1962795975.png)**

4.出现这个错误是因为墙的原因，解决方案是使用镜像，好用的有[清华镜像](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)和[阿里云镜像](https://developer.aliyun.com/mirror/homebrew)，在这里我使用清华的镜像。

**5.首先修改homebrew相关的环境变量：**

**输入命令：**

```
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
```

然后再运行安装命令：

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

安装成功，此时还无法在终端使用brew，需要配置brew的安装路径到环境变量。

![img](img/MacOs%20homeBrew%E5%AE%89%E8%A3%85/1595751-20220807093743176-1658401334.png)

 

 6.配置brew的安装路径到环境变量：

```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

 配置完成即可在终端使用brew命令了，开始愉快的使用吧！

![img](img/MacOs%20homeBrew%E5%AE%89%E8%A3%85/1595751-20220807094312585-1540111104.png)

 





## brew install 慢

### 切换到 Homebrew 目录

```csharp
cd "$(brew --repo)"
查看远程仓库 git remote -v.  默认的使用的github。
 删除远程： git remote rm origin 
添加阿里源 ：git remote add origin https://mirrors.aliyun.com/homebrew/brew.git
切换成阿里源: git remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git
```

 

### 替换 homebrew-core.git:

```csharp
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
查看远程仓库 git remote -v.  默认的使用的github。
 删除远程： git remote rm origin 
添加阿里源 ：git remote add origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
切换成阿里源： git remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
```

### 步骤三
brew update
注意这里需要等待一会，因为要更新资源。

更新完后使用brew update，brew install速度变快很多了，不会卡在那半天没动静，替换镜像完成。
