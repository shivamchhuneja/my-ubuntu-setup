# My Ubuntu Dev Setup (base is Omakub)

This repository is a complete backup of my Linux development environment, created on Ubuntu 24.04. It contains all my config files and the list of packages I use so I can easily recreate this exact setup on any new machine. It’s built for development in Go, Java, Python, and MySQL, and uses tools like LazyVim (with Rose Pine Moon theme), Alacritty, Zellij, and Ulauncher. Shell preferences and configs for both zsh and bash are also included.

To get started, first clone this repository:

git clone https://github.com/shivamchhuneja/my-ubuntu-setup.git  
cd my-ubuntu-setup

Next, restore all packages using the saved dpkg package list. This will safely install any missing packages without affecting the ones already installed:

sudo apt update  
sudo apt install -y dselect  
sudo dpkg --set-selections < packages.list  
sudo apt-get dselect-upgrade -y

Once the packages are installed, restore your configuration files:

cp -r configs/lazyvim/nvim ~/.config/nvim
cp -r configs/alacritty/alacritty ~/.config/alacritty
cp -r configs/zellij/zellij ~/.config/zellij
cp -r configs/ulauncher/ulauncher ~/.config/ulauncher
cp .zshrc ~/
cp .bashrc ~/

If you prefer using zsh, make it your default shell:

chsh -s $(which zsh)

To set up LazyVim from scratch, you can clone the starter config like this:

git clone https://github.com/LazyVim/starter ~/.config/nvim  
nvim

Then overwrite it with the config from this repo:

cp -r ./nvim ~/.config/

If any dependency issues show up, fix them with:

sudo apt --fix-broken install  
sudo apt autoremove

For proper icon and theme support in tools like LazyVim and Alacritty, it’s recommended to install a Nerd Font. FiraCode Nerd Font works well. You can download & install it on your system, and set it as the default font in your terminal settings.
