# TeX template
## required
- The MacTeX-2016 Distribution
- Skim
- Neovim
- dein.vim
- vimproc.vim
- vim-quickrun
- vimtex
- deoplete.nvim

## settings
### ~/.latexmkrc
```perl
#!/usr/bin/perl

$latex = 'uplatex -kanji=utf8 -synctex=1 -halt-on-error -interaction=nonstopmode %O %S';
$latex_silent = 'uplatex -synctex=1 -halt-on-error -interaction=batchmode';
$bibtex = 'pbibtex %O %B';
$dvipdf = 'dvipdfmx %O -o %D %S';
$makeindex = 'mendex %O -o %D %S';
$max_repeat = 5;
$pdf_mode = 3;
$pvc_view_file_via_temporary = 0;
$pdf_previewer = "open -ga /Applications/Skim.app";
```

### ~/.config/nvim/dein.toml
```toml
# quickrun {{{
[[plugins]]
repo = 'thinca/vim-quickrun'
hook_add = '''
let g:quickrun_config = {
  \ "_" : {
    \ 'runner' : 'vimproc',
    \ 'runner/vimproc/updatetime' : 60,
    \ 'outputter' : 'error',
    \ 'outputter/error/success' : 'buffer',
    \ 'outputter/error/error' : 'quickfix',
    \ 'outputter/buffer/split' : ':rightbelow 8sp',
    \ 'outputter/buffer/close_on_empty' : 1,
    \ 'hook/time/enable' : 1,
  \ },
  \ 'tex' : {
  \ 'command' : 'latexmk',
  \ 'exec' : ['%c -gg -pdfdvi %s', 'open %s:r.pdf'],
  \ },
\}
'''
# }}}
```

### ~/.config/nvim/dein_lazy.toml
```toml
[[plugins]]
repo = 'lervag/vimtex'
on_ft = 'tex'
hook_source = '''
let g:vimtex_fold_envs = 0
let g:vimtex_view_general_viewer = '/Applications/Skim.app/Contents/SharedSupport/displayline'
let g:tex_conceal=''
'''
```
