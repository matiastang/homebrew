# Homebrew使用

[Homebrew官网](https://brew.sh/index_zh-cn)
[Homebrew安装](https://github.com/matiastang/homebrew/blob/master/md/homebrew%E5%AE%89%E8%A3%85.md)

## Homebrew常用命令

> $ brew update # 更新`Homebrew`

> $ brew outdated # 查看哪些安装包需要更新

> $ brew install $FORMULA   # 安装

*注意* 执行安装时，会先去更新`Homebrew`，如果不想更新，只是想安装包，可以`Ctrl + c`结束更新，结束后就自动下载包了。

> $ brew upgrade             # 更新所有的包
> $ brew upgrade $FORMULA    # 更新指定的包

> $ brew cleanup             # 清理所有包的旧版本
> $ brew cleanup $FORMULA    # 清理指定包的旧版本
> $ brew cleanup -n          # 查看可清理的旧版本包，不执行实际操作

> $ brew pin $FORMULA      # 锁定某个包
> $ brew unpin $FORMULA    # 取消锁定

> $ brew info $FORMULA    # 显示某个包的信息
> $ brew info             # 显示安装了包数量，文件数量，和总占用空间

`brew info` 可以查看包的相关信息，最有用的应该是包依赖和相应的命令。比如 `Nginx` 会提醒你怎么加 `launchctl` ，`PostgreSQL` 会告诉你如何迁移数据库。这些信息会在包安装完成后自动显示，如果忘了的话可以用这个命令很方便地查看。

> $ brew deps --installed --tree # 查看已安装的包的依赖，树形显示

`brew deps` 可以显示包的依赖关系，我常用它来查看已安装的包的依赖，然后判断哪些包是可以安全删除的。

> $ brew list   # 列出已安装包

> $ brew rm $FORMULA                # 删除某个包
> $ brew uninstall --force $FORMULA # 删除所有版本

## 问题

* `cannot load such file -- active_support/core_ext/object/blank`

> $ brew doctor

```c
/System/Library/Frameworks/Ruby.framework/Versions/2.3/usr/lib/ruby/2.3.0/rubygems/core_ext/kernel_require.rb:55:in `require': cannot load such file -- active_support/core_ext/object/blank (LoadError)
```

执行如下命令：
> $ brew update-reset

[stack overflow](https://stackoverflow.com/questions/54888582/ruby-cannot-load-such-file-active-support-core-ext-object-blank)