## Setup development environment

Make sure XCode is installed


#### Install homebrew
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### Install zsh
```
$ brew install zsh
$ sudo chsh -s /bin/zsh $(whoami)
```

#### Install oh-my-zsh (or prezto)
```
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

#### Add the folowing to the top of ~/.zshrc
```
if [ "$TMUX" = "" ]; then tmux; fi
```

#### Install reattach-to-user-namespace for tmux to work properly
```
$ brew install reattach-to-user-namespace 
``` 

#### Install tmux
```
$ brew install tmux
```

#### ~/.tmux.conf
```
###########################
#  Configuration
###########################

# use 256 term for pretty colors
set -g default-terminal "screen-256color"

# increase scroll-back history
set -g history-limit 5000

# use vim key bindings
setw -g mode-keys vi

set-option -g mouse-select-pane on
set-option -g mouse-select-window on
set-option -g mode-mouse on
set-option -g mouse-resize-pane on

# decrease command delay (increases vim responsiveness)
set -sg escape-time 1

# increase repeat time for repeatable commands
set -g repeat-time 1000

# start window index at 1
set -g base-index 1

# start pane index at 1
setw -g pane-base-index 1

# highlight window when it has new activity
setw -g monitor-activity on
set -g visual-activity on

# re-number windows when one is closed
set -g renumber-windows on

# enable pbcopy and pbpaste
# https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard/blob/master/README.md
set-option -g default-command "reattach-to-user-namespace -l zsh"

###########################
#  Key Bindings
###########################

# tmux prefix
# unbind C-b
# set -g prefix C-j

# copy with 'enter' or 'y' and send to mac os clipboard: http://goo.gl/2Bfn8
unbind -t vi-copy Enter
bind-key -t vi-copy Enter copy-pipe "reattach-to-user-namespace pbcopy"
bind-key -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"

# paste
unbind C-p
bind C-p paste-buffer

# window splitting
# unbind %
# bind | split-window -h
# unbind '"'
# bind - split-window -v

# quickly switch panes
unbind ^J
bind ^J select-pane -t :.+

# force a reload of the config file
unbind r
bind r source-file ~/.tmux.conf \; display "Reloaded!"

###########################
# Status Bar
###########################

# enable UTF-8 support in status bar
set -g status-utf8 on

# set refresh interval for status bar
set -g status-interval 30

# center the status bar
set -g status-justify left

# show session, window, pane in left status bar
set -g status-left-length 40
set -g status-left '#[fg=green]#S#[fg=blue] #I:#P#[default]'

# show hostname, date, time, and battery in right status bar
set-option -g status-right '#[fg=green]#H#[default] %m/%d/%y %I:%M\
 #[fg=red]#(battery discharging)#[default]#(battery charging)'

###########################
# Colors
###########################

# color status bar
# set -g status-bg colour235
# set -g status-fg white
# 
# # highlight current window
# set-window-option -g window-status-current-fg black
# set-window-option -g window-status-current-bg green
# 
# # set color of active pane
# set -g pane-border-fg colour235
# set -g pane-border-bg black
# set -g pane-active-border-fg green
# set -g pane-active-border-bg black

# default statusbar colors
set-option -g status-bg colour235
set-option -g status-fg colour179
set-option -g status-attr default

# default window title colors
set-window-option -g window-status-fg colour244
set-window-option -g window-status-bg default

# active window title colors
set-window-option -g window-status-current-fg colour166
set-window-option -g window-status-current-bg default
set-window-option -g window-status-current-attr bright

# pane border
set-option -g pane-border-fg colour235
set-option -g pane-active-border-fg colour240

# pane number display
set-option -g display-panes-active-colour colour33
set-option -g display-panes-colour colour166
```

#### Setup vim
First make sure vim is upgraded to latest version (Look at MacVim)


#### Install vundle
Just go to this website and RTFM !
https://github.com/VundleVim/Vundle.vim 


