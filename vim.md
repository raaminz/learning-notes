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
- `diw` delete inner word
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
- `$` cursor go to end of line
- `A` it does `$` and insert mode
- `gg` go to first line
- `5gg` / `5G` go to line 5
- `G` go to last line
- `H` move to top of screen
- `M` move to middle of screen
- `L` move to bottom of screen
- `G` go to the last line of the document
- `}`  jump to next paragraph (or function/block, when editing code)
- `{` jump to previous paragraph (or function/block, when editing code)

##### Scrolling (https://vim-jp.org/vimdoc-en/scroll.html)
- `Ctrl-Y` scroll window up
- `Ctrl-U` scroll half a screen up
- `Ctrl-B` scroll a full screen up
- `Ctrl-E` scroll window down
- `Ctrl-D` scroll half a screen down
- `Ctrl-F` scroll a full screen down

##### tricks
- `vim -u NONE -N`
	- The -u NONE flag tells Vim not to source your vimrc on startup
