# iTerm2 + Oh My Zsh 打造舒适终端体验

---
### 写在前面

最终效果图：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/14.png)

本文严重抄袭自：https://www.jianshu.com/p/7de00c73a2bb

因排版和原文中的一些bug，参照搜索引擎和原文有了本篇文章。

因为powerline以及homebrew均需要安装command line tool，网络条件优越的同学在执行本文下面内容之前，可以先安装XCode并打开运行一次（会初始化安装components），省去以后在iterm2中的等待时间。

另外，git也是必要的，各位可以自行下载安装，除了网络没有任何坑：

https://git-scm.com

介于此，本文默认各位同学已经安装了git环境和xcode（command line tools），遇到提示找不到git命令或需要安装command line tool的地方，文中不再赘述了。


### 下载iTerm2

可以直接去官网下载：https://www.iterm2.com/

安装完成后，在/bin目录下会多出一个zsh的文件。

Mac系统默认使用dash作为终端，可以使用命令修改默认使用zsh：

```bash
chsh -s /bin/zsh
```

如果想修改回默认dash，同样使用chsh命令即可：

```bash
chsh -s /bin/bash
```

OK，这就是iTerm2初始的样子，下面我们来美化它，让它变得更好用！

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/1.png)

### 安装Oh my zsh

安装方法有两种，可以使用curl或wget，看自己环境或喜好：

```bash
# curl 安装方式
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

```bash
# wget 安装方式
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

安装命令和安装完成后的截图：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/2.png)

oh-my-zsh开源地址：https://github.com/robbyrussell/oh-my-zsh

### 安装PowerLine

powerline官网：http://powerline.readthedocs.io/en/latest/installation.html

安装powerline的方式依然简单，也只需要一条命令：

```bash
pip install powerline-status --user
```

没有安装pip的同学可能会碰到zsh: command not found: pip。

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/3.png)

使用命令安装pip即可：

```bash
sudo easy_install pip
```

安装后再次执行安装powerline的命令即可。

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/4.png)

### 安装PowerFonts

安装字体库需要首先将项目git clone至本地，然后执行源码中的install.sh。

在你习惯的位置新建一个文件夹，如：~/Desktop/OpenSource/

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/5.png)

在此文件夹下执行git clone命令：

```bash
# git clone
git clone https://github.com/powerline/fonts.git --depth=1
# cd to folder
cd fonts
# run install shell
./install.sh
```

执行结果如下：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/6.png)

安装好字体库之后，我们来设置iTerm2的字体，具体的操作是iTerm2 -> Preferences -> Profiles -> Text，在Font区域选中Change Font，然后找到Meslo LG字体。有L、M、S可选，看个人喜好：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/7.png)

### 安装配色方案

配色方案在使用VIM或Colorful Log时会变得非常有用，同时界面也不会一片黑绿一样死板。

同样使用git clone的方式下载源码进行安装：

```bash
cd ~/Desktop/OpenSource
git clone https://github.com/altercation/solarized
cd solarized/iterm2-colors-solarized/
open .
```

在打开的finder窗口中，双击Solarized Dark.itermcolors和Solarized Light.itermcolors即可安装明暗两种配色：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/8.png)

再次进入iTerm2 -> Preferences -> Profiles -> Colors -> Color Presets中根据个人喜好选择这两种配色中的一种即可：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/9.png)

### 安装主题

下载agnoster主题，执行脚本安装：

```bash
cd ~/Desktop/OpenSource
git clone https://github.com/fcamblor/oh-my-zsh-agnoster-fcamblor.git
cd oh-my-zsh-agnoster-fcamblor/
./install
```

执行上面的命令会将主题拷贝到oh my zsh的themes中：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/10.png)

拷贝完成后，执行命令打开zshrc配置文件，将ZSH_THEME后面的字段改为agnoster。

```bash
vi ~/.zshrc
```

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/11.png)

修改完成后按一下esc调出vi命令，输入:wq保存并退出vi模式。

此时command+Q或source配置文件后，iTerm2变了模样：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/12.png)

### 安装高亮插件

