# Terminal-from-scratch

When crash your computer windows or Linux have to have remembered all the stuff installed before to set them again once recover your OS.

This Blog has the purpose to encapsulate all the steps to set again all stuff minimum necessary to start to code again.

---

## Installing google chrome by terminal

First to all update linux

```sh
$ sudo apt update & sudo apt upgrade -y
```

install `wget`

```sh
$ sudo apt install wget
```

download chrome from deb

```sh
$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

install the package with `dpkg`

```sh
$ sudo dpkg -i google-chrome-stable_current_amd64.deb
```

if you have some error during the installation run the command below

```sh
$ sudo apt-get install -f
```

more [Information](https://es.wikihow.com/instalar-Google-Chrome-desde-la-Terminal-en-Linux)

---

## Font installation

Manual font installation
Download these four ttf files:

- [MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

---

## Setting up the terminal

### Installing VS Code

Step 1 - Install wget if not present.

```sh
$ sudo apt update
$ sudo apt -y install wget
```

Step 2 - Add Visual Studio Code repository and key

```sh
$ sudo apt update
$ sudo apt install apt-transport-https
$ curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
$ sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
```

Step 3 - Add APT repository to the system

```sh
$ sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable $ main" > /etc/apt/sources.list.d/vscode.list'
```
Step 4 - Visual Studio Code on

```sh
$ sudo apt update
$ sudo apt install code
```

To launch the text editor type next in the terminal

```sh
$ code
```

### Installing Git

Step 1 - Open the terminal and type 

```sh
$ sudo apt install git-all
```

Step 2 - you can check the git version with

```sh
$ git --version
```

Step 3 - Connect git with github

Configure your e-mail in git (the same as your github account)

```sh
$ git config --global user.email cargdev@example.com
```

Generate the SSH key

```sh
$ ssh-keygen -t rsa -b 4096 -C "cargdev@example.com"
```

Check the key in with the terminal

```sh
$ eval $(ssh-agent)
```

Add the key to Windows

```sh
$ ssh-add ~/.ssh/id_rsa
```

Copy your public key to github locate in --> ~/.ssh/id_rsa.pub
In github go to Account/setting/SSH and GPG keys and add New SSH Key and Add it

![Github key.png](./Image/Github.PNG)

### Installing Nodejs and NPM



Step 1 - Update the system using apt package manager index by running the following command.

```sh
$ sudo apt update
```

Step 2 - Install Node.js global repository by typing

```sh
$ sudo apt install nodejs
```

Step 3 - Confirm the installation of Node.js by typing

```sh
$ node --version
```

Step 4 - Install npm by running following command

```sh
$ sudo apt install npm
```

Step 5 - Confirm the installation of npm by typing

```sh
$ npm --version
```

if need a version in specified, download node from `curl`

```sh
$ cd ~
$ curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
$ sudo apt install nodejs
```

---

## Installing OH-MY-ZSH


Step 1- Installing ZSH and git-core

open the terminal and type next:

```sh
$ sudo apt-get install zsh
$ sudo apt-get install git-core
```

Step 2 - Download ZSH and execute

```sh
$ wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

Step 3 - Change from sheel to ZSH

```sh
$ chsh -s `which zsh`
```

Step 4 - Restart your system

---

## Installing NVIM

