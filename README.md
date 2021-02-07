## Barow

![barow](./img/barow.png)

A minimalist statusline for [n](https://neovim.io/)/[vim](https://www.vim.org/).

### install
If you use a plugin manager, follow the traditional way.

For example with [vim-plug](https://github.com/junegunn/vim-plug) add this in `.vimrc`/`init.vim`:
```
Plug 'doums/barow'
```

Then run in vim:
```
:source $MYVIMRC
:PlugInstall
```
If you use vim's native package `:h packages`.

### usage
Barow works out of the box.\
But if you want, here are all the options you can customize
```
" in .vimrc/init.vim

let g:barow = {
      \'modes': {
      \  'normal': [ ' ', 'BarowNormal' ],
      \  'insert': [ 'i', 'BarowInsert' ],
      \  'replace': [ 'r', 'BarowReplace' ],
      \  'visual': [ 'v', 'BarowVisual' ],
      \  'v-line': [ 'l', 'BarowVisual' ],
      \  'v-block': [ 'b', 'BarowVisual' ],
      \  'select': [ 's', 'BarowVisual' ],
      \  'command': [ 'c', 'BarowCommand' ],
      \  'shell-ex': [ '!', 'BarowCommand' ],
      \  'terminal': [ 't', 'BarowTerminal' ],
      \  'prompt': [ 'p', 'BarowNormal' ],
      \  'inactive': [ ' ', 'BarowModeNC' ]
      \},
      \'buf_name': {
      \  'empty': '',
      \  'highlight': [ 'BarowBufName', 'BarowBufNameNC' ]
      \},
      \'read_only': {
      \  'value': 'ro',
      \  'highlight': [ 'BarowRO', 'BarowRONC' ]
      \},
      \'buf_changed': {
      \  'value': '*',
      \  'highlight': [ 'BarowChange', 'BarowChangeNC' ]
      \},
      \'tab_changed': {
      \  'value': '*',
      \  'highlight': [ 'BarowTChange', 'BarowTChangeNC' ]
      \},
      \'line_percent': {
      \  'highlight': [ 'BarowLPercent', 'BarowLPercentNC' ]
      \},
      \'row_col': {
      \  'highlight': [ 'BarowRowCol', 'BarowRowColNC' ]
      \},
      \'modules': []
      \}
```
NOTE: For `modes`, the text value is intentionally set to one character max.

NOTE: The strings `Barow*` are highlight groups. You can use `barow#hi` function to create your own groups.

### modules
You can add additional modules to your bar in a simple way.\
Available modules:
- [barowLSP](https://github.com/doums/barowLSP), display LSP diagnostics count and status
- [barowGit](https://github.com/doums/barowGit), display git current branch

```
" .vimrc/init.vim
" ...

Plug 'doums/barow'
Plug 'doums/barowGit'
Plug 'doums/barowLSP'
" ...

let g:barow = {
" ...
      \  'modules': [
      \    [ 'barowGit#branch', 'BarowHint' ],
      \    [ 'barowLSP#error', 'BarowError' ],
      \    [ 'barowLSP#warning', 'BarowWarning' ],
      \    [ 'barowLSP#info', 'BarowInfo' ],
      \    [ 'barowLSP#hint', 'BarowHint' ],
      \    [ 'barowLSP#coc_status', 'StatusLine' ],
      \    [ 'barowLSP#ale_status', 'StatusLine' ]
      \  ]
      \}
```

NOTE: Module outputs will only appear in the statusbar of the current window.

You can define your own module. To update the statusline call `barow#update` function.

### `barow#hi`

You can use `barow#hi` function to create your own highlight groups.
```
" arguments:   group_name,     fg_color,       bg_color,       style
call barow#hi('MyCustomGroup', ['#ffffff', 7], ['#000000', 0], 'bold')
```
For more details see `:h highlight-args`.

### `barow#update`

To update the statusline call `barow#update` function. Useful if you write a module.
```
call barow#update()
```

### color support
- Truecolor
- 256 color

### license
Mozilla Public License 2.0
