"use :help options for a complete list of options
"type :so % to source this file
"type :so $MYVIMRC from any other file to reload vimrc
"
set nocompatible
"----------------------------------------------------------------------"
"OS specific settings
"----------------------------------------------------------------------"
let os = substitute(system('uname'), "\n", "", "")

"----------------------------------------------------------------------"
"Mac OS X
"----------------------------------------------------------------------"
if os == "Darwin"                   "OS X GUI specific
    if has("gui_running")
        colorscheme solarized
		    set background=dark
        set guioptions-=T           "gets rid of top toolbar in macvim
        "set transparency=30
        "set fullscreen
        set autochdir               "automatically cd into file directory
        set cursorline              " Highlight current line
    else                            "mac terminal specific
    colorscheme darkblue
    endif
    "set guifont=courier_new:h14     "terminal and GUI shared options
"----------------------------------------------------------------------"
"Linux
"----------------------------------------------------------------------"
elseif os == "Linux"
    colorscheme desert
    "set guifont=courier_new:h12
"----------------------------------------------------------------------"
"Windows
"----------------------------------------------------------------------"
else    "windows
    set guioptions-=T
    set cursorline                  " Highlight current line
    colorscheme desert
    set guifont=courier_new:h10
    set autochdir                   "automatically cd into file directory
endif
"----------------------------------------------------------------------"

syntax on

"how to set a specific syntax
"cal SetSyn("Python")

"----------------------------------------------------------------------"
"Pathogen settings
"----------------------------------------------------------------------"
call pathogen#infect()
call pathogen#helptags()
filetype plugin on
filetype indent on

"----------------------------------------------------------------------"
"tabbing and indents
"----------------------------------------------------------------------"
set shiftwidth=2
set expandtab
set tabstop=2
set softtabstop=2
set autoindent
set smartindent      "The first setting tells vim to use \"autoindent" (that is, use the current line's indent level to set the indent level of new lines). The second makes vim attempt to intelligently guess the indent level of any new line based on the previous line, assuming the source file is in a C-like language. Combined, they are very useful in writing well-formatted source code.
set smarttab

"----------------------------------------------------------------------"
set showmatch         "This setting will cause the cursor to very briefly jump to a brace/parenthese/bracket's match whenever you type a closing or opening brace/parenthese/bracket. I've had almost no mismatched-punctuation errors since I started using this setting.

"----------------------------------------------------------------------"
set wildmode=longest,full
set wildmenu           "allows to tab complete and tab cycle through filenames in current directory when opening (:e)

"----------------------------------------------------------------------"
set undolevels=1000             " 1000 undos

"----------------------------------------------------------------------"
set noerrorbells
set vb t_vb=                    " Turn off visual bell

"----------------------------------------------------------------------"

" ================ Turn Off Swap Files ==============

set noswapfile
set nobackup
set nowb

"----------------------------------------------------------------------"
"search settings
"----------------------------------------------------------------------"
set hls                       "turn on search highlighting, turn off with set nohls
set incsearch                 "With this nifty option, vim will search for text as you enter it. For instance, if you type /bob to search for bob, vi will go to the first \"b" after you type the \"b," to the first \"bo" after you type the \"o," and so on. It makes searching much faster, since if you pay attention you never have to enter more than the minimum number of characters to find your target location. Make sure that you press Enter to accept the match after vim finds the location you want.

set ruler
set number  "line numbering

"----------------------------------------------------------------------"
"folding settings
"----------------------------------------------------------------------"
set foldenable
set foldmethod=indent     "fold based on indent
set foldnestmax=10        "deepest fold is 10 levels
set nofoldenable          "dont fold by default
set foldlevel=1           "this is just what i use
set backspace=indent,eol,start  "Allow backspace in insert mode
set history=1000                "Store lots of :cmdline history
set showmode                    "Show current mode down the bottom

"Set space to toggle a fold
nnoremap <space> za

"folding colors
:highlight Folded guibg=grey guifg=blue
:highlight FoldColumn guibg=darkgrey guifg=white

set foldtext=""
set foldcolumn=2

"Turn off word wrapping
set nowrap
"set showcmd    " display incomplete commands - I'm not sure what this means

"shows hidden characters (tabs, etc..)
"set list

"hides hidden characters
"set nolist

" ================ Scrolling ========================

set scrolloff=8         "Start scrolling when we're 8 lines away from margins
set sidescrolloff=15
set sidescroll=1

