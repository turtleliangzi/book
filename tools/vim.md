# <center>Vim——面向程序员的编辑利器</center>
<center>create at 2017-01-04 by turtle</center>
 <hr>
 <br>

 vim是一款面向程序员的编辑器，即使某些功能无法直接完成，借助其丰富的插件资源，必定可以达到目标，这就是所需即所获。本文着重介绍如何将vim打造成像IDE一样的编辑器，提高开发效率。

 ### 一、vim必知知识

 在正式开始前先介绍几个vim的基本知识点。

 #### （1）.vimrc文件

 .vimrc是控制vim行为的配置文件，位于~/.vimrc，（刚开始，这个文件是不存在的，需要你新建），不论vim窗口外观、显示字体，还是操作方式、快捷键、插件属性均属于可通过编辑该配置文件将vim调教成最适合你的编辑器。

 很多人之所以觉得vim难用，是因为vim缺少默认配置，甚至安装完成后你连配置文件都找不到，不进行任何配置的vim的确很难看、难用。

 前缀键，<leader>，vim中自带很多快捷键，再加上各类插件的快捷键，大量快捷键出现在单层空间中难免引起冲突，为缓解该问题，引入了前缀键<leader>，在.vimrc中定义<leader>键：

 ```
"定义前缀键，即<leader>
let mapleader=";"
```

#### （2）.vim目录

.vim目录是存放所有插件的地方。vim有一套自己的脚本语言，通过这种脚本语言可以实现与vim的交互，达到功能扩展的目的。

#### （3）插件管理器

1、vundle

vundle是比较流行的一款插件管理器，它可以通过某种机制实现批量自动安装、更新、卸载所有插件。

(vundle)[https://github.com/VundleVim/Vundle.vim]

但经常碰到github网络不通畅时，插件下载不下来。

2、pathogen

pathogen需要手动通过git clone下载插件到.vim/bundle目录下，更新和卸载都不是很方便，特别是重新配置vim时，需要再一次手动下载。 但如果你的电脑配置了代理的话，从github下载会很方便。

(pathogen)[https://github.com/tpope/vim-pathogen]

结合以上两种插件管理器的优缺点，本文将同时使用vundle、pathogen插件管理器来管理后面要安装的插件。


### 二、让vim像IDE一样工作

#### （一）安装插件管理器

安装vundle:

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
接下来在.vimrc中增加相关配置信息

```

"vundle配置
set nocompatible
filetype off          

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim

"vundle插件列表必须位于begin和end之间

call vundle#begin()

call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" 插件示例，根据情况进行安装

Plugin 'tpope/vim-fugitive'
Plugin 'L9'
Plugin 'git://git.wincent.com/command-t.git'
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
Plugin 'ascenator/L9', {'name': 'newL9'}

call vundle#end()           
filetype plugin indent on   

```

安装pathogen:

```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```
