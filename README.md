
# Note_keeping  <!-- omit in toc --> 

## Summary 

- [Summary](#summary)
- [instaling zsh](#instaling-zsh)
- [Easy Hardware Sensors](#easy-hardware-sensors)
  - [Ram memory](#ram-memory)
- [Other Software Instalation](#other-software-instalation)
  - [Discord](#discord)
  - [Spotify](#spotify)
  - [Vivaldi](#vivaldi)
  - [Vs Code](#vs-code)
    - [Extentions List:](#extentions-list)
    - [Json:](#json)
  - [Github For Desktop](#github-for-desktop)
  - [xjournalpp](#xjournalpp)
    - [Change Colors:](#change-colors)
- [Programing stuff](#programing-stuff)
  - [C](#c)
  - [Python](#python)
  - [Poetry](#poetry)
  - [Docker](#docker)
  - [postbird](#postbird)
  - [Front End](#front-end)
    - [Node.js](#nodejs)
    - [Yarn](#yarn)
    - [Killing Process in LocalHost](#killing-process-in-localhost)
  - [Java](#java)
- [Gnone Extensions and Theme](#gnone-extensions-and-theme)
  - [Keyboard Shortcuts:](#keyboard-shortcuts)
- [Monitor issues on Ubuntu](#monitor-issues-on-ubuntu)


## instaling zsh

guide to setting up Oh my zsh the way i like it on ubuntu
```zsh
sudo apt-get update && sudo apt-get upgrade
sudo apt install git-core zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sudo apt install fonts-powerline
chsh -s $(which zsh)
## relog to take effect
```

Chosen THEME: [Powerlevel10k](https://github.com/romkatv/powerlevel10k)

Chosen plugins needed to install:
- [syntax highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [autossugestions](https://github.com/zsh-users/zsh-autosuggestions)
- [you should use](https://github.com/MichaelAquilina/zsh-you-should-use#installation)

plugins=(git zsh-syntax-highlighting zsh-autosuggestions sudo web-search copybuffer jsontools you-should-use)
___

## Easy Hardware Sensors

```zsh
sudo apt install hddtemp lm-sensors
hddtemp
sensors
```

install display with: https://extensions.gnome.org/extension/841/freon/

### Ram memory
```zsh
sudo dmidecode --type 17 
```
___

## Other Software Instalation

### Discord
```zsh
sudo snap instal discord
```

ps: if discord bugs on the preview:
> ~/snap/discord/130/.config/discord
> delete "settings.json"

### Spotify

```zsh
snap install spotify
```

### Vivaldi

https://vivaldi.com/download/
```zsh
sudo apt install ./vivaldi_download_name.deb
```

### Vs Code
```zsh
sudo snap install --classic code
```

#### Extentions List:
- community matherial theme darker high contrast
- indent rainbow
- markdown all in one
- drakula theme
- auto close tag
- auto rename tag
- file utils
- open in browser
- prettier
- vscode-icons
- docker
- HTML to CSS autocompletion
- omni theme
- better comments

#### Json:

```json
{
    /* VSCODE STUFF */
    "workbench.iconTheme": "vscode-icons",
    "workbench.colorTheme": "Omni",
    "editor.formatOnSave": true,
    "editor.bracketPairColorization.enabled": true,
    "editor.guides.bracketPairs": "active",
    "editor.tabSize": 4,
    "editor.suggestSelection": "first",
    "editor.mouseWheelZoom": true,
    "breadcrumbs.enabled": false,
    "editor.renderWhitespace": "none",
    "explorer.confirmDelete": false,
    "editor.acceptSuggestionOnEnter": "off",
    "explorer.confirmDragAndDrop": false,
    "editor.glyphMargin": false, //no debugger
    "editor.folding": true,
    "terminal.integrated.fontFamily": "MesloLGS NF",
    "window.menuBarVisibility": "toggle",
    "editor.snippetSuggestions": "top",
    "emmet.showSuggestionsAsSnippets": true,
    "editor.rename.enablePreview": false,
    "vsicons.dontShowNewVersionMessage": true,
    "workbench.experimental.layoutControl.enabled" : true,
    "workbench.experimental.layoutControl.type": "both",

    /* FILES STUFF */
    "files.exclude": {
        "**/*.exe": true,
        "**/__pycache__": true,
    },

    /* PYTHON STUFF */
    "python.formatting.provider": "black",
    "python.formatting.blackArgs": [
        "-t",
        "py37"
    ],
    "python.linting.flake8Args": [
        "--ignore=E501",
        "perFile-ignores = __init__py:F401"
    ],
    // "[markdown]": {
    //     "editor.defaultFormatter": "tehnix.vscode-tidymarkdown"
    // },

    /* C STUFF */
    "[c]": {
        "editor.formatOnSave": false,
    },

    /* KITE STUFF */
    // "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    // "kite.showWelcomeNotificationOnStartup": false,

    /* IDENT RAINBOW */
    "indentRainbow.colorOnWhiteSpaceOnly": true,
    "indentRainbow.colors": [
        // "rgba(255,255,64,0.07)",
        // "rgba(127,255,127,0.07)",
        // "rgba(255,127,255,0.07)",
        // "rgba(79,236,236,0.07)"
        // "rgba(255, 0 , 0,0.3)",

        "rgba(255, 184, 108 ,0.15)",
        "rgba(255, 117, 181 ,0.15)",
        "rgba(69, 169, 249 ,0.15)",
        "rgba(176, 132, 235 ,0.15)",
        "rgba(230, 230, 230 ,0.15)",
        "rgba(25, 249, 216 ,0.15)",

    ],



    /* PRETTIER AND WEB DEV STUFF */
    "prettier.tabWidth": 2,
    "auto-close-tag.SublimeText3Mode": true,
    "emmet.includeLanguages": {
        "javascript": "javascriptreact",

    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true,
        "editor.tabSize": 2,
    },
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true,
        "editor.tabSize": 2,
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true,
        "editor.tabSize": 2,
    },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true,
        "editor.tabSize": 2,
    },
    
    // "npm.enableScriptExplorer": true,
}
```

### Github For Desktop
```zsh
sudo wget https://github.com/shiftkey/desktop/releases/download/release-2.9.3-linux3/GitHubDesktop-linux-2.9.3-linux3.deb
### Uncomment below line if you have not installed gdebi-core before
# sudo apt-get install gdebi-core 
sudo gdebi GitHubDesktop-linux-2.9.3-linux3.deb
```

### xjournalpp
```zsh
sudo add-apt-repository ppa:apandada1/xournalpp-stable
sudo apt install xournalpp
```

#### Change Colors:

in `~/.config/xournalpp/palette.gpl`

```txt
GIMP Palette
Name: Xournal Default Palette
#
250 116 191 fA74bf
251 91 104 fb5b68
0 192 255 00c0ff
98 114 164 6272a4
189 147 249 bd93f9
139 233 253 8be9fd
80 250 123 50fa7b
255 184 108 ffb86c
241 250 140 f1fa8c
248 248 242 f8f8f2
119 136 153 lightslategray
```
___

## Programing stuff

### C
```zsh
sudo apt install gcc
```

### Python
```zsh
sudo apt install libpq-dev python3-dev
sudo apt-get install python3-distutils
sudo apt-get install python3.10-distutils
sudo apt install libpq-dev python3.10-dev
```

### Poetry
```zsh
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3.10 -
### uninnstalling
curl https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py > get-poetry
python3 get-poetry --uninstall
```

Poetry env path: `~/.cache/pypoetry/virtualenvs`

Python dev libs: Black && IceCream

### Docker
- Follow [documentation](https://docs.docker.com/engine/install/ubuntu/)
- Do the [groupadd](https://docs.docker.com/engine/install/linux-postinstall/)
- `docker pull postgres`
- docker run --name postgresql-container -p 5432:5432 -e POSTGRES_PASSWORD=somePassword -d postgres

### postbird
```zsh
sudo snap install postbird
```

### Front End

#### Node.js
[documentation](https://github.com/nodesource/distributions#debinstall)
```zsh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
## You may also need development tools to build native addons:
sudo apt-get install gcc g++ make
## build-essentials
sudo apt-get install -y build-essential
#####
# npx create-react-app my-app
# cd my-app
# npm start
sudo npm install tar@6 -g
```

#### Yarn
```zsh
npm install --global yarn
# yarn create react-app my-app
```
or
```zsh
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn
```

#### Killing Process in LocalHost
```zsh
lsof -i tcp:port_number
kill -9 PID
```

### Java
```zsh
sudo apt install default-jre
```

___

## Gnone Extensions and Theme

- gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```zsh
sudo apt install gnome-shell-extensions
sudo apt install gnome-tweak-tool
# https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep
sudo apt install chrome-gnome-shell
```
- get the 'unite' extention to get rid of title bars
- https://extensions.gnome.org/extension/1160/dash-to-panel/
- Theme:
  - https://www.pling.com/p/1275087
  - https://www.pling.com/p/1013714

### Keyboard Shortcuts:
- move to workspace above  super+page up
- move to workspace below  super+page down
- copy a screenshot of an area to clipbloard	super+shift+s
- add system monitor shortcut
	- command: gnome-system-monitor
	- shortcut: alt+q

___

## Monitor issues on Ubuntu

If ubuntu doesn't recgonize the output of monitors use `xrandr`
```zsh
xrandr
## take a note of the monitor output name
cvt width height hz
## coppy the line it will spit out
sudo xrandr --newmode cvt_Modeline
sudo xrandr --addmode monitor_name Modeline_quotes
sudo xrandr --output monitor_name --mode Modeline_quotes
gedit ~/.profile
## to edit the mode in
```