这是oh my zsh的一个插件，安装方式与theme大同小异：

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
vi ~/.zshrc
```

这时我们再次打开zshrc文件进行编辑。找到plugins，此时plugins中应该已经有了git，我们需要把高亮插件也加上：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/13.png)

请务必保证插件顺序，zsh-syntax-highlighting必须在最后一个。

然后在文件的最后一行添加：source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

按一下esc调出vi命令，输入:wq保存并退出vi模式。

执行命令使刚才的修改生效：

```bash
source ~/.zshrc
```

至此大功告成，请看最终效果图：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/14.png)

背景图片取自微软Surface Studio的4K壁纸(将近12MB大小)，非常漂亮，需要的可以自取：

https://pan.baidu.com/s/18jNrULbr05npD0Z_ht28Kg

更换背景图片方式：iTerm2 -> Preferences -> Profiles -> Window -> BackGround Image勾选图片即可。

#### 可选择、命令补全

跟代码高亮的安装方式一样，这也是一个zsh的插件，叫做zsh-autosuggestion，用于命令建议和补全。

```bash
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-autosuggestions
vi ~/.zshrc
```

找到plugins，加上这个插件即可：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/15.png)

插件效果：

![ImageInitIterm](https://raw.githubusercontent.com/sirius1024/pubimgs/master/blogs/iterm2/16.png)

有同学说补全命令的字体不太清晰，与背景颜色太过相近，其实可以自己调整一下字体颜色。

Preferences -> Profiles -> Colors 中有Foreground是标准字体颜色，ANSI Colors中Bright的第一个是补全的字体颜色。


----

#### 高亮当前鼠标的位置
一个标签页中开的窗口太多，有时候会找不到当前的鼠标，⌘+/找到它。
![ImageInitIterm](https://upload-images.jianshu.io/upload_images/6780798-6082151f7dc85050.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)


#### iTerm2 快速隐藏和显示
这个功能也非常使用，就是通过快捷键，可以快速的隐藏和打开iTerm2,示例配置(Commond + .):
![ImageInitIterm](https://upload-images.jianshu.io/upload_images/6780798-eafc19258f733275.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)


#### iTerm2 隐藏用户名和主机名
有时候我们的用户名和主机名太长，比如我的xishuai@xishuaideMacBook-Pro，终端显示的时候会很不好看（上面图片中可以看到），我们可以手动去除。

编辑vim ~/.zshrc文件，增加DEFAULT_USER="xishuai"配置，示例：
![ImageInitIterm](https://upload-images.jianshu.io/upload_images/6780798-e1b9c5b2a8bd3f2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/982/format/webp)

我们可以通过whoami命令，查看当前用户，效果（另外分屏的效果）：

![ImageInitIterm](https://upload-images.jianshu.io/upload_images/6780798-63e18826ff74f888.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

#### iTerm2快捷命令
快捷命令说明：[这里](https://cnbin.github.io/blog/2015/06/20/iterm2-kuai-jie-jian-da-quan/ "悬停显示")有详细的：
```markdown
command + t 新建标签
command + w 关闭标签
command + 数字 command + 左右方向键    切换标签
command + enter 切换全屏
command + f 查找
command + d 垂直分屏
command + shift + d 水平分屏
command + option + 方向键 command + [ 或 command + ]    切换屏幕
command + ; 查看历史命令
command + shift + h 查看剪贴板历史
ctrl + u    清除当前行
ctrl + l    清屏
ctrl + a    到行首
ctrl + e    到行尾
ctrl + f/b  前进后退
ctrl + p    上一条命令
ctrl + r    搜索命令历史
```

----
#### ssh保活（keepalive）配置
当你使用ssh客户端连接公司服务器时，很有可能会出现闲置一段时间后，被服务器断开的情况，这是运维部门的一种安全策略。但这种被动断开很可能会影响到自己的工作上下文，例如你运行了一个耗时较长的脚本，或用vim打开了一个文本文件，如果此时远程服务器断开了你的连接，你的工作就被中断了，且无法恢复，这种体验非常糟糕。

怎样才能让iTerm2帮你保持连接呢？其实这事儿也不是iTerm2来完成的，而是ssh客户端本身来完成的，修改~/.ssh/config文件，如下
```markdown
Host *
    ServerAliveInterval 10
```
上述设置意为对任何一个ssh连接，每10秒发送一个no-op包，意思是即使你不做任何操作，也可以起到心跳保活的效果.

参考：
[iTerm2中ssh保持连接不断开](http://bluebiu.com/blog/iterm2-ssh-session-idle.html)


----
----
参考链接：
感谢[GuoTuo](https://github.com/sirius1024/iterm2-with-oh-my-zsh)、[杂货铺学徒](https://www.jianshu.com/p/53cd3cdf2679?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation)



