# Console Cowboy

> [Can You Jam With The Console Cowboys in Cyberspace?](https://www.youtube.com/watch?v=bLlj_GeKniA)

My carefully curated Vim and Tmux config files. Made for Mac OS X.

## What's in it?

* [iTerm 2](http://www.iterm2.com/)
* [tmux](http://tmux.sourceforge.net/)
* [MacVim](https://code.google.com/p/macvim/)
* [Ocean Dark Base16 theme](http://chriskempson.github.io/base16/#ocean)

## Why You Should Use Vim and TMUX

* Watch [Chris Hunt's great intro talk](https://www.youtube.com/watch?v=9jzWDr24UHQ) about the benefits of using both Vim and TMUX
* Read this great article explaining [why VIM and TMUX are better together](https://blog.bugsnag.com/tmux-and-vim/)
* Check out [Gary Bernhardt quickly switching between VIM and the terminal](https://youtu.be/tdNnN5yTIeM?t=3m05s) so you can get motivated

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
* `<C-]>` & `<C-[>` to move between vim tab
* `s` and `i` to open vertical and horizontal windows from [NERDTree](https://github.com/scrooloose/nerdtree)
* `<C-v>` and `<C-x>` to open vertical and horizontal windows from [ctrlp.vim](https://github.com/kien/ctrlp.vim)

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
BASE16_SHELL=$HOME/.config/base16-shell/
[ -n "$PS1" ] && [ -s $BASE16_SHELL/profile_helper.sh ] && eval "$($BASE16_SHELL/profile_helper.sh)"
```

Start a new shell and then type `base16_ocean` (hit enter)

## Configuring Your Keyboard

It's common and often recommended to reassign the caps lock key to be your modifier key instead. To do this 

    System Preferences > Keyboard > Modifier Keys (bottom right) > assign Caps Lock to use ^Control instead

Next, set Key Repeat and Delay Until Repeat all the way to the right ("fast" and "short" respectively).

## Configuring iTerm

    Preferences > Profiles > [Select Your Profile] > Terminal

Silence the Bell, Enable the flash and disable the Growl messages.  

## Uninstall

    rake uninstall

Note that this won't remove everything, but your vim configuration should be reset to whatever it was before installing. Some uninstallation steps will be manual.

