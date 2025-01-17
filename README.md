# Vim Notes from the Primeagen
[The Primeagen](https://www.youtube.com/playlist?list=PLm323Lc7iSW9kRCuzB3J_h7vPjIDedplM)

Notes written in (neo)vim
 
## Vim Movements P1 - Your First Moves 
https://www.youtube.com/watch?v=nnhqVDIx-go

Don't use your arrow keys!

`j`, `k`,`h`, `l`: down, up, left, right  

`w`, `b`: jump forward by word, jump backwards by word  

`f`, `t`: jump to a letter, jump one before a letter  

`%`: Go to respective parenthesis, brace, etc.  

`Ctrl-d`, `Ctrl-u`: jump down half page, jump up half page  

`{`, `}`: jump up a block, jump down by a block  

`V`: highlight line and enter visual mode  

`P`, `p`: paste up a line, paste down a line  

`U`: Capitalize stuff that's highlighted  

`Ctrl-a`, `ctrl-x`: Increment var, decrement var  

`o`, `O`: Insert newline below current, insert newline above current line (both enter insert mode)  

`I`, `A`: Enter insert mode at first character on a line, enter insert mode at last character in the current line  

Add some nice remap to make things easier:
* `F5`: Show undo tree

* `<leader>ps`: (Project Search) searches for stuff using ripgrep (Make sure to install ripgrep on your system)

* `<leader>gd`: Go to definition
* `<leader>gr`: Go to references  

## VIM Movements P2: 5 moves to make you better ked
https://www.youtube.com/watch?v=QN4fuSsWTbA

* Use Ctrl-c or Ctrl-open bracket instead of Esc.  
  Instead of using the CAPS LOCK key for Esc, you can use it for CTRL.

* When using f and t, you can use `,` to go backwards and `;` to go forwards to search for the same letter without repeating the same command
* Use `c` instead of `d` to enter insert mode
* You can use `i` and `a` in conjunction with c or d to remove whatever's inside {}, [], "", '', etc.
  E.g. ci" will delete everything within the following string: "Hello, world".
  ca" will delete everything inside the string as well as the "". 
* Marks allow jumping to points in a file: `mJ` will create a mark called J. `'J` will jump to the mark. Note: Capital letter are marks that are unique across multiple files while lowercase letters are for local file marks.
* Bonus remap allows you to move highlighted regions up or down:
``` {.vimscript}
vnoremap J :m '>+1<CR>gv=gv
vnoremap K :m '<-2<CR>gv=gv
```


## Using Vim: Vim + Git - Fugitive (Haven't tried it yet looks interesting)
https://www.youtube.com/watch?v=PO6DxfGPQvw

`<leader>gs`: Git Status  

Use `s` to stage and `u` to unstage.  

`:Gcommit`: Commits stuff  

`:Gpush`: Pushes stuff  

`:Git merge <branchname>`: Merge  

Use `dv` on the file you want to resolve if you have merge conflicts.  
The window on the left should be the current branch, the window on the right should be the one you just merged from, and the middle window is the resulting merge.    

`<leader>gf`: Grab from the window on the left (Use 'gu' if using dvorak)  

`<leader>gj`: Grab from the window on the right (Use 'gh' if using dvorak)  

`Ctrl-w` and `ctrl-O`: save and close  

## Vimium: Intro to using keyboard in your browser
https://www.youtube.com/watch?v=cA2aUFsSLac

`j` and `k`: down and up  

`d`, `u`: half-page down, half-page up (you don't need ctrl)  

`f`: open link in current tab  

`H`: go back  

`V`: Visual mode highlight entire line  

`y`: yank  

## Using Vim: My Vim Workflow - Solving a bug
https://www.youtube.com/watch?v=-I1b8BINyEw

### First you want some plugins

* Gruvbox: "The greatest colorscheme ever bestowed to mankind"
* COC: For autocomplete
* Fzf: File finding

gzf remap to make searching for files easier:
```
nnoremap <C-p> :Files<CR> 
```

### Commands Used 

`Ctrl-p`: Remap for :Files. Use it to search for a file. Works even for searching large codebases.  

`gd`(normal mode): Jump to definition  

`Ctrl-^`: Jumps to the last file you were in

`Ctrl-o`: Go back to last position

`Ctrl-i`: Go forward position (Opposite of Ctrl-o)

## VIM: Coolest Vim Command (Gotta look into that as well)
https://www.youtube.com/watch?v=E7NBhSsZouc

Let's say you have a line of code:
```javascript
const res = await fetch("http://localhost:8002", {
```
If you wanted to change the `http://localhost:8002` string inside the quotes,
you don't have to use `f"` to go to the quotes, you can just use `ci"`. Vim automatically jumps to the nearest quote.

## Vim "g" Command
https://www.youtube.com/watch?v=CN8p9iL7PPI

`g Ctrl-g`: Shows you what line, column, word, and byte you're at and how far you're down the file

`g8`: Get ASCII Code of current character

`g<`: Get the output from the last command you executed

`g&`: Replay your last s command (substitution)

`gJ`: Combines the line below with the current line while keeping the spacing the same

`gU motion`: Uppercase stuff

`gu motion`: Lowercase stuff

`gd`: Jump to definition in the file (or function?)

`gf`: Jumps to a file

`gF`: Jump to a line in a file

`gq`: Automatically align text to 80 characters

`gQ`: Enter Ex mode

`8g_`: Jumps down *7* lines and puts you at the end of that line

`g\$`: In wrap mode go to the end of the "line"

`g??`: Rot13 on a line

`gg`: To Top

`G`: Bottom

`gv`: Rehighlight what you previously highlighted

`gi`: Go back to your previous insert spot

`'<,'>g/Styled/d`: Delete all lines with "Styled"

`'<,'>g/Styled/norm! diw`: Execute diw on every line with "Styled"

`:help g`: A bunch more g commands

`help :g`: All the fun searching g commands


## Spell checking in vim
`:set spell!`: highlights all the poorly spelled word in the current buffer
`]s`: to move to the next spelling mistake
`z=`: gives spelling suggestions for the current word under the cursor
