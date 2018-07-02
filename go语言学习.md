### Mac下Vim开发配置（三）

#### Mac下终端配置配色方案（item2 + oh-my-zsh +3024Night)
##### 配置
将iTem2设置为默认终端：
（菜单栏）iTerm2 -> Make iTerm2 Default Term


##### 配色方案
我选用的是3024Night,可以自行配置喜欢的主题，这个在官网有很多，自己下载http://iterm2colorschemes.com 

安装oh-my-zsh
github连接：https://github.com/robbyrussell/oh-my-zsh

使用 crul 安装：
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

或使用wget：
```
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

##### 主题

安装成功后，用vim打开隐藏文件 .zshrc ，修改主题为 agnoster：
```
ZSH_THEME="agnoster"
```
应用这个主题需要特殊的字体支持，否则会出现乱码情况，这时我们来配置字体：

1.使用 Meslo 字体，点开连接点击 view raw 下载字体。

2.安装字体到系统字体册。

3.应用字体到iTerm2下，我自己喜欢将字号设置为16px，看着舒服（iTerm -> Preferences -> Profiles -> Text -> Change Font）。

4.重新打开iTerm2窗口，这时便可以看到效果了。 

到这步我们的终端看上去已经非常好看了，这时我们来安装其它插件，让终端看起来更加风骚。


##### 自动提示命令
当我们输入命令时，终端会自动提示你接下来可能要输入的命令，这时按 → 便可输出这些命令，非常方便。

设置如下：

1.克隆仓库到本地 ~/.oh-my-zsh/custom/plugins 路径下
```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
2.用 vim 打开 .zshrc 文件，找到插件设置命令，默认是 plugins=(git) ，我们把它修改为
```
plugins=(zsh-autosuggestions git)
```
3.重新打开终端窗口。
PS：当你重新打开终端的时候可能看不到变化，可能你的字体颜色太淡了，我们把其改亮一些：
```
cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions 
vim zsh-autosuggestions.zsh
```
修改 ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=10' （ fg=10 在我电脑上显示良好）。

##### 语法高亮
1.使用homebrew安装 zsh-syntax-highlighting 插件。
```
brew install zsh-syntax-highlighting
```
2.配置.zshrc文件，插入一行。
```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
3.输入命令。
```
source ~/.zshrc
```
4.ls

Mac OS X 是基于 FreeBSD 的，所以一些工具 ls, top 等都是 BSD 那一套，ls 不是 GNU ls，所以即使 Terminal/iTerm2 配置了颜色，但是在 Mac 上敲入 ls 命令也不会显示高亮，可以通过安装 coreutils 解决
```
brew install coreutils
```
PS：安装homebrew包管理工具：
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


