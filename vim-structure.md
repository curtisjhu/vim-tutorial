# Structure of vim

.vimrc
- Configurations, settings lauched when the vim text editor is lauched.
```
set nocompatible
filetype on
filetype plugin on
filetype indent on
syntax on
```

.vim
- A hidden directory where some vim files are stored. Pluggin files, themes, snippets, etc.
```
~/.vim $ ls
autoload  themes  plugged
```

.viminfo 
- The command line history.
- The search string history.
- The input-line history.
- Contents of non-empty registers.
- Marks for several files.
- File marks, pointing to locations in files.
- Last search/substitute pattern (for 'n' and '&').
- The buffer list.
- Global variables.

```
|2,0,1656188710,,"NERDTree"
:Ntree
|2,0,1656188675,,"Ntree"
::q
|2,0,1656188462,,":q"
:h
|2,0,1656188101,,"h"
:scriptnames
|2,0,1656186422,,"scriptnames"
:scriptnaems
|2,0,1656186419,,"scriptnaems"
:tree
```
