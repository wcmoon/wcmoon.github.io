---
title: vim 配置记录
date: 2021-02-07 09:32:17
tags:
- tmux
categories:
- 工具
img: https://blog-cdn.wcmoon.com/tool.jpg
---

vim 配置记录
```
set nu
set cul
set ai
syntax on
set mouse=a
set selection=exclusive
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
" git repos on your local machine (i.e. when working on your own plugin)
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}
Plugin 'scrooloose/nerdtree'
" All of your Plugins must be added before the following line
Plugin 'mattn/emmet-vim'
Plugin 'hail2u/vim-css3-syntax'
Plugin 'groenewege/vim-less'
Plugin 'Raimondi/delimitMate'
Plugin 'scrooloose/syntastic'
Plugin 'Shougo/neco-vim'
Plugin 'majutsushi/tagbar'
Plugin 'jiangmiao/auto-pairs'
Plugin 'vim-airline/vim-airline'
Plugin 'c.vim'
Plugin 'gorodinskiy/vim-coloresque'
Plugin 'sheerun/vim-polyglot'
Plugin 'artur-shaik/vim-javacomplete2'
Plugin 'pangloss/vim-javascript'
Plugin 'alvan/vim-closetag'
Plugin 'Yggdroot/indentLine'
Plugin 'maksimr/vim-jsbeautify'
Plugin 'othree/html5.vim'
Plugin 'othree/javascript-libraries-syntax.vim'
Plugin 'sickill/vim-monokai'
Plugin 'Shougo/neocomplete.vim'
Plugin 'Shougo/neosnippet'
Plugin 'Shougo/neosnippet-snippets'
Plugin 'ervandew/supertab'
Plugin 'OmniCppComplete' 
Plugin 'othree/jspc.vim'
Plugin '1995eaton/vim-better-javascript-completion'
Plugin 'tomasr/molokai' 
Plugin 'digitaltoad/vim-pug' 
Plugin 'dNitro/vim-pug-complete' 
Plugin 'itspriddle/vim-jquery'
Plugin 'posva/vim-vue'
Plugin 'myhere/vim-nodejs-complete'
Plugin 'heavenshell/vim-jsdoc'
Plugin 'isRuslan/vim-es6'
Plugin 'leshill/vim-json'
Plugin 'rhysd/vim-clang-format'
Plugin 'geoffharcourt/vim-matchit'
Plugin 'vim-scripts/indentpython.vim'
Plugin 'jelera/vim-javascript-syntax'
Plugin 'AutoComplPop'
Plugin 'shawncplus/phpcomplete.vim'
Plugin 'mxw/vim-jsx'
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this lineet selectmode=mouse,key
set showmatch
set tabstop=4
set shiftwidth=4
set expandtab
inoremap jj <Esc>
map <F5> :NERDTreeMirror<CR>
map <F5> :NERDTreeToggle<CR>
let NERDTreeShowHidden=1
let NERDTreeWinPos=0

function ShortTabLabel ()
    let bufnrlist = tabpagebuflist (v:lnum)
    let label = bufname (bufnrlist[tabpagewinnr (v:lnum) -1])
    let filename = fnamemodify (label, ':t')
    return filename
endfunction
set guitablabel=%{ShortTabLabel()}

inoremap ' ''<ESC>i
inoremap " ""<ESC>i
inoremap ( ()<ESC>i
inoremap [ []<ESC>i
inoremap { {<CR>}<ESC>O
inoremap <C+k> <ESC>la 


let g:pmenu_scheme = 'dark'
let g:snipMate = {}
let g:snipMate.scope_aliases = {}
let g:javascript_scope_aliases = 'javascript,javascript-react,javascript-es6-react'
let g:snipMate.scope_aliases['javascript'] = g:javascript_scope_aliases
let g:snipMate.scope_aliases['javascript.jsx'] = g:javascript_scope_aliases
let g:tsuquyomi_javascript_support = 1
let g:tsuquyomi_completion_detail = 0
let g:tsuquyomi_completion_preview = 0
let g:tsuquyomi_auto_open = 0


" Jedi 配置
let g:jedi#auto_initialization = 1
let g:jedi#popup_on_dot = 1
let g:jedi#popup_select_first = 0
let g:jedi#show_call_signatures = "1"
autocmd FileType python setlocal completeopt-=preview

set completeopt=preview,menu
set completeopt=longest,menu
set autowrite

```
