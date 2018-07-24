### 安装
```
brew install vim // Mac
```
### 新手指南
```
vimtutor // vim 教程
```

### 移动光标
```
# hjkl
# 2w 向前移动两个单词
# 3e 向前移动到第 3 个单词的末尾
# 0 移动到行首
# $ 当前行的末尾
# gg 文件第一行
# G 文件最后一行
# 行号+G 指定行
# <ctrl>+o 跳转回之前的位置
# <ctrl>+i 返回跳转之前的位置
```

### 退出
```
# <esc> 进入正常模式
# :q! 不保存退出
# :wq 保存后退出
```

### 删除
```
# x 删除当前字符
# dw 删除至当前单词末尾
# de 删除至当前单词末尾，包括当前字符
# d$ 删除至当前行尾
# dd 删除整行
# 2dd 删除两行
```

### 修改
```
# i 插入文本
# A 当前行末尾添加
# r 替换当前字符
# o 打开新的一行并进入插入模式
```

### 撤销
```
# u 撤销
# <ctrl>+r 取消撤销
```
### 复制粘贴剪切
```
# v 进入可视模式
# y 复制
# p 粘贴
# yy 复制当前行
# dd 剪切当前行
```

### 文件
```
# :e! 强制刷新该文件
# <ctrl>+g 显示当前行以及文件信息
```

### 查找
```
# / 正向查找（n：继续查找，N：相反方向继续查找）
# ？ 逆向查找
# % 查找配对的 {，[，(
# :set ic 忽略大小写
# :set noic 取消忽略大小写
# :set hls 匹配项高亮显示
# :set is 显示部分匹配
```
### 替换
```
# :s/old/new 替换该行第一个匹配串
# :s/old/new/g 替换全行的匹配串
# :%s/old/new/g 替换整个文件的匹配串
```
### 折叠
```
# zc 折叠
# zC 折叠所有嵌套
# zo 展开折叠
# zO 展开所有折叠嵌套
```

### 执行外部命令
```
# :!shell 执行外部命令
```

### 字体
```
# <ctrl> - 缩小
# <ctrl> shift + 放大
# <ctrl> 0 还原
```

### 分屏
```
$ Ctrl+W v  // 左右
$ Ctrl+W s  // 上下

# 移动光标
$ Ctrl+W h/j/k/l  // 左/上/下/右

# 移动分屏
$ Ctrl+W H/J/K/L  // 左/上/下/右

# 修改屏幕尺寸
$ Ctrl+W =/+/-
```

## 基本配置
.vimrc 是 Vim 的配置文件，需要我们自己创建
```
cd 系统用户根目录
touch .vimrc
```
### 常用设置 
```
//1. 取消备份
set nobackup    
set noswapfile
  
//2. 文件编码
set encoding=utf-8 
  
//3. 查找
set ic  
set hls  
set is

//4. 显示行号
set number

//5. 显示光标当前位置
set ruler

//6. 设置缩进
set cindent
set tabstop=2
set shiftwidth=2

//7. 突出显示当前行
set cursorline

//8. 左下角显示当前 vim 模式
set showmode

// 9. 代码折叠
set nofoldenable
```

------

### 待续...........
### 参考
1. [让 vim 成为我们的神器](https://segmentfault.com/a/1190000011466454)
2. [Vim 配置vim airline](https://github.com/hokein/Wiki/wiki/Vim-%E9%85%8D%E7%BD%AEvim-airline)



