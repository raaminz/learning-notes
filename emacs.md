[[tools]]

#### My requirements
- [ ] Large font, solarized theme
- [ ] Finding source files and going back and forth easily 
- [ ] Bookmarking sorucefiles
- [ ] Full information of current file
- [ ] Debugging
- [ ] Searching full texts in project
- [ ] Opening different projects in one workspace
- [ ] Working with Git
- [ ] working with Docker
- [ ] code refactoring (find and replace occurrences, renaming, moving)
- [ ] following logs efficiently

| command                       | meaning                       |
| ----------------------------- | ----------------------------- |
| C g                           | Cancel / Quit                 |
| M x ...type                   | Search a function             |
| C h  ... type                 | Ask for help                  |
| C h k ...command              | What is this command          |
| C x 0                         | Delete window                 |
| C x 1                         | Delete other window           |
| C x C b                       | Open buffer list              |
| M x switch-to-buffer someName | Create a new buffer           |
| C x C s                       | save-buffer                   |
| C x C k                       | kill-buffer                   |
| C x C f                       | fine-file                     |
| C n                           | next-line                     |
| C p                           | previous-line                 |
| C b                           | back in line                  |
| C f                           | forward in line               |
| C shift n                     | select next lines             |
| C w                           | kill (cut) text (kill-region) |
| C y                           | yank (paste) text             |
| M w                           | Copy (kill and save)          |
| C x 2                         | split-window-below            |
| C x 3                         | split-window-right            |
| C /                           | undo                          |
| C f C /                       | redo                          |
| C x o                         | Cycle through buffers         |
| C x 5 2                       | New freame                    |
| C x 5 o                       | cycle through frames          |
| C x 5 1                       | Delte other frames            |
| M x org-mode                  |                               |
| M x describe-mode             |                               |
| C x h                         | Select all                    |
|                               |                               |

create a file ~/emacs.d/init.el
https://melpa.org/#/getting-started
add melpa
Copy instruction
C e -> to run the file

M x package-refresh-contents

.emacs.d/ init.el first file to load

use-package -> decoration to use simply emacs packages
ensures it's load and add hooks
no need to config them 
```lisp
(unless (package-installed-p 'use-package)
  (package-refresh-contents)
  (package-install 'use-package))
```

which-key -> if you say C x and wait , it shows available commands
```lisp
(use-package which-key
  :ensure t
  :config (which-key-mode))
```

doom-themes
```lisp
(use-package doom-themes
  :ensure t
  :config (load-theme 'doom-solarized-light))
```

`M-x customize-group RET doom-modeline RET`