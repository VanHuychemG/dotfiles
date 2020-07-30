# @cumpsd • dotfiles

## Table of Contents

- [@cumpsd • dotfiles](#cumpsd-•-dotfiles)
  - [Goal](#goal)
  - [Prerequisites on an Ubuntu based machine](#prerequisites-on-an-ubuntu-based-machine)
  - [Setup an Ubuntu based machine](#setup-an-ubuntu-based-machine)
  - [Setup GPG](#setup-gpg)
  - [Post Install steps on WSL](#post-install-steps-on-wsl)
    - [Windows Font Install](#windows-font-install)
  - [More configuration sync](#more-configuration-sync)
    - [VS Code](#vs-code)
  - [Credits](#credits)
    - [Dotfiles](#dotfiles)
    - [Misc](#misc)
    - [Resources](#resources)

## Goal

> Make my life easier when setting up a machine.

## Prerequisites on an Ubuntu based machine

```bash
# Add Ansible and Git
sudo apt-get update
sudo apt-get install ansible git software-properties-common pinentry-tty
```

## Setup an Ubuntu based machine

```bash
# Get the dotfiles
git clone --recurse-submodules https://github.com/cumpsd/dotfiles.git <your preferred location>/dotfiles
cd <your preferred location>/dotfiles

# Setup the system
./setup-system

# In case you want to have a GUI, run the following instead:
./setup-system --with-gui

# At this point, it might be needed to explicitly run fisher and Oh My Fish! to get our shell setup
fish
fisher
# fish/oh-my-fish/bin/install --offline
omf install
fish_update_completions
```

## Setup GPG

```bash
# Import our existing GPG keys
gpg2 --import <key>

# Trust our imported key
gpg --edit-key user@domain.com

gpg> trust

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
And don't forget to save the changes:

gpg> save

# Unlock the dotfiles repo
git-crypt unlock

# Use SSH for remote
git remote set-url origin git@github.com:cumpsd/dotfiles.git

# At this point you can clone all the repos by running:
repos/setup.sh
```

## Post Install steps on WSL

### Windows Font Install

- Download [Nerd Fonts Hack](https://github.com/ryanoasis/nerd-fonts/releases/download/v1.2.0/Hack.zip)
- Extract and install the required fonts (everything which ends with `Complete Mono Windows Compatible.ttf`)
- Set default console font to Hack NF, 14

## More configuration sync

### VS Code

- Install `shan.code-settings-sync`
- Press `Shift + Alt + D` it will ask your GitHub Gist ID.
- All VS Code settings are getting synced, whenever you change something you can upload them with `Shift + Alt + U` or turn on Auto-Upload with `Sync : Advanced Options > Toggle Auto-Upload on Settings Change`
- More info at https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync

## Credits

### Dotfiles

- [dotbot](https://github.com/anishathalye/dotbot) - A tool that bootstraps your dotfiles ⚡️

### Misc

| Where | What |
| --- | --- |
| [oh-my-fish](https://github.com/oh-my-fish/oh-my-fish) | The Fishshell Framework. |
| [fisherman](https://github.com/fisherman/fisherman) | The fish-shell plugin manager. |
| [theme-bobthefish](https://github.com/oh-my-fish/theme-bobthefish) | A Powerline-style, Git-aware fish theme optimized for awesome. |
| [nerd-fonts](https://github.com/ryanoasis/nerd-fonts) | Iconic font aggregator, collection, and patcher. |
| [dircolors-solarized](https://github.com/seebi/dircolors-solarized/) | Solarized dircolors. |
| [git-crypt](https://github.com/AGWA/git-crypt) | Transparent file encryption in git. |
| [thefuck](https://github.com/nvbn/thefuck) | Magnificent app which corrects your previous console command. |
| [GNU Privacy Guard](https://gnupg.org/) | All things encryption. |

### Resources

| Where | What |
| --- | --- |
| [Increasing development productivity with repository management](https://blog.kalis.me/increasing-development-productivity-repository-management/) | System to easily manage repositories. |
