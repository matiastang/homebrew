# Homebrew安装

[Homebrew官网](https://brew.sh/index_zh-cn)

[Homebrew使用](https://github.com/matiastang/homebrew/blob/master/md/homebrew%E4%BD%BF%E7%94%A8.md)

## 简介

`Homebrew` 是使用 `Mac OS` 的包管理工具，`Homebrew` 可以安装 `Apple` 没有预装但非常有用的软件包。`Homebrew` 会将软件包安装到独立目录，并将其文件软链接至 `/usr/local`。

## 安装

开始安装前需要安装 macOS 命令行工具：

```
$ xcode-select —install
```

或者，在[下载安装](https://developer.apple.com/download/more/)。

* 科学上网

使用命令行安装Homebrew：
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
* 非科学上网

1. 使用上述命令安装时会报错：
```
$ curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused
```
2. 下载`homebrew.rb`文件到本地

3. 进入保存`homebrew.rb`的文件夹执行如下命令：
```
$ ruby homebrew.rb
```
## 更换`Homebrew`源

默认官方的更新源都是存放在**GitHub**上的，这也是中国大陆用户访问缓慢的原因，一般来说我们会更倾向选择国内提供的更新源，在此推荐中国科大以及清华大学提供的更新源。

### 替换brew.git:
```
$ cd "$(brew --repo)"
```
* 中国科大:
```
$ git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
```
* 清华大学:
```
$ git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
```
### 替换homebrew-core.git:
```
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
```
* 中国科大:
```
$ git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
```
* 清华大学:
```
$ git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
```
### 替换homebrew-cask:
```
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
```
* 中国科大:
```
$ git remote set-url origin git://mirrors.ustc.edu.cn/homebrew-cask.git
```
* 清华大学:
```
$ git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
```
### 替换homebrew-bottles:

* 中国科大:
```
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile
```
* 清华大学:
```
$ echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
$ source ~/.bash_profile
```
### 应用生效:
```
$ brew update
$ brew update --verbose # 可以查看更新进度
```
完成更新源后，我们可以使用如下命令：
```
$ brew upgrade
```
将现有的软件进行更新至最新版本，速度上会比从github上快很多。

## 重置更新源

某些时候也有换回官方源的需求

### 重置brew.git:
```
$ cd "$(brew --repo)"
$ git remote set-url origin https://github.com/Homebrew/brew.git
```
### 重置homebrew-core.git:
```
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
$ git remote set-url origin https://github.com/Homebrew/homebrew-core.git
```
## 诊断Homebrew

如果`Homebrew`有点儿什么问题，可以如下尝试解决

### 诊断Homebrew的问题:
```
$ brew doctor
```
### 重置brew.git设置:
```
$ cd "$(brew --repo)"
$ git fetch
$ git reset --hard origin/master
```
### homebrew-core.git同理:
```
$ cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
$ git fetch
$ git reset --hard origin/master
```
### 应用生效:
```
$ brew update
```