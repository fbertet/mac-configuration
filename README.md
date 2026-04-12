# Mac configuration

[![GitHub License](https://img.shields.io/github/license/fbertet/mac-configuration?label=License)](LICENSE)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196?logo=conventionalcommits&logoColor=white)](https://conventionalcommits.org)

<p align="center">
  <img src="logo.png" alt="Ansible logo" width="150">
</p>

<p align="center">
  <em>An Ansible playbook to configure my mac for software development</em>
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#prerequisites">Prerequisites</a> •
  <a href="#run-playbook">Run Playbook</a> •
  <a href="#additional-manual-steps">Manual steps</a> •
  <a href="#acknowledgments">Acknowledgments</a> •
  <a href="#license">License</a>
</p>

---

## Overview

This ansible playbook installs and configures most of the software I use on my Mac for software development.

Some things in macOS are difficult to automate, so I still have a few manual installation steps (See below).


## Prerequisites

Before using this ansible playbook:
* Turn ON the mac and follow the initial configuration steps,
* Update Mac OS to its latest version,
* Log in to the App Store


## Run playbook

In the terminal:
``` sh
# Install Apple's command line tools.
xcode-select --install

# Install Ansible.
pip3 install --upgrade pip
pip3 install ansible

# Add Python3 and Homebrew binaries to $PATH
export PATH="$PATH:$HOME/Library/Python/3.9/bin:/opt/homebrew/bin"

# Download this repository to local drive.
cd $HOME/Documents && mkdir -p Perso/Projects/GitHub && cd Perso/projects/GitHub
curl -L -o main.zip "https://github.com/fbertet/mac-configuration/archive/refs/heads/main.zip"
unzip main.zip && rm main.zip
cd mac-configuration-main

# Install Ansible dependencies and run playbook.
ansible-galaxy install -r requirements.yml
ansible-playbook playbooks/main.yml --ask-become-pass
```

Once completed, restart the Mac to ensure all changes are applied.


## Additional manual steps

Some things can't be automated... or aren't worth the time 😅

### MacOS System Settings

* In `Wallpaper`, replace default wallpaper
* In `Displays`, setup Main Display resolution to `More Space`
* In `Desktop & Dock`, setup Default web browser to `Firefox`
* In `Keyboard` > `Keyboard Shortcuts...` > `Spotlight`, uncheck `Show Spotlight search`
* In `Touch ID & Password` > Setup left and right indexes

NB: Guide made for Mac OS 26.4, the menus might change -> use the search bar.

### Finder

* Add ~/Desktop/Screenshots directory to sidebar.

### Raycast

Open Raycast and setup the shortcut to `Cmd+Space`.

### SSH Key(s)

* Generate a SSH Key: `ssh-keygen -t ed25519 -C <email_address>`
* When asked, generate a passphrase and add it to password manager.
* Add ssh key to ssh-agent: `ssh-add ~/.ssh/id_ed25519`
* Add the SSH key to GitHub/GitLab profile(s).

### Git configuration

* Replace email address in `~/.gitconfig` if necessary

### Apps to setup

Open apps and setup:
* Bitwarden
* Slack
* Spotify
* Signal
* Wireguard
* Firefox

### Firefox Plugins

Open Firefox and install:
* [Auto Tab Discard](https://addons.mozilla.org/fr/firefox/addon/auto-tab-discard/)
* [Bitwarden](https://addons.mozilla.org/fr/firefox/addon/bitwarden-password-manager/)
* [Dark Reader](https://addons.mozilla.org/fr/firefox/addon/darkreader/)
* [I still don't care about cookies](https://addons.mozilla.org/en-US/firefox/addon/istilldontcareaboutcookies/)
* [uBlock Origin](https://addons.mozilla.org/fr/firefox/addon/ublock-origin/)


## Acknowledgments

- Mac collection for Ansible: https://github.com/geerlingguy/ansible-collection-mac
- osx-command-line-tools Ansible role: https://github.com/elliotweiser/ansible-osx-command-line-tools
- Awesome macOS Command Line: https://github.com/herrbischoff/awesome-macos-command-line


## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.
