### Requirements

Your Computer must connect the Internet and be installed Git & Vim.

### Key Mapping & Tutorial

[Key Mapping & Tutorial](https://www.evernote.com/shard/s257/sh/6c0d6c01-9f19-4f27-87c9-57f4f0b01bad/82297dec2e813f765157cf5f5be95b16) (Only Chinese version currently.)

### Installation

If ~/.vimrc and ~/.vim/ exist, then backup your original vim config

```bash
mv ~/.vimrc ~/.vimrc.old
mv ~/.vim ~/.vim.old
```

Then do following steps.

1. Download this repo:  

 ```bash  
git clone https://github.com/chetui/dotfiles.git
 ```

2. Put files in your home:  

 ```bash  
 mv dotfiles/vim/.vimrc ~  
 mv dotfiles/vim/.vim ~  
 mv dotfiles/vim/.ycm_extra_conf.py ~  
 ```

3. Download the plugin mamage plugin:  

 ```bash
 git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/vundle
 ```

4. Install all the plugins:  

 ```bash
 vim +BundleInstall +qall 
 ```

5. Fix a bug of WinManager:  

 ```bash
 vim ~/.vim/bundle/winmanager/plugin/winmanager.vim
 ```

 add **exe 'q'** in following position:  
 
 ```bash
      function! <SID>ToggleWindowsManager()
        if IsWinManagerVisible()
           call s:CloseWindowsManager()
        else
           call s:StartWindowsManager()
           exe 'q'   
        end
     endfunction
 ```

6. Install python syntax checker lib:  
  ```
  sudo apt-get install python-pip
  sudo pip install flake8
  ```
  
7. [Optional] Syntax-based code completion plugin:  

  Configure YouCompleteMe:  
  7.1 Remove neocomplcache plugin:  

  ```bash
  vim ~/.vimrc
  ```
  Comment neocomplcache plugin:

  ```bash
  "Bundle 'Shougo/neocomplcache'
  
  ...
  
  
  "" Plugin: neocomplcache {
  "...
  "" }
  ```
  Remove neocomplcache plugin:
  
  ```bash
  rm -rf ~/.vim/bundle/neocomplcache/
  ```
  7.2 Install YouCompleteMe plugin:
  
  ```bash
  vim ~/.vimrc
  ```
  Uncomment YouCompleteMe plugin:
  
  ```bash
  Bundle 'Valloric/YouCompleteMe'
  
  ...
  
  " Plugin: YouCompleteMe {
  ...
  " }
  ```
  Install YouCompleteMe plugin:
  
  ```bash
  vim +BundleInstall +qall
  ```
  
  7.3 Configure C/C++ header files paths:
  
  ```bash
  echo | clang -std=c++11 -stdlib=libc++ -v -E -x c++ -
  ```
  Add the output paths after ***#include <...> search starts here:*** into ~/.ycm_extra_conf.py. 
  Notice insert ***'-isystem'*** before each paths.
  For example:
  
  ```bash
  flags = [
  
  ...
  
  '-isystem',
  '/output/path/one',
  '-isystem',
  '/output/path/two',
  ]
  ```
  
  7.4 YouCompleteMe plugin need to be compiled.  
  You can follow the [official install guide](https://github.com/Valloric/YouCompleteMe).  
  It is very easy for Mac OS X and Ubuntu 14.04 to install it. For other Debian-based distro, e.g Ubuntu 12.04, you need to compile and update your Vim first.  
  [Official install guide for Mac OS X](https://github.com/Valloric/YouCompleteMe#mac-os-x-super-quick-installation)  
  [Official install guide for Ubuntu Linux x64](https://github.com/Valloric/YouCompleteMe#ubuntu-linux-x64-super-quick-installation)
