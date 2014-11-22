# Console Cowboy

> Can You Jam With The Console Cowboys in Cyberspace?

My carefully curated Vim and Tmux config files. Made for Mac OS X.

![Console Cowboy preview](http://f.cl.ly/items/3t2h1U0v2n322b1H0o3q/console-cowboy.png)

## What's in it?

* [MacVim](https://code.google.com/p/macvim/)
* [iTerm 2](http://www.iterm2.com/)
* [tmux](http://tmux.sourceforge.net/)
* [Ocean Dark Base16 theme](http://chriskempson.github.io/base16/#ocean)

### Vim 

* `,d` brings up [NERDTree](https://github.com/scrooloose/nerdtree), a sidebar buffer for navigating and manipulating files
* `,t` brings up [ctrlp.vim](https://github.com/kien/ctrlp.vim), a project file filter for easily opening specific files
* `,b` restricts ctrlp.vim to open buffers
* `,a` starts project search with [ag.vim](https://github.com/rking/ag.vim) using [the silver searcher](https://github.com/ggreer/the_silver_searcher) (like ack, but faster)
* `ds`/`cs` delete/change surrounding characters (e.g. `"Hey!"` + `ds"` = `Hey!`, `"Hey!"` + `cs"'` = `'Hey!'`) with [vim-surround](https://github.com/tpope/vim-surround)
* `\\\` toggles current line comment
* `\\` toggles visual selection comment lines
* `vii`/`vai` visually select *in* or *around* the cursor's indent
* `,[space]` strips trailing whitespace
* `,l` begins aligning lines on a string, usually used as `,l=` to align assignments
* `<C-hjkl>` move between windows, shorthand for `<C-w> hjkl`
* `<C-]>` & `<C-[>` to move between vim tabs

### Tmux

* `<C-a>` is the prefix
* mouse scroll initiates tmux scroll
* `prefix v` makes a vertical split
* `prefix s` makes a horizontal split

If you have three or more panes:
* `prefix +` opens up the main-horizontal-layout
* `prefix =` opens up the main-vertical-layout

You can adjust the size of the smaller panes in `tmux.conf` by lowering or increasing the `other-pane-height` and `other-pane-width` options.

## Install

    rake

## Customize

In your home directory, Console Cowboy creates a `.vimrc.local` file where you can customize
Vim to your heart’s content.

## ZSH Theme

Colors are a tricky beast. First install [this shell script](https://github.com/chriskempson/base16-shell):

```
git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
```

In order to make iTerm and Vim work add the bottom of your `.zshrc` file:

```
# Base16 Shell
BASE16_SHELL="$HOME/.config/base16-shell/base16-ocean.dark.sh"
[[ -s $BASE16_SHELL ]] && source $BASE16_SHELL
```

## Uninstall

    rake uninstall

Note that this won't remove everything, but your vim configuration should be reset to whatever it was before installing. Some uninstallation steps will be manual.

