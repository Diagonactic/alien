# alien

[![GitHub tag](https://img.shields.io/github/tag/eendroroy/alien.svg)](https://github.com/eendroroy/alien/tags)

[![Contributors](https://img.shields.io/github/contributors/eendroroy/alien.svg)](https://github.com/eendroroy/alien/graphs/contributors)
[![GitHub last commit (branch)](https://img.shields.io/github/last-commit/eendroroy/alien/master.svg)](https://github.com/eendroroy/alien)
[![license](https://img.shields.io/github/license/eendroroy/alien.svg)](https://github.com/eendroroy/alien/blob/master/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/eendroroy/alien.svg)](https://github.com/eendroroy/alien/issues)
[![GitHub closed issues](https://img.shields.io/github/issues-closed/eendroroy/alien.svg)](https://github.com/eendroroy/alien/issues?q=is%3Aissue+is%3Aclosed)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/eendroroy/alien.svg)](https://github.com/eendroroy/alien/pulls)
[![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/eendroroy/alien.svg)](https://github.com/eendroroy/alien/pulls?q=is%3Apr+is%3Aclosed)

**alien** theme is faster than a lot other themes. **Why?** It updates part of the prompt asyncronously - the time consuming processings like git status checking, git dirty copy checking etc. **How?** It starts a background job for these process, and in the mean time draws initial prompt and lets you use the terminal as you would normally.

alien theme is **independent** of any library like Oh-My-Zsh or Prezto. Whatever it needs already included inside. The only exception is font. You need to **install the powerline patched fonts** to properly display the prompt.

## About the Fork - Change Log from Original

The upstream `alien` prompt is a great project and I strongly recommend those finding this repository to use it ahead of this one unless the added features are (a) still not available in upstream or (b) are unnecessary for what you do dday-to-day.  While I'm likely to keep this up-to-date and add features to it (since **I** really like the way this prompt works and don't see replacing my use of it anytime soon), I'm not terribly interested in supporting this fork outside of my own needs.  If it proves popular enough, I'll see about a pull request with upstream (assuming they're at all interested in what I've tweaked).

This is a small fork of the alien theme to add the hostname for easier identification when I'm SSHed into a remote host so that I don't accidentally run the wrong command in the wrong place.  It also updates the prompt when a user runs `sudo -i`, providing the name of the user who ran `sudo` in addition to the current user (usually `root` unless `sudo -iu` was used).

I have every expectation that this fork would work for others desiring that funcitonality, however, I wrote it quick and dirty for myself after accidentally smoking a home directory on my server (due to, bingo, not realizing I had alt-tabbed into the wrong Alacritty window).

I also use `zplugin` with the included [zsh module](https://github.com/zdharma/zplugin#more-on-zplugin-zsh-module).  This results in all directories containing zsh scripts to get an additional `.zwc`, compiled, zsh script.  Normally, I'd update the `.gitmodules` to ignore dirty modules, along with updating the `.git/config/module/**/exclude` files to eliminate the `.zwc` files, however, since I use this every day and want things clean/up-to-date, I have forked the submodules and updated this script to point to them.

I will be including a script to pull from the upstream `alien` repo and patch it with changes from this repository (heck, it might already be there since there's a relatively good chance that I've updated the code before I hit up the REAMDE again)

...and becuase I use zplugin, I have updated the instructions below to include install instructions (very basic -- it could be done significantly better, I presume).  These instructions will also work for the original project if you change the repo name accordingly

## Requirements

- zsh (obviously)
- powerline patched fonts [**see here**](https://github.com/powerline/fonts)

## Installation

Add the following line to your .zshrc depending on your zsh plugin manager

##### [antigen](https://github.com/zsh-users/antigen):

```zsh
antigen theme Diagonactic/alien alien
```

##### [zgen](https://github.com/tarjoilija/zgen):

```zsh
zgen load Diagonactic/alien
```

##### [zplug](https://github.com/zplug/zplug):

```zsh
zplug "Diagonactic/alien"
```

##### [zplugin](https://github.com/zdharma/zplugin):

```zsh
zplugin load Diagonactic/alien
# Using light instead of load will probably work, but I haven't tested it
# There's also likely some ice configuration that would make this better but I'm in a hurry (-8
```

##### [oh-my-zsh: Overriding and Adding Themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Customization#overriding-and-adding-themes)

##### Manually clonning

```bash
git clone https://github.com/eendroroy/alien.git
cd alien
git submodule update --init --recursive
```

Add the following line to your `~/.zshrc`

```bash
source ~/alien/alien.zsh
```

## Asciicast v1.0.3

[![asciicast](http://asciinema.org/a/162085.png)](https://asciinema.org/a/162085)

###### color scheme

**add all configurations before plugin definitions**

you can chose from 3 different color schemes (blue is the default)

in ~/.zshrc just add any from the following three lines before your `antigen theme ...` line

```bash
export ALIEN_THEME="blue"
```

![blue](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/blue.png)

```bash
export ALIEN_THEME="green"
```

![green](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/green.png)

```bash
export ALIEN_THEME="red"
```

![red](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/red.png)

```bash
export ALIEN_THEME="soft"
```

![soft](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/soft.png)

```bash
export ALIEN_THEME="gruvbox"
```

![gruvbox](https://raw.githubusercontent.com/eendroroy/alien/master/screenshots/gruvbox.png)


**Custom Color**

```bash
color0=018      # time background color
color1=226      # normal background color
color1r=196     # normal error background color
color2=254      # time foreground color
color3=026      # user background color
color4=254      # user foreground color
color5=045      # dir background color
color6=019      # dir foreground color
color7=238      # vcs background color
color8=228      # prompt foreground color
color9=051      # vcs foreground color
color10=244     # git left-right background color
color11=255     # git left-right foreground color
color12=253     # dirty copy background color
color13=016     # dirty copy foreground color
color14=245     # venv color
```

Or creating a new theme file:

__/path/to/custom/theme.zsh__

```bash
#!/usr/bin/env zsh

alien_theme(){
  color0=018    # time bg
  color1=226    # init bg
  color1r=196   # init bg error
  color2=254    # time fg
  color3=026    # user bg
  color4=254    # user fg
  color5=045    # dir bg
  color6=019    # dir fg
  color7=238    # vcs bg
  color8=228    # prompt fg
  color9=051    # vcs fg
  color10=244   # lr bg
  color11=255   # lr fg
  color12=253   # dirty copy bg
  color13=016   # dirty copy fg
  color14=245   # venv color
}
```

Then activate the theme using:

```bash
export ALIEN_CUSTOM_THEME_PATH=/path/to/custom/theme.zsh
```

###### date format

```bash
export ALIEN_DATE_TIME_FORMAT=%H:%M:%S # default is %r
```

###### nerd font

Enable Nerd Font

```bash
export USE_NERD_FONT=1
```

_*Note: [Nerd fonts](https://github.com/ryanoasis/nerd-fonts)*_

### promptlib-zsh Configs:

#### customize symbols

```bash
export ALIEN_GIT_SYM=G
export ALIEN_HG_SYM=H
export ALIEN_SVN_SYM=S
export ALIEN_BRANCH_SYM=
# Symbols from promptlib
export PLIB_GIT_ADD_SYM=+
export PLIB_GIT_DEL_SYM=-
export PLIB_GIT_MOD_SYM=⭑
export PLIB_GIT_NEW_SYM=?
export PLIB_GIT_PUSH_SYM=↑
export PLIB_GIT_PULL_SYM=↓
```

_Note: this overrides `USE_NERD_FONT` configuration._

#### customize colors

```bash
export PLIB_GIT_TRACKED_COLOR=green
export PLIB_GIT_UNTRACKED_COLOR=red
```

## Libraries Used

- ['256color'](https://github.com/chrissicool/zsh-256color) by **[@chrissicool](https://github.com/chrissicool)**
- ['zsh-async'](https://github.com/mafredri/zsh-async) by **[@mafredri](https://github.com/mafredri)**
- ['promptlib-zsh'](https://github.com/eendroroy/promptlib-zsh) by **[@eendroroy](https://github.com/eendroroy)**

## Author

* **indrajit** - *Owner* - [eendroroy](https://github.com/eendroroy)

## License

The project is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
