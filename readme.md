download the vim config that has
```
au User lsp_setup call lsp#register_server({
  \ 'name': 'clangd',
  \ 'cmd': {info->['clangd', '--experimental-modules-support', '--background-index']},
  \ 'allowlist': ['c', 'cpp'],
  \ })
autocmd FileType c,cpp setlocal omnifunc=lsp#complete
```

then run these 2 commands

cmake -G Ninja -B build -DCMAKE_CXX_COMPILER=clang++

cmake --build build
