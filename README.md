![NVIM
Setup](https://img.shields.io/badge/NVIM%20Setup-Custom%20Config-blue)

# NVIM / Terminal Configurations

![Terminal
Preview](https://github.com/RussellChubb/nvim_terminal_config_files/blob/main/bg.png?raw=true)

## Why

This is my first foray into configuring both my terminal and NeoVim
setup.\
The setup is intentionally minimal and fits my workflow. I expect this
repository to evolve---especially the NeoVim config, since that
rabbit-hole runs deep.

------------------------------------------------------------------------

# Installation & Setup Guide

## Windows Terminal Configuration

### Appearance Settings

1.  **Appearance → Use acrylic material in tab row → ON**\
2.  **Profiles → PowerShell → Appearance → Color scheme →
    `One Half Dark`**\
3.  **Profiles → PowerShell → Appearance → Enable acrylic material →
    ON**\
4.  **Profiles → PowerShell → Appearance → Background opacity → `60%`**

------------------------------------------------------------------------

## Install Nerd Fonts

1.  Go to: https://www.nerdfonts.com\
2.  Download your preferred NF (I use **CaskaydiaCove Nerd Font Mono**)\
3.  Extract & install\
4.  Set in Windows Terminal:\
    **Profiles → PowerShell → Appearance → Font face →
    `CaskaydiaCove Nerd Font Mono`**

------------------------------------------------------------------------

## Install NeoVim

``` powershell
winget install --id=Neovim.Neovim -e
```

Then:

``` powershell
cd $env:LOCALAPPDATA
mkdir nvim
cd nvim
nvim init.vim
```

Paste in your `init.vim` configuration → save & exit:

``` vim
:wq
```

------------------------------------------------------------------------

## Install Vim Plug

``` powershell
iwr -useb https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim |
  ni $HOME/vimfiles/autoload/plug.vim -Force
```

Then:

``` powershell
cd $env:LOCALAPPDATA
vim
nvim init.vim
```

Inside NeoVim, run:

``` vim
:PlugInstall
:wq
```

------------------------------------------------------------------------

## Install Git

``` powershell
winget install --id Git.Git -e --source winget
```

Generate SSH key:

``` powershell
cd ~/.ssh
ssh-keygen
```

Copy the contents of `id_rsa.pub` → add to GitHub → Settings → SSH Keys.

------------------------------------------------------------------------

## Install Node

``` powershell
winget install -e --id OpenJS.NodeJS
```

------------------------------------------------------------------------

## Install Chocolatey

``` powershell
Set-ExecutionPolicy AllSigned
Set-ExecutionPolicy Bypass -Scope Process -Force; `
  [Net.ServicePointManager]::SecurityProtocol = `
  [Net.ServicePointManager]::SecurityProtocol -bor 3072; `
  iex ((New-Object Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

------------------------------------------------------------------------

## Install NVM (via Chocolatey)

``` powershell
choco install nvm
```

------------------------------------------------------------------------

## Install Yarn for CoC

``` powershell
cd $env:LOCALAPPDATA
vim-data\plugged\coc.nvim
npm install --global yarn
yarn install
yarn build
```

Then:

``` powershell
cd $env:LOCALAPPDATA
vim
nvim init.vim
```

Let updates finish → save & exit.

------------------------------------------------------------------------

## Install CoC-Python

``` powershell
nvim main.py
```

Inside NeoVim:

``` vim
:CocInstall coc-python
:wq
```

------------------------------------------------------------------------

## Install Winfetch

``` powershell
choco install winfetch -y
```

------------------------------------------------------------------------

## Install Oh My Posh

``` powershell
winget install JaneDeDobbeleer.OhMyPosh -s winget
```

Find profile location:

``` powershell
echo $PROFILE
```

Then:

``` powershell
cd ~/OneDrive/Documents
mkdir PowerShell
cd PowerShell
nvim Microsoft.PowerShell_profile.ps1
```

Paste in your profile config → save & exit.

------------------------------------------------------------------------

## Terminal Utilities

### Install Terminal Icons

``` powershell
cd ~/Documents/PowerShell
Install-Module -Name Terminal-Icons -Repository PSGallery -Force
Import-Module Terminal-Icons
```

------------------------------------------------------------------------

### Install PSReadLine Enhancements

``` powershell
cd ~/Documents/PowerShell
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView
```

------------------------------------------------------------------------

### Install Powershell Autocompletion

``` powershell
Notepad $profile
Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete
```

------------------------------------------------------------------------

# System Information

-   **OS:** Windows 11

------------------------------------------------------------------------

# NVIM Plugins Installed

  --------------------------------------------------------------------------
  Plugin                         Description
  ------------------------------ -------------------------------------------
  **vim-surround**               Quickly add/change/delete surroundings like
                                 `() "" ''`.

  **nerdtree**                   File explorer sidebar.

  **vim-commentary**             Toggle comments via `gcc` / `gc`.

  **vim-airline**                Status bar with theme support.

  **pgsql.vim**                  PostgreSQL syntax highlighting.

  **awesome-vim-colorschemes**   Collection of retro and classic themes.

  **vim-devicons**               Adds icons in file explorer.

  **tagbar**                     Sidebar showing code structure.

  **vim-multiple-cursors**       Multi-cursor editing.

  **coc.nvim**                   Language server + autocomplete engine.

  **auto-pairs**                 Auto-close brackets, braces, parentheses.
  --------------------------------------------------------------------------

------------------------------------------------------------------------

# Keyboard Shortcuts

  Shortcut   Function
  ---------- --------------------------
  `<C-f>`    Focus NERDTree window
  `<C-n>`    Open NERDTree
  `<C-t>`    Toggle NERDTree
  `<C-l>`    Jump to definition (CoC)
  `<F8>`     Toggle Tagbar
  `<C-w>w`   Cycle window focus

------------------------------------------------------------------------

# Credits

Special thanks to **[Bek Brace](https://gist.github.com/BekBrace)**,
whose original config I built upon.
