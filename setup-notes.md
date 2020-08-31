# Setup Notes

## Pre-reqs

* Make sure you have Windows Terminal installed
* Install Ubuntu 18.04
* Install Git for Windows and Ubuntu

## Setting up PowerShell

* [Install PowerLine for Windows](https://docs.microsoft.com/en-us/windows/terminal/tutorials/powerline-setup)

## Setting up Ubuntu

* Install OhMyZsh for Ubuntu
* https://blog.entrostat.com/install-and-configure-zsh/
* https://ohmyz.sh/

```
# install Zsh
sudo apt-get install zsh
# set as default shell
chsh -s $(which zsh)
# zsh
# Upon opening a terminal again you will be asked some setup questions; select the option which populates your configuration with the default system administrator recommended settings.

# install Oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# Install auto-complete plugin
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Add auto-complete to ~/.zshrc
plugins=(
  git
  zsh-autosuggestions
)
```

Change directory colors in Windows

* https://unix.stackexchange.com/questions/94498/what-causes-this-green-background-in-ls-output

```
dircolors -p > ~/.dircolors
vim ~/.dircolors
OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky

In your `.zshrc` file, include:
eval "$(dircolors ~/.dircolors)"
```

## Configure Windows Terminal themes


## Remap Caps-Lock to Escape

Remap your "capslock" key to "escape." Vi was written using an ADM-3A terminal and its keyboard, which you can see here: https://catonmat.net/why-vim-uses-hjkl-as-arrow-keys has the escape-key in a sane place. This should prevent you from having to stretch to hit escape.

To remap your keys on Windows, you need to download Power Toys: https://github.com/microsoft/PowerToys/releases


