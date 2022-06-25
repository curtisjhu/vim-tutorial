# Vim Cheatsheet
Everything you need to know about default vim in one page
Of course, the best way to learn is to use it.
```
$ vimtutor
```

Table of Contents
- [Cursor Movement](#cursor-movement)
- [Macros](#macros)
- [Insert Mode](#insert-mode)
- [Editing Mode](#editing-mode)
- [Visual Mode](#visual-mode)
- [Exiting](#exiting)
- [Copy and Paste](#copy-and-paste)
- [Registers](#registers)
- [Working with Multiple Files](#working-with-multiple-files)
- [Indenting](#indenting)
- [Tabs](#tabs)
- [Options](#options)
- [Search](#search)
- [Diff](#diff)
- [Marks and Positions](#marks-and-positions)
- [Global](#global)
- [Non-Vim](#Non-Vim commands)

### Cursor Movement
(in order of most helpful to least helpful)
**Moving**
- h - left ⬅
- j - down ⬇
- k - up ⬆
- l - right ➡

**Jumping in a line**
- w - jump forwards to the start of a word
- W - jump forwards to the start of a word (words can contain punctuation)
- e - jump forwards to the end of a word
- E - jump forwards to the end of a word (words can contain punctuation)
- b - jump backwards to the start of a word
- B - jump backwards to the start of a word (words can contain punctuation)
- ge - jump backwards to the end of a word
- gE - jump backwards to the end of a word (words can contain punctuation)

- 0 - jump to the start of the line
- ^ - jump to the first non-blank character of the line
- $ - jump to the end of the line
- g_ - jump to the last non-blank character of the line
- % - move to matching character (default supported pairs: '()', '{}', '[]' - use :h matchpairs in vim for more info)

**Jumping around a document**
- gg - go to the first line of the document 🔝
- G - go to the last line of the document 🎬

- } - jump to next paragraph (or function/block, when editing code) ﹛ ⬅
- { - jump to previous paragraph (or function/block, when editing code) ➡️ ｝

- gj - move cursor down (multi-line text)
- gk - move cursor up (multi-line text)

- H - move to top of screen
- M - move to middle of screen
- L - move to bottom of screen
- zz - center cursor on screen

- 5gg or 5G - go to line 5
- gd - move to local declaration
- gD - move to global declaration
- fx - jump to next occurrence of character x
- tx - jump to before next occurrence of character x
- Fx - jump to the previous occurrence of character x
- Tx - jump to after previous occurrence of character x
- ; - repeat previous f, t, F or T movement
- , - repeat previous f, t, F or T movement, backwards

**shifting screen**
- Ctrl + e - move screen down one line (without moving cursor)
- Ctrl + y - move screen up one line (without moving cursor)
- Ctrl + b - move back one full screen
- Ctrl + f - move forward one full screen
- Ctrl + d - move forward 1/2 a screen
- Ctrl + u - move back 1/2 a screen

### Macros
- q[char] - record macro [char]
- q - stop recording macro
- @[char] - run macro [char]
- @@ - rerun last run macro

### Insert Mode
- i - insert before the cursor
- I - insert at the beginning of the line
- a - insert (append) after the cursor
- A - insert (append) at the end of the line
- o - append (open) a new line below the current line
- O - append (open) a new line above the current line
- ea - insert (append) at the end of the word
- Ctrl + h - delete the character before the cursor during insert mode
- Ctrl + w - delete word before the cursor during insert mode
- Ctrl + j - begin new line during insert mode
- Ctrl + t - indent (move right) line one shiftwidth during insert mode
- Ctrl + d - de-indent (move left) line one shiftwidth during insert mode
- Ctrl + n - insert (auto-complete) next match before the cursor during insert mode
- Ctrl + p - insert (auto-complete) previous match before the cursor during insert mode
- Ctrl + rx - insert the contents of register x
- Ctrl + ox - Temporarily enter normal mode to issue one normal-mode command x.
- Esc - exit insert mode

### Editing Mode
- r - replace a single character.
- R - replace more than one character, until ESC is pressed.
- J - join line below to the current one with one space in between
- gJ - join line below to the current one without space in between
- gwip - reflow paragraph
- g~ - switch case up to motion
- gu - change to lowercase up to motion
- gU - change to uppercase up to motion
- cc - change (replace) entire line
- c$ or C - change (replace) to the end of the line
- ciw - change (replace) entire word
- cw or ce - change (replace) to the end of the word
- s - delete character and substitute text
- S - delete line and substitute text (same as cc)
- xp - transpose two letters (delete and paste)
- u - undo
- U - restore (undo) last changed line
- Ctrl + r - redo
- . - repeat last command

### Visual Mode
- v - start visual mode, mark lines, then do a command (like y-yank)
- V - start linewise visual mode
- o - move to other end of marked area
- Ctrl + v - start visual block mode
- O - move to other corner of block
- aw - mark a word
- ab - a block with ()
- aB - a block with {}
- at - a block with <> tags
- ib - inner block with ()
- iB - inner block with {}
- it - inner block with <> tags
- Esc - exit visual mode
- \> - shift text right
- < - shift text left
- y - yank (copy) marked text
- d - delete marked text
- ~ - switch case
- u - change marked text to lowercase
- U - change marked text to uppercase

### Exiting
- :w - write (save) the file, but don't exit
- :w !sudo tee % - write out the current file using sudo
- :wq or :x or ZZ - write (save) and quit
- :q - quit (fails if there are unsaved changes)
- :q! or ZQ - quit and throw away unsaved changes
- :wqa - write (save) and quit on all tabs

### Copy and Paste
- yy - yank (copy) a line
- 2yy - yank (copy) 2 lines
- yw - yank (copy) the characters of the word from the cursor position to the start of the next word
- yiw - yank (copy) word under the cursor
- yaw - yank (copy) word under the cursor and the space after or before it
- y$ or Y - yank (copy) to end of line
- p - put (paste) the clipboard after cursor
- P - put (paste) before cursor
- gp - put (paste) the clipboard after cursor and leave cursor after the new text
- gP - put (paste) before cursor and leave cursor after the new text
- dd - delete (cut) a line
- 2dd - delete (cut) 2 lines
- dw - delete (cut) the characters of the word from the cursor position to the start of the next word
- diw - delete (cut) word under the cursor
- daw - delete (cut) word under the cursor and the space after or before it
- d$ or D - delete (cut) to the end of the line
- x - delete (cut) character

### Registers
- :reg[isters] - show registers content
- "xy - yank into register x
- "xp - paste contents of register x
- "+y - yank into the system clipboard register
- "+p - paste from the system clipboard register
- 0 - last yank
- " - unnamed register, last delete or yank
- % - current file name
- \# - alternate file name
- \* - clipboard contents (X11 primary)
- \+ - clipboard contents (X11 clipboard)
- / - last search pattern
- : - last command-line
- . - last inserted text
- \- - last small (less than a line) delete
- = - expression register
- _ - black hole register

### Working with multiple files
- :e[dit] file - edit a file in a new buffer
- :bn[ext] - go to the next buffer
- :bp[revious] - go to the previous buffer
- :bd[elete] - delete a buffer (close a file)
- :b[uffer]# - go to a buffer by index #
- :b[uffer] file - go to a buffer by file
- :ls or :buffers - list all open buffers
- :sp[lit] file - open a file in a new buffer and split window
- :vs[plit] file - open a file in a new buffer and vertically split window
- :vert[ical] ba[ll] - edit all buffers as vertical windows
- :tab ba[ll] - edit all buffers as tabs
- Ctrl + ws - split window
- Ctrl + wv - split window vertically
- Ctrl + ww - switch windows
- Ctrl + wq - quit a window
- Ctrl + wx - exchange current window with next one
- Ctrl + w= - make all windows equal height & width
- Ctrl + wh - move cursor to the left window (vertical split)
- Ctrl + wl - move cursor to the right window (vertical split)
- Ctrl + wj - move cursor to the window below (horizontal split)
- Ctrl + wk - move cursor to the window above (horizontal split)
- Ctrl + wH - make current window full height at far left (leftmost vertical window)
- Ctrl + wL - make current window full height at far right (rightmost vertical window)
- Ctrl + wJ - make current window full width at the very bottom (bottommost horizontal window)
- Ctrl + wK - make current window full width at the very top (topmost horizontal window)

### Indenting
- \>\> - indent (move right) line one shiftwidth
- << - de-indent (move left) line one shiftwidth
- \>% - indent a block with () or {} (cursor on brace)
- \>ib - indent inner block with ()
- \>at - indent a block with <> tags
- 3== - re-indent 3 lines
- =% - re-indent a block with () or {} (cursor on brace)
- =iB - re-indent inner block with {}
- gg=G - re-indent entire buffer
- ]p - paste and adjust indent to current line

### Tabs
- :tabnew or :tabnew {page.words.file} - open a file in a new tab
- Ctrl + wT - move the current split window into its own tab
- gt or :tabn[ext] - move to the next tab
- gT or :tabp[revious] - move to the previous tab
- #gt - move to tab number #
- :tabm[ove] # - move current tab to the #th position (indexed from 0)
- :tabc[lose] - close the current tab and all its windows
- :tabo[nly] - close all tabs except for the current one
- :tabdo command - run the command on all tabs (e.g. :tabdo q - closes all opened tabs)

### Options
- :abbreviate   - list abbreviations
- :args         - argument list
- :augroup      - augroups
- :autocmd      - list auto-commands
- :buffers      - list buffers
- :breaklist    - list current breakpoints
- :cabbrev      - list command mode abbreviations
- :changes      - changes
- :cmap         - list command mode maps
- :command      - list commands
- :compiler     - list compiler scripts
- :digraphs     - digraphs
- :file         - print filename, cursor position and status (like Ctrl-G)
- :filetype     - on/off settings for filetype detect/plugins/indent
- :function     - list user-defined functions (names and argument lists but not the full code)
- :function Foo - user-defined function Foo() (full code list)
- :highlight    - highlight groups
- :history c    - command history
- :history =    - expression history
- :history s    - search history
- :history      - your commands
- :iabbrev      - list insert mode abbreviations
- :imap         - list insert mode maps
- :intro        - the Vim splash screen, with summary version info
- :jumps        - your movements
- :language     - current language settings
- :let          - all variables
- :let FooBar   - variable FooBar
- :let g:       - global variables
- :let v:       - Vim variables
- :list         - buffer lines (many similar commands)
- :lmap         - language mappings (set by keymap or by lmap)
- :ls           - buffers
- :ls!          - buffers, including "unlisted" buffers
- :map!         - Insert and Command-line mode maps (imap, cmap)
- :map          - Normal and Visual mode maps (nmap, vmap, xmap, smap, omap)
- :map<buffer>  - buffer local Normal and Visual mode maps
- :map!<buffer> - buffer local Insert and Command-line mode maps
- :marks        - marks
- :menu         - menu items
- :messages     - message history
- :nmap         - Normal-mode mappings only
- :omap         - Operator-pending mode mappings only
- :print        - display buffer lines (useful after - :g or with a range)
- :reg          - registers
- :scriptnames  - all scripts sourced so far
- :set all      - all options, including defaults
- :setglobal    - global option values
- :setlocal     - local option values
- :set          - options with non-default value
- :set termcap  - list terminal codes and terminal keys
- :smap         - Select-mode mappings only
- :spellinfo    - spellfiles used
- :syntax       - syntax items
- :syn sync     - current syntax sync mode
- :tabs         - tab pages
- :tags         - tag stack contents
- :undolist     - leaves of the undo tree
- :verbose      - show info about where a map or autocmd or function is defined
- :version      - list version and build options
- :vmap         - Visual and Select mode mappings only
- :winpos       - Vim window position (gui)
- :xmap         - visual mode maps only

### Search
- /pattern - search for pattern
- ?pattern - search backward for pattern
- \vpattern - 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
- n - repeat search in same direction
- N - repeat search in opposite direction
- :%s/old/new/g - replace all old with new throughout file
- :%s/old/new/gc - replace all old with new throughout file with confirmations
- :noh[lsearch] - remove highlighting of search matches
- :vim[grep] /pattern/ {`{file}`} - search for pattern in multiple files
- e.g. :vim[grep] /foo/ **/*
- :cn[ext] - jump to the next match
- :cp[revious] - jump to the previous match
- :cope[n] - open a window containing the list of matches
- :ccl[ose] - close the quickfix window

### Diff
- zf - manually define a fold up to motion
- zd - delete fold under the cursor
- za or zA - toggle fold under the cursor
- zo - open fold under the cursor
- zc - close fold under the cursor
- zr - reduce (open) all folds by one level
- zm - fold more (close) all folds by one level
- zi - toggle folding functionality
- ]c - jump to start of next change
- [c - jump to start of previous change
- do or :diffg[et] - obtain (get) difference (from other buffer)
- dp or :diffpu[t] - put difference (to other buffer)
- :diffthis - make current window part of diff
- :dif[fupdate] - update differences
- :diffo[ff] - switch off diff mode for current window

### Marks and positions
- :marks - list of marks
- ma - set current position for mark A
- `a - jump to position of mark A
- y`a - yank text to position of mark A
- `0 - go to the position where Vim was previously exited
- `" - go to the position when last editing this file
- `. - go to the position of the last change in this file
- `` - go to the position before the last jump
- :ju[mps] - list of jumps
- Ctrl + i - go to newer position in jump list
- Ctrl + o - go to older position in jump list
- :changes - list of changes
- g, - go to newer position in change list
- g; - go to older position in change list
- Ctrl + ] - jump to the tag under cursor

### Global
- :h[elp] keyword - open help for keyword
- :sav[eas] file - save file as
- :clo[se] - close current pane
- :ter[minal] - open a terminal window
- K - open man page for word under the cursor

### Non-Vim commands
Multiline Editing
- On Windows, you hold Ctrl+Alt while pressing the up ↑ or down ↓ arrow keys to add cursors.
- Mac: ⌥ Opt+⌘ Cmd+↑/↓
- Linux: Shift+Alt+↑/↓