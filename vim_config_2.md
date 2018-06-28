### Mac下Vim开发配置（二）

#### 安装和基本用法
安装插件建议使用[Vundle](https://github.com/VundleVim/Vundle.vim)进行安装，Vundle的用法很简单，可以到GitHub上面查看。

在NERDTree操作区的一些基本操作:
``` vim
?: 快速帮助文档
o: 打开一个目录或者打开文件，创建的是buffer，也可以用来打开书签
go: 打开一个文件，但是光标仍然留在NERDTree，创建的是buffer
t: 打开一个文件，创建的是Tab，对书签同样生效
T: 打开一个文件，但是光标仍然留在NERDTree，创建的是Tab，对书签同样生效
i: 水平分割创建文件的窗口，创建的是buffer
gi: 水平分割创建文件的窗口，但是光标仍然留在NERDTree
s: 垂直分割创建文件的窗口，创建的是buffer
gs: 和gi，go类似
x: 收起当前打开的目录
X: 收起所有打开的目录
e: 以文件管理的方式打开选中的目录
D: 删除书签
P: 大写，跳转到当前根路径
p: 小写，跳转到光标所在的上一级路径
K: 跳转到第一个子路径
J: 跳转到最后一个子路径
<C-j>和<C-k>: 在同级目录和文件间移动，忽略子目录和子文件
C: 将根路径设置为光标所在的目录
u: 设置上级目录为根路径
U: 设置上级目录为跟路径，但是维持原来目录打开的状态
r: 刷新光标所在的目录
R: 刷新当前根路径
I: 显示或者不显示隐藏文件
f: 打开和关闭文件过滤器
q: 关闭NERDTree
A: 全屏显示NERDTree，或者关闭全屏
```

以上是一些基本的用法，平时常用的就几个。

#### 增加一些配置
在使用NERDTree的过程中有一些不太方便的地方就是打开的过个文件不共享NERDTree，所以就需要配合安装一个共享插件[vim-nerdtree-tabs](https://github.com/jistr/vim-nerdtree-tabs)，这就让你赶紧只是打开了一个NERDTree
``` vim
" 关闭NERDTree快捷键
map <leader>t :NERDTreeToggle<CR>
" 显示行号
let NERDTreeShowLineNumbers=1
let NERDTreeAutoCenter=1
" 是否显示隐藏文件
let NERDTreeShowHidden=1
" 设置宽度
let NERDTreeWinSize=31
" 在终端启动vim时，共享NERDTree
let g:nerdtree_tabs_open_on_console_startup=1
" 忽略一下文件的显示
let NERDTreeIgnore=['\.pyc','\~$','\.swp']
" 显示书签列表
let NERDTreeShowBookmarks=1
```

#### 在NERDTree 中显示git信息
开发的过程中，我们希望git信息直接在NERDTree中显示出来，和Eclipse一样，修改的文件和增加的文件都给出相应的标注，这时需要安装的插件就是[nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin)

配置信息如下
``` vim
let g:NERDTreeIndicatorMapCustom = {
    \ "Modified"  : "✹",
    \ "Staged"    : "✚",
    \ "Untracked" : "✭",
    \ "Renamed"   : "➜",
    \ "Unmerged"  : "═",
    \ "Deleted"   : "✖",
    \ "Dirty"     : "✗",
    \ "Clean"     : "✔︎",
    \ "Unknown"   : "?"
    \ }
```
NERDTree配合使用这两个插件文件管理就很棒了，当然如果再加上ctrlp，那就无敌了。

#### 参考
1. [最全的Vim命令](https://blog.csdn.net/scaleqiao/article/details/45153379)






