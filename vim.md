[[tools]]

##### NerdTree
- press `m` : manage files

##### map both `caps lock` and `esc` to `esc`
`setxkbmap -option caps:escape`
##### copy paste
- `yy/Y` yank (copy)
- `3yy` to copy 3 lines
- `p` paste
- `P` paster before the cursor
- `y4k` yank 4 lines on top of cursor
- `y$` yank right of the cursor
- `yaw` yank a word
- `y^` yank left of the cursor
- `x`   - delete the current character
- `dd` cut the line
- `3dd` cut 3 lines
- `d$` cut right of the cursor
	- Visual mode
		- `v` normal selecting
		- `V` to select the line
		- `Ctrl + v` select the block
		- `y` yank
		- `d` cut 
		- `p` paste

##### Cursor
- `u` undo
- `o` new line and insert mode
- `0` cursor to begining of line
- `Shift + i` it does `0` and insert mode
- `gg` go to first line
- `5gg` / `5G` go to line 5
- `G` go to last line
- `$` go to end of line
- `A` it does `$` and insert mode

##### tricks
- `vim -u NONE -N`
	- The -u NONE flag tells Vim not to source your vimrc on startup
