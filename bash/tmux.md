# Tmux

## Usage

### Attach a session

`ctrl a + :` `a -t sessio_name`

### Kill a session

`tmux ls` `tmux kill-session -t 9`

### Copy Mode

* search mode space enter
* Open vi Insert ctrl+a \]

### New session

`tmux new -t SESSION_name`

### switch

`ctrl a (`

## Configuration file

unbind C-b  
 set-option -g prefix C-a  
 bind-key C-a send-prefix  
 set-option -g mouse off

set -g history-limit 10000  
 set -g allow-rename off

bind-key j command-prompt -p "join pane from:" "join-pane -s '%%'"  
 bind-key s command-prompt -p "send pane to:" "join-pane -t '%%'"

\#search mode like vi  
 set-window-option -g mode-keys vi

run-shell /home/b3v1l/tmux-logging/logging.tmux  
 \#Colors !

set -g default-terminal "screen-256color"

\#bind -n WheelUpPane if-shell -F -t = "\#{mouse\_any\_flag}" "send-keys -M" "if -Ft= '\#{pane\_in\_mode}' 'send-keys -M' 'select-pane -t=; copy-mode -e; send-keys -M'"  
 \#Bind -N WheelDownPane select-pane -t= ; send-keys -M

\#source-file /home/user/utils/tmux/tmux-themepack/powerline/default/blue.tmuxtheme  
 source-file /home/user/.tmux/powerline.tmuxtheme



