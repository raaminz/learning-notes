[[tools]]

#### My requirements
- [x] Large font, eye friendly theme
- [x] Finding source files and going back and forth easily 
- [x] Bookmarking sorucefiles
- [x] Full information of current file
- [ ] Debugging
- [x] Searching full texts in project
- [x] Opening different projects in one workspace
- [x] working with Git
- [x] working with Docker
- [x] code refactoring (find and replace occurrences, renaming, moving)
- [x] following logs efficiently
- [ ] Having some playground functionality

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
| C q Tab                       | Insert a tab                  |

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

Navigate easier
* ido  =>  in C x C f , lists all the files in current path
```lisp
(setq ido-everywhere t)
(setq ido-enable-flex-matching t)
(ido-mode t)
```
* Helm
```lisp
(use-package helm
  :ensure t
  :config (helm-mode 1))
```

- Projectile - a series of command only for a project
```lisp
(use-package projectile
  :ensure t
  :config
  (define-key projectile-mode-map (kbd "C-x p") 'projectile-command-map)
  (projectile-mode 1))
```

- C x p f : find a file
- C x p b : switch to another buffer
- C x p p : swithc to another project

```lisp
(use-package helm-projectile
  :ensure t
  :config (helm-projectile-on))
```

- adding dashboard
```lisp
(use-package dashboard
  :ensure t
  :init
  (progn
    (setq dashboard-items '((recents . 1)
			    (projects . 1))))
  (setq dashboard-show-shortcuts t)
  (setq dashboard-center-content nil)
  :config
  (dashboard-setup-startup-hook))
```
C x b \*dashboard\* confirm
M - x dashboard-refresh-buffer

- treemacs
M x treemacs
```lisp
(use-package treemacs
  :ensure t
  :bind
  (:map global-map
	([f8] . treemacs)
	("C-<f8>" . treemacs-select-window))
  :config
  (setq treemacs-is-never-other-window t))
```
inside treemacs
C c C p -> project
C c C w -> workspaces

- treemacs-projectile
```lisp
(use-package treemacs-projectile
  :after treemacs projectile
  :ensure t)
```

## Spacemacs
SPC f e d --> find spacemacs dotfile
SPC h l --> help for layers
SPC b h --> go to home
SPC f s --> save the file
SPC q q --> quit
SPACE * to find text under cursor in project or selected with visual-mode.
SPACE s l to resume last search (yes, that's the letter L).
SPC p f to find a file within a project.

`(setq lsp-keymap-prefix "C-c C-l")`
`M-x customize-option lsp-keymap-prefix`
## Doom emacs
SPC h r r -> fx compile .doom.d/init
