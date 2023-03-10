# lbaseconf
Base configuration for linux system

### Adding sudo permission to main user

```sh
su -
```

```sh
usermod -aG sudo <user name>
```

## Update Repositories and backports
##### Oficial repositories
```sh
deb http://deb.debian.org/debian/ bullseye main 
deb-src http://deb.debian.org/debian/ bullseye main 

deb http://deb.debian.org/debian-security/ bullseye-security main 
deb-src http://deb.debian.org/debian-security/ bullseye-security main 

deb http://deb.debian.org/debian/ bullseye-updates main 
deb-src http://deb.debian.org/debian/ bullseye-updates main 
```
##### non-free repositories
```sh
deb http://deb.debian.org/debian/ bullseye-backports main contrib non-free 
deb-src http://deb.debian.org/debian/ bullseye-backports main contrib non-free 

deb http://deb.debian.org/debian/ bullseye main contrib non-free 
deb-src http://deb.debian.org/debian/ bullseye main contrib non-free 

deb http://deb.debian.org/debian-security/ bullseye-security main contrib non-free 
deb-src http://deb.debian.org/debian-security/ bullseye-security main contrib non-free 

deb http://deb.debian.org/debian/ bullseye-updates main contrib non-free 
deb-src http://deb.debian.org/debian/ bullseye-updates main contrib non-free
```
```sh
sudo apt update
```

## Install nala-legacy
```sh
echo "deb http://deb.volian.org/volian/ scar main" | sudo tee /etc/apt/sources.list.d/volian-archive-scar-unstable.list
```
```sh
wget -qO - https://deb.volian.org/volian/scar.key | sudo tee /etc/apt/trusted.gpg.d/volian-archive-scar-unstable.gpg > /dev/null
```
```sh
sudo apt update
```
```sh
sudo apt install nala-legacy
```

## Install kitty
```sh
sudo nala install kitty
```
###### Press crtl+shift+F2
###### Close the windows
###### Go to the path to modify kitty font size 
```sh
.config/kitty/kitty.conf
```
###### Add the line with the font number, e.g. 20.0
```sh
font_size 20.0
```

## Install silversearcher-ag
```sh
sudo nala install silversearcher-ag
```

### Install Nvidia drivers
##### Debian 11 "Bullseye" add the file to /etc/apt/sources.list
```sh
deb http://deb.debian.org/debian/ bullseye main contrib non-free
```
```sh
sudo nala update
```
```sh
sudo nala install nvidia-driver firmware-misc-nonfree
```

## Install Brave browser

```sh
sudo nala install curl
```
```sh
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
```
```sh
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
```
```sh
sudo nala update
```
```sh
sudo nala install brave-browser
```

## Install tmux
```sh
sudo nala install tmux -y
```

## Install Nodejs and npm
```sh
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
```sh
sudo nala update
```
```sh
sudo nala upgrade
```

##### If nodejs and npm is not installed run the following
```sh
sudo nala install nodejs npm -y
```

## Install vim
```sh
sudo nala install vim
```
```sh
ln -s configs/.vimrc ./.vimrc
```
```sh
ln -s configs/.vim ./.vim
```

##### Install vim-plug [vim-plug doc](https://github.com/junegunn/vim-plug)
```sh
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```

## Install nvim
```sh
sudo nala install neovim
```
##### Create a folder on ~/.confg/ named nvim and inside a file init.vim
```sh
mkdir ./config/nvim
```
```sh
touch init.vim
```
##### In the file init.vim write the following
```sh
set runtimepath^=~/.vim runtimepath+=~/.vim/after
let &packpath=&runtimepath
source ~/.vimrc
```
##### In nvim run the following comand :PlugInstall

## Install zsh
```sh
sudo nala install zsh -y
```
```sh
ln -s configs/.zshrc ./.zshrc
```
##### Install oh my zsh
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
```sh
chsh -s $(which zsh)
```
```sh
ln -s configs/.zshrc .zshrc
```
```sh
cd ~/.oh-my-zsh/custom/plugins
```
```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```
```sh
source ~/.zshrc
```
