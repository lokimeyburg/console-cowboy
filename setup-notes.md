# Setup Notes

**Overview**
* Pre-reqs
* Install Git
* Setting up PowerShell, Powerline and Fonts
* Ubuntu

## Pre-reqs

* Visual Studio Code: https://code.visualstudio.com/
* Windows Terminal: https://docs.microsoft.com/en-us/windows/terminal/

## Install Git (setup SSH)

Install Git: https://git-scm.com/download/win. Don't create a start menu folder. You'll be doing everything in VIM anyway. 

**Setup SSH**

Note: open PowerShell as Administrator. Start > PowerShell > Run as administrator.

First you will need to enable OpenSSH Agent which comes with Windows. Go to Start > Search > Services. Find and double-click on OpenSSH Authentication Agent. Select Startup type to Automatic (Delayed Start). Then select 'start' to run the service. 

You can also manually start the service by running
```
Start-Service ssh-agent
```

**Generate your SSH keys**
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
For the location question, just hit enter. Choose your passphrase.

Then add your keys
```
ssh-add C:\Users\lomeybur\.ssh\id_ed25519
```
Copy your keys to your clipboard
```
Get-Content "~/.ssh/id_ed25519" | Set-Clipboard
```
**Upload to Github**

Go to Github > Settings > SSH and GPG keys. Create a new key and upload the one copied to your clipboard. Next, you can test it out in your terminal.
```
ssh -T git@github.com
```
Set your Git credentials
```
git config --global user.name "<github name>"
git config --global user.email <name@email.com>
```

Setup your SSH keys to always sign your commits. Create a file called `config` in `~/.ssh/config` (where your SSH keys are found). Add the following to the file:

```
[user]
	name = <github full name>
	email = <email@address.com>
[core]
	sshCommand = C:/Windows/System32/OpenSSH/ssh.exe
```

## Setting up PowerShell, Powerline and Fonts

Note: open PowerShell as Administrator. Start > PowerShell > Run as administrator. Set execution policy to allow profiles to be executed.

```
set-executionpolicy remotesigned
```

Install PowerLine
```
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
Install-Module -Name PSReadLine -Scope CurrentUser -Force -SkipPublisherCheck
```

Setup Microsoft.PowerShell_profile.ps1
```
code $PROFILE
```

Then add the following to the file:

```
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
```

Restart Windows Terminal to see if PowerLine works for you. Next you will need to install the Cascadia Code fonts and use the `Cascadia Code PL` font. Download the fonts here: https://github.com/microsoft/cascadia-code. Be sure to install the True-Type Fonts (TFF). Once that's done, go to Windows Terminal > Settings > Windows PowerShell > Appearance. Set the Font Face to `Cascadia Code PL`, color scheme to `One Half Dark` and font-weight to `11`. You should also go to Visual Studio Code and set your fonts and terminal fonts to use Cascadia Code PL and install the `One Dark Theme` to match Windows Temrinal.

Links:
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
