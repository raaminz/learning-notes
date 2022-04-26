[[tools]]

----

#### session
`tmux new -s basic`
`tmux new -s basic -d` create and detach
`tmux kill-session -t basic`

#### #tmux-attach
`tmux list-sessions` OR `tmux ls`
`tmux attach`  attach to the last one
`tmux attach -t second_session`

#### #tmux-windows
`tmux new -s windows -n shell` name the first windows (tab in tmux) shell

### inside tmux
- **exit** -> to exit current windows #tmux-windows 
- press **Ctrl + b** and then
	- **?** -> to see keybinds
	- **t**  -> shows the time
	- **d** -> *detach* the current session #tmux-detach
	- **c** -> create a new window  #tmux-windows 
	- **,** -> rename current window #tmux-windows 
	- **n** -> switch to next windows #tmux-windows 
	- **p** -> switch to previous windows #tmux-windows 
	- **0-...** -> switch to window number #tmux-windows 
	- **w** -> show visual menu to choose window #tmux-windows 
	- **f** , Enter -> find the window you want #tmux-windows 
	- **&** -> to exit current window #tmux-windows 
	- **%** -> divide down from the middle #tmux-pane
	- **"** -> split pane in half #tmux-pane 
	- **o** -> cycle throug the #tmux-pane 
	- **Up-Down-Left-Right** -> move around #tmux-pane 
	- **Spacebar** -> change #tmux-pane layout
		- *even-horizontal* stacks all panes horizontally, left to right.
		- *even-vertical* stacks all panes vertically, top to bottom.
		- *main-horizontal* creates one larger pane on the top and smaller panes underneath.
		- *main-vertical* creates one large pane on the left side of the screen, and stacks the rest of the panes vertically on the right.
		- *tiled* arranges all panes evenly on the screen.
	- **x** -> close current #tmux-pane 
- press **Ctrl + b** -> **:** to enter command
	- *new-window -n console* 
	- *new-window -n process "top"* -> create a window and run the command "top"
		- press *q* to quit the window
