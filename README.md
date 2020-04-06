# vim-fuzzy-line-searcher
Proof of concept based on https://gist.github.com/danmikita/d855174385b3059cd6bc399ad799555e

## What does it do?

- Calling Fzf_lines() (default <leader>f) opens a search for all lines in all files recursively in the current directory
- Type to fuzzy match a line
- The fuzzy search does not match the filename, only the line contents
- Select a line and the file will be opened for editting on that line

Two different display scripts are provided
- `fuzzy-line-viewer.sh` displays the selected line and the next 19 lines of the file
- `fuzzy-line-viewer-2.sh` displays a section of the selected file, with the selected line being the only coloured one

The first display script is less resource intensive compared to the second one.

## How to install

1. Add or source the `init.vim` script in the `.vimrc`
2. Set the nnoremap to whatever you like
3. Set the path to the selected display script in the `l:fzf_files_options` variable

## Other info/limitations

- Tested on Arch linux and MacOS Mojave
- Explicit shebang in the display scripts to execute through bash, they dont seem to work in zsh
- The `fuzzy-line-viewer-2.sh` seems very inefficient with three seperate calls to bat, tail, and head
- The display scripts remove whitespace from the filename to view them in bat, but this may be an issue if a filename has whitespace in it
