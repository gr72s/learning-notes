# install ocaml

- download script: `wget https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh`
- install script: `sh install.sh`
- install ocaml
  - env setup:
    - `opam init`
    - `source ~/.profile`
  - install devtools: `opam install dune utop ocaml-lsp-server`

# utop

> 通过《real world ocaml 第二版》学习的 ocaml, 书中使用的标准库是 Base(Core 的子集), 所以在使用 utop 之前需要一些额外的设置

- install base: `opam install core core_bench`
- setup utop
  - create and edit ocamlinit: `touch ~/.ocamlinit`
    ```
    #require "core.top";;
    #require "ppx_jane";;
    open Base;;
    ```

# ide

## vs code

- install plugin
  - ocaml platform
  - ocaml formatter
