# Vim Cheatsheet
Of course, the best way is to use it.

### Cursor 
(in order of most helpful to least helpful)
** Moving **
- h - left ⬅
- j - down ⬇
- k - up ⬆
- l - right ➡

** Jumping in a line **
w - jump forwards to the start of a word
W - jump forwards to the start of a word (words can contain punctuation)
e - jump forwards to the end of a word
E - jump forwards to the end of a word (words can contain punctuation)
b - jump backwards to the start of a word
B - jump backwards to the start of a word (words can contain punctuation)
ge - jump backwards to the end of a word
gE - jump backwards to the end of a word (words can contain punctuation)

0 - jump to the start of the line
^ - jump to the first non-blank character of the line
$ - jump to the end of the line
g_ - jump to the last non-blank character of the line
% - move to matching character (default supported pairs: '()', '{}', '[]' - use :h matchpairs in vim for more info)

** Jumping around a document **
- gg - go to the first line of the document 🔝
- G - go to the last line of the document 🎬

- } - jump to next paragraph (or function/block, when editing code) ﹛ ⬅
- { - jump to previous paragraph (or function/block, when editing code) ➡️ ｝

gj - move cursor down (multi-line text)
gk - move cursor up (multi-line text)

H - move to top of screen
M - move to middle of screen
L - move to bottom of screen
zz - center cursor on screen

5gg or 5G - go to line 5
gd - move to local declaration
gD - move to global declaration
fx - jump to next occurrence of character x
tx - jump to before next occurrence of character x
Fx - jump to the previous occurrence of character x
Tx - jump to after previous occurrence of character x
; - repeat previous f, t, F or T movement
, - repeat previous f, t, F or T movement, backwards

** shifting screen **
Ctrl + e - move screen down one line (without moving cursor)
Ctrl + y - move screen up one line (without moving cursor)
Ctrl + b - move back one full screen
Ctrl + f - move forward one full screen
Ctrl + d - move forward 1/2 a screen
Ctrl + u - move back 1/2 a screen



### Options
:abbreviate   - list abbreviations
:args         - argument list
:augroup      - augroups
:autocmd      - list auto-commands
:buffers      - list buffers
:breaklist    - list current breakpoints
:cabbrev      - list command mode abbreviations
:changes      - changes
:cmap         - list command mode maps
:command      - list commands
:compiler     - list compiler scripts
:digraphs     - digraphs
:file         - print filename, cursor position and status (like Ctrl-G)
:filetype     - on/off settings for filetype detect/plugins/indent
:function     - list user-defined functions (names and argument lists but not the full code)
:function Foo - user-defined function Foo() (full code list)
:highlight    - highlight groups
:history c    - command history
:history =    - expression history
:history s    - search history
:history      - your commands
:iabbrev      - list insert mode abbreviations
:imap         - list insert mode maps
:intro        - the Vim splash screen, with summary version info
:jumps        - your movements
:language     - current language settings
:let          - all variables
:let FooBar   - variable FooBar
:let g:       - global variables
:let v:       - Vim variables
:list         - buffer lines (many similar commands)
:lmap         - language mappings (set by keymap or by lmap)
:ls           - buffers
:ls!          - buffers, including "unlisted" buffers
:map!         - Insert and Command-line mode maps (imap, cmap)
:map          - Normal and Visual mode maps (nmap, vmap, xmap, smap, omap)
:map<buffer>  - buffer local Normal and Visual mode maps
:map!<buffer> - buffer local Insert and Command-line mode maps
:marks        - marks
:menu         - menu items
:messages     - message history
:nmap         - Normal-mode mappings only
:omap         - Operator-pending mode mappings only
:print        - display buffer lines (useful after :g or with a range)
:reg          - registers
:scriptnames  - all scripts sourced so far
:set all      - all options, including defaults
:setglobal    - global option values
:setlocal     - local option values
:set          - options with non-default value
:set termcap  - list terminal codes and terminal keys
:smap         - Select-mode mappings only
:spellinfo    - spellfiles used
:syntax       - syntax items
:syn sync     - current syntax sync mode
:tabs         - tab pages
:tags         - tag stack contents
:undolist     - leaves of the undo tree
:verbose      - show info about where a map or autocmd or function is defined
:version      - list version and build options
:vmap         - Visual and Select mode mappings only
:winpos       - Vim window position (gui)
:xmap         - visual mode maps only
