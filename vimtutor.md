# Info
* running `vimtutor` in the terminal that has some UNIX kernel will open up a tutorial on how to use the VI/VIM text editor
* It's basically a text editor but on the terminal. Believe me that it's way way faster than just manually going through File Explorer or Finder
# Syntax
```bash
vimtutor
```
* There is a version on NeoVIM that will NOT be covered in CS 3377 Systems Programming in UNIX systems that can be accessed (assuming you have neoVIM)
```bash
nvim +Tutor
```
* Remember that if VIM somehow doesn't work, VI might work because VIM is an improved version of VI.
* The pipe operator, `|`, can work with VIM as well, opening, for example, file trees (assuming you have a recent Ubuntu installation, it should exist by default).
  * The UTD cs1 server does have access to the `tree` command
  * To look inside of a directory with `tree`, you need ONLY `r` or `4` permissions because you are displaying information about a directory. If you don't have permissions, it will give you an error message after the last field.
```bash
tree | vim -
```

* within `tree`, lowercase `n` will shift you forward
* within `tree`, uppercase `N` will shift you backward

`/` means search in vim text editor, so it works like CTRL + F
