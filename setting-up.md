# Getting Setup (Optional)
If you want to skip this step navigate [to the hacker101 website.](https://www.hacker101.com/start-here)  <br>
**I will be using Manjaro KDE, an Arch Linux based distribution, commands may be different on your machine**  <br>
Follow along [here](https://github.com/Hacker0x01/hacker101?tab=readme-ov-file)
## Prerequisites:
git: <br>
To install git on Arch Linux distributions run: `sudo pacman -S git`
## Getting started:
The hacker101 course has the option for the user to clone the github repo and run the website locally using Ruby and the bundler gem. I chose this option because I have no experience with Ruby, Rubygems, Arch User Repositories. 
## Setting up rbenv:
Follow along here: https://github.com/rbenv/rbenv  <br>
rbenv is a version manager for ruby, we will use it to setup and manage our ruby apps and version.
Because I am on an arch linux distribution, rbenv does not have an official repository, instead we will need to use Arch User Repositories (AUR). If you want to learn more about AUR you can either 
explore the [wiki](https://aur.archlinux.org/) or take a look at my basic crash course [here.](https://github.com/danithen/AUR-crashcourse) Let's get started. <br>
### Make a new subdirectory in your home directory: <br>
`mkdir AUR` <br>
### Clone the rbenv git into your AUR directory: 
`git clone https://aur.archlinux.org/rbenv.git ~/AUR` <br>
### Navigate to the rbenv subdirectory in AUR:
`cd ~/AUR/rbenv`
### Make your package: 
`makepkg`
### Copy the tar.zst file, and run:
`sudo pacman -U rbenv-1.2.0-1-any.pkg.tar.zst`
## Prequisites:
Before we can install ruby we need to install the [ruby-build](https://aur.archlinux.org/packages/ruby-build) dependency. Follow the same steps we used to install rbenv, clone this into the AUR directory. <br>
**We also need to make sure we have some basic tools:** <br>
`sudo pacman -S base-devel`
## Installing Ruby:
### Get the latest version of Ruby:
`rbenv install -l`
### Set a ruby version to finish (My version is 3.3.5):
`rbenv global 3.3.5`
#### If you have any issues during your install refer to the official [rbenv](https://github.com/rbenv/rbenv) guide.
## Ruby Gems:
### Before we install gems, we need to install the rubygems dependency:
`sudo pacman -S rubygems`
### Install bundler
`gem install bundler`
### Following along with ARCH Linux?
Did you get this warning? WARNING:You don't have /home/user/.local/share/gem/ruby/3.2.0/bin in your PATH, gem executables will not run. <br>
### To fix it: <br>
#### Open the .zshrc (.bashrc if you are using bash) file in nano: <br>
`nano ~/.zshrc` <br>
#### At the end of the file copy and paste: <br>
`export PATH="$HOME/.local/share/gem/ruby/3.2.0/bin:$PATH"` <br>
#### Save and exit the file: <br>
`Ctrl+S, Ctrl+X` <br>
#### Reload Shell Config: <br>
`source ~/.zshrc`
#### What did we just do?
We commited /home/user/.local/share/gem/ruby/3.2.0/bin to the PATH variable. PATH is the set of directories that the system looks through when you try to run an executable. The error we got earlier was simply saying that the directory where the gems were stored was not apart of our PATH, so the gems we install would not be executable.
## Booting up our Hacker101 server:
### Simply Run:
`bundle exec jekyll serve`
### Browse to:
`http://localhost:4000`
## Next Up: Lesson 1