Step 1 - Install [Neovim PPA](https://launchpad.net/~neovim-ppa/+archive/ubuntu/unstable)

```sh
$ sudo add-apt-repository ppa:neovim-ppa/unstable
```

then update the packages

```sh
$ sudo apt-get update
$ sudo apt-get install neovim
```

Step 2 - Check the installation

```sh
$ nvim
```

Step 3 - Install the copy clipboard due to NVim can copy to your system

```sh
$ sudo apt install xclip
$ sudo apt install xsel
```

Step 4 - Install [Python interface](https://github.com/neovim/python-client), this because some plugins in NVim use python to work

```sh
$ sudo apt install python3-pip
```

Then install the NVim interface

```sh
$ python3 -m pip install neovim
```

Step 5 - Upgrade python interface

```sh
$ python3 -m pip install --upgrade neovim
```

Step 6 - Install ruby, due to some interfaces from Python use [Ruby](https://rubygems.org/gems/neovim/)

```sh
$ sudo apt install ruby
$ sudo apt install ruby-dev
```

Install Ruby interface

```sh
$ sudo gem install neovim
```

Step 7 - Checl the nvim dependencies

```sh
$ nvim +checkhealth
```

![Github key.png](./Image/checkhealth.png)

Step 8 - Install the plug installator, in this case is vim-plug

In the terminal type the text below
```sh
$ sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```
A minimalist Vim plugin manager.

<img src="https://raw.githubusercontent.com/junegunn/i/master/vim-plug/installer.gif" height="450">

To check how use vim please go to [how use vim](http://vimsheet.com/)

To install the vim configuration I use check my [VIM Repository](https://github.com/CarGDev/Vim-configuration)

---

## Installing autosuggestions and syntax-highlighting for ZSH


### zsh-autosuggestions


Requirements: Zsh v4.3.11 or later

<a href="https://asciinema.org/a/37390" target="_blank"><img src="https://asciinema.org/a/37390.png" width="400" /></a>


Step 1 - Clone this repository into `$ZSH_CUSTOM/plugins` (by default `~/.oh-my-zsh/custom/plugins`)

```sh
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Step 2 - Add the plugin to the list of plugins for Oh My Zsh to load (inside `~/.zshrc`):

```sh
$ plugins=(zsh-autosuggestions)
```

Step 3 - Start a new terminal session.


## zsh-syntax-highlighting

Step 1 - Clone this repository in oh-my-zsh's plugins directory:

```sh
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Step 2 - Activate the plugin in `~/.zshrc`:

```sh
$ plugins=( [plugins...] zsh-syntax-highlighting)
```

Step 3 - Restart zsh (such as by opening a new instance of your terminal emulator).


---

## Installing Powerlevel 10k for ZSH

Step 1 - Install the theme typing next

```sh
$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Step 2 - Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc.

Step 3 -  Restart zsh (such as by opening a new instance of your terminal emulator).

Note: to use all the icons in this theme is recommended use [Meslo Nerd Font](https://github.com/romkatv/powerlevel10k/blob/master/font.md)


---

## Installing ranger for terminal

Download the repository

```sh
$ git clone https://github.com/hut/ranger.git
```

Installing ranger

```sh
$ cd ranger
$ sudo make install
```

check the installation in the terminal

```sh
$ ranger
```

download the configuration

```sh
$ ranger --copy-config=all
```

to modify the files configuration:

```sh
$ cd ~/.config/ranger
```
---
## Installing terminator

Install terminator from the terminal

```sh
$ sudo apt install terminator
```

---

## Installing extensions in Ubuntu

To install gnome extensions install first `chrome-gnome-shell` from the terminal

```sh
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install chrome-gnome-shell
```

In particular I like the extensions below

- [dash-to-dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [arc menu](https://extensions.gnome.org/extension/3628/arcmenu/)
- [Transparent Top Bar](https://extensions.gnome.org/extension/3960/transparent-top-bar-adjustable-transparency/)

for more extensions [click here](https://extensions.gnome.org/)

---

## Installing postman

```sh
$ sudo snap install postman
```

---
## Installing DBeaver

Download DBeaver

```sh
$ wget -O - https://dbeaver.io/debs/dbeaver.gpg.key | sudo apt-key add -
```

and then

```sh
$ echo "deb https://dbeaver.io/debs/dbeaver-ce /" \
| sudo tee /etc/apt/sources.list.d/dbeaver.list
```
after that you can download `DBeaver`

```sh
$ sudo apt update
$ sudo apt install dbeaver-ce
```