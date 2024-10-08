# Getting Setup (Optional)
If you want to skip this step navigate to the hacker101 [website](https://www.hacker101.com/start-here).  <br>
**I will be using Manjaro, an Arch Linux based distribution, commands may be different on your machine**  <br>
Follow along [here](https://github.com/Hacker0x01/hacker101?tab=readme-ov-file).
## Prerequisites:
### git: <br>
To install git on Arch Linux distributions run: `sudo pacman -S git`
## Getting started:
The hacker101 course has the option for the user to clone the github repo and run the website locally using Ruby and the bundler gem. I chose this option because I have no experience with Ruby, Rubygems, Arch User Repositories. 
## Setting up rbenv:
Follow along here: https://github.com/rbenv/rbenv  <br>
rbenv is a version manager for ruby, we will use it to setup and manage our ruby apps and version.
Because I am on an arch linux distribution, rbenv does not have an official repository, instead we will need to use Arch User Repositories (AUR). If you want to learn more about AUR you can 
explore the [wiki](https://aur.archlinux.org/). Let's get started. <br>
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
## More Prequisites:
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
### Clone the hacker101 repository:
`git clone https://github.com/Hacker0x01/hacker101.git`
### In the new hacker101 directory run:
`bundle install`
### Finally Run:
`bundle exec jekyll serve`
### Browse to:
`http://localhost:4000`
## Next Up: [Lesson 1](https://github.com/danithen/hacker101-writeup/blob/main/lesson-1.md)
### Lessons Learned:
During this setup process I learned quite a bit about a few topics. This was my first experience with **AUR**, packaging and installing non official repositories will definitely be useful down the line. I spent a long time reading the **ARCH** wiki, this really helped guide me. One of the most frustrating parts of this process was my installed gems not showing as executable commands. It took me quite a while to figure out that my **big** issue was actaully quite small really easy to fix, and after a few wiki articles it was fixed. **Jekyll** was also a new concept to me so I decided to do a bit of research into it, and it is basically a static site generator for blogs that uses ruby. 
