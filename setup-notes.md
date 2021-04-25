# Setup Notes

**Overview**
* Pre-reqs
* Powershell
* Ubuntu
* Themes

## Pre-reqs

* Make sure you have Windows Terminal installed
* Install Ubuntu 18.04
* Install Git for Windows and Ubuntu

## Install Windows Terminal

* https://docs.microsoft.com/en-us/windows/terminal/

## Install Git (setup SSH)

* Install Git: https://git-scm.com/download/win
  * Don't create a start menu folder. You'll be doing everything in VIM anyway. 
* Setup SSH:
 * https://medium.com/dev-genius/set-up-ssh-key-and-git-integration-in-windows-10-native-way-c9b94952dd2c
 * https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh)

Open Git Bash from the Start menu. Make sure to run it as an administrator.

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Don't follow the instructions to use Git Bash for OpenSSH. Instead use the built-in Windows OpenSSH.

``
Get-Content "~/.ssh/id_ed25519.pub" | Set-Clipboard
```

* Note that x-clip doesn't work in WSL, use `clip.exe < ~/.ssh/id_rsa.pub` instead.
* Use SSH Agent: https://stackoverflow.com/questions/48843643/using-git-with-powershell-and-ssh-key-with-passphrase

## Setting up PowerShell

* TODO: create custom `profile.ps1` file
* [You may run into issues with executing the profile as a non-administrator](https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/whats-wrong-with-my-windows-powershell/f05e72f2-a429-4ee0-81fb-910c8c8a1306?auth=1), you should run

```
set-executionpolicy remotesigned
```

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
eval `$dircolors ~/.dircolors`
```

## Configure Windows Terminal themes

## Remap Caps-Lock to Escape

Remap your "capslock" key to "escape." Vi was written using an ADM-3A terminal and its keyboard, which you can see here: https://catonmat.net/why-vim-uses-hjkl-as-arrow-keys has the escape-key in a sane place. This should prevent you from having to stretch to hit escape.

To remap your keys on Windows, you need to download Power Toys: https://github.com/microsoft/PowerToys/releases
