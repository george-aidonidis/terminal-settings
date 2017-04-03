# A nice configuration over iTerm2, tmux and vim

## Table of Contents
1. [Screenshots](#screenshots)
2. [iTerm2](#iterm2)
3. [Vundle](#vundle)
4. [Gruvbox theme](#gruvbox-theme)
5. [tmux](#tmux)
6. [Vim airline](#vim-airline)

## Screenshots
After following this small guide your terminal should look like this:
![image][terminal-img]

And a more complicated one (node app running, `vim` and `htop`):
![image][terminal-dev-img]

## iTerm2
- [Here][nightly] you can download iTerm2 nightly build.
- In order to have the top bar the same color with gruvbox go to `Preferences` --> `Profiles` --> `Color` --> `Tab Color` and put **RGB (39, 39, 39**).
## Vundle
- Considering that you have `vim` installed on your system, you can follow the instructions on how to download/setup vundle [here][vundle-tut].

## gruvbox theme
- **iTerm2**: Download [these][gruviterm] files and import them to iTerm2 (from `Preferences` --> `Profiles` --> `Colors` --> `Color Presets` --> `Import...`)
- **vim**: Place below line between `vundle` configuration inside `.vimrc` file:
```sh
call vundle#begin()
...
Plugin 'morhetz/gruvbox'
...
call vundle#end()
```
and run `:PluginInstall`

_More [here][gruv]_

## tmux
- You can install `tmux` via `brew` on mac or use the package manager of your os. You should also install the `reattach-to-user-namespace` package to avoid problems with copy/paste when `tmux` is running (for `mac os`).
```sh
brew install `tmux`
brew install reattach-to-user-namespace
```

- As mentioned above, in order to avoid the copy/paste problem **make sure** you include the following line inside your `.tmux.conf`
```sh
# Fix for copy paste problem when opening an editor inside tmux
set-option -g default-command "reattach-to-user-namespace -l zsh"
```
Or you can `git clone`/download the [.tmux.conf](./.tmux.conf)
## vim airline
- `Vim airline` is used to display information in the status bar on vim. It can be installed as any plugin.
Just place between the `vundle` configuration:
```sh
call vundle#begin()
...
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
...
call vundle#end()
```
Or you can `git clone`/download the [.vimrc](./.vimrc) file.
- And as with any `vundle` plugin you need to run `:PluginInstall`

- Afterwads you need to select the `base16` that suits the `gruvbox` vim theme (in my opinion at least) by running `:AirlineTheme base16`
If you'd like this to be persistent add the following to your `.vimrc` file:
```sh
let g:airline_theme='base16'
```
- More about `vim airline` [here][airline] and about its themes [here][airline-themes]


[nightly]: https://iTerm2.com/downloads/nightly/#/section/home
[gruviterm]: https://github.com/morhetz/gruvbox-contrib/tree/master/iTerm2
[vundle-tut]: https://github.com/VundleVim/Vundle.vim#quick-start
[gruv]: https://github.com/morhetz/gruvbox
[airline]: https://github.com/vim-airline/vim-airline#themes
[airline-themes]: https://github.com/vim-airline/vim-airline/wiki/Screenshots
[terminal-img]: http://i.imgur.com/oSA7DNM.png
[terminal-dev-img]: http://i.imgur.com/VSfdtl5.png