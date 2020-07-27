# linux-setup

    sudo apt-get update
    sudo apt-get install -y vim mosh tmux htop git curl wget unzip zip gcc build-essential make

### Configure SSH:

    sudo vim /etc/ssh/sshd_config
        AllowUsers www
        PermitRootLogin no
        PasswordAuthentication no

### Restart SSH server, change www user password:

    sudo service ssh restart
    sudo passwd www
    
### Install [oh-my-zsh:](https://github.com/robbyrussell/oh-my-zsh)

    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    chsh -s $(which zsh)


### Install python 3.8

    wget https://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz ; \
    tar xvf Python-3.8.5 ; \
    cd Python-3.8.5 ; \
    mkdir ~/.python ; \
    ./configure --enable-optimizations --prefix=/home/www/.python ; \
    make -j8 ; \
    sudo make altinstall

### Update pip:

    sudo /home/www/.python/bin/python3.8 -m pip install -U pip

### Delite python.tgz and python directorн

    rm -rf Python-3.8.5.tgz Python-3.8.5/
### vim ~/.zshrc and add code
    export PATH=$PATH:/home/www/.python/bin
##### restart .zshrc
    source ~/.zshrc
---
# setup Vim
    git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
		
#### vim ~/.vimrc	
    set nocompatible              " be iMproved, required
    filetype off                  " required
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    Plugin 'VundleVim/Vundle.vim'
    Plugin 'tpope/vim-fugitive'
    Plugin 'git://git.wincent.com/command-t.git'
    Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
    call vundle#end()            " required
    filetype plugin indent on    " required

##### Launch vim and run

	:PluginInstall
#### vim ~/.vimrc
add code

	Plugin 'flazz/vim-colorschemes'
	Plugin 'tpope/vim-surround'
	
	" Настройки табов для Python, согласно рекоммендациям
	set tabstop=4 
	set shiftwidth=4
	set smarttab
	set expandtab "Ставим табы пробелами
	set softtabstop=4 "4 пробела в табе
	" Автоотступ
	set autoindent
	" Подсвечиваем все что можно подсвечивать
	let python_highlight_all = 1
	" Включаем 256 цветов в терминале, мы ведь работаем из иксов?
	" Нужно во многих терминалах, например в gnome-terminal
	set t_Co=256

	" Перед сохранением вырезаем пробелы на концах (только в .py файлах)
	autocmd BufWritePre *.py normal m`:%s/\s\+$//e ``
	" В .py файлах включаем умные отступы после ключевых слов
	autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class

	syntax on "Включить подсветку синтаксиса

	" set nu "Включаем нумерацию строк
	set mousehide "Спрятать курсор мыши когда набираем текст
	set mouse=a "Включить поддержку мыши
	set termencoding=utf-8 "Кодировка терминала
	set novisualbell "Не мигать 
	set t_vb= "Не пищать! (Опции 'не портить текст', к сожалению, нету)
	" Удобное поведение backspace
	set backspace=indent,eol,start whichwrap+=<,>,[,]
	" Вырубаем черточки на табах
	set showtabline=1

	" Переносим на другую строчку, разрываем строки
	set wrap
	set linebreak

	" Вырубаем .swp и ~ (резервные) файлы
	set nobackup
	set noswapfile
	set encoding=utf-8 " Кодировка файлов по умолчанию
	set fileencodings=utf8,cp1251

	set clipboard=unnamed
	set ruler

	set hidden
	nnoremap <C-N> :bnext<CR>
	nnoremap <C-P> :bprev<CR>

	" Выключаем звук в Vim
	set visualbell t_vb=

	"Переключение табов по CMD+number для MacVim
	if has("gui_macvim")
		" Press Ctrl-Tab to switch between open tabs (like browser tabs) to 
		" the right side. Ctrl-Shift-Tab goes the other way.
		noremap <C-Tab> :tabnext<CR>
		noremap <C-S-Tab> :tabprev<CR>

		" Switch to specific tab numbers with Command-number
		noremap <D-1> :tabn 1<CR>
		noremap <D-2> :tabn 2<CR>
		noremap <D-3> :tabn 3<CR>
		noremap <D-4> :tabn 4<CR>
		noremap <D-5> :tabn 5<CR>
		noremap <D-6> :tabn 6<CR>
		noremap <D-7> :tabn 7<CR>
		noremap <D-8> :tabn 8<CR>
		noremap <D-9> :tabn 9<CR>
		" Command-0 goes to the last tab
		noremap <D-0> :tablast<CR>
	endif

	set guifont=Monaco:h18
	colorscheme OceanicNext

##### Launch vim and run
	:PluginInstall
