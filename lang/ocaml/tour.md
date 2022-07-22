- [逗号和分号](#逗号和分号)
- [变量、函数](#变量函数)
  - [变量](#变量)
  - [函数](#函数)
- [泛型](#泛型)
- [数据结构](#数据结构)
- [array](#array)
- [module](#module)
  - [模块声明](#模块声明)
  - [使用模块](#使用模块)
  - [ml/mli](#mlmli)
  - [open/include](#openinclude)
- [record、mutable 和 ref](#recordmutable-和-ref)
- [error/exception](#errorexception)
  - [error](#error)
  - [exception](#exception)
- [compile](#compile)

  - [dune](#dune)
  - [ocamlfind](#ocamlfind)
  - [ocamlopt/ocamlc](#ocamloptocamlc)

- [ ] 尾递归
- [ ] List 模块

# 逗号和分号

- 使用逗号分隔变量会被解释为元组
- 数组中使用分号分隔数据

# 变量、函数

- 类型自动推导, 可显式声明类型
  ```ocaml
  let var1 = 1
  let var2:float = 1.
  ```
- 使用 let 关键字定义变量或函数
- 变量名必须小写字母、下划线或者`'`开头, 类型必须大写字母开头

## 变量

- `float`的变量和运算符需要额外加个`.`
  ```ocaml
  let var1 = 1. +. 2.
  ```

## 函数

- 定义函数
  - 显式定义参数列表: `let fun-name param-list = ...`
  - 隐式定义参数列表: `let fun-name = function ...`
  - 匿名函数: `(fun param-list -> fun-body.. )`
- 函数签名
  - 参数列表使用 -> 连接, 最后一个参数是函数的返回值, `=<fun>`标识这是一个函数
    ```ocaml
    let square x = x * x;;
    val square : int -> int = <fun>
    ```
- 偏函数

  - 使用`let`绑定一个未完全传参的函数
    ```ocaml
    let colon_concat = concat ~sep:":"
    ```
  - 使用偏函数时, 如果可选参数定义在普通参数前的话, 可选参数会被擦除; 如果把可选参数定义在最后, 编译器会警告可选参数不会被擦除

- 标签参数

  - 声明: `val split : string -> on:char -> string list`
  - 使用

    ```ocaml
    String.split ~on:';' "a:b"

    let on = ':'
    String.split ~on "a:b"
    ```

    - 传参: `~标签名:参数名`
    - 变量名和标签名重复时可以省略标签名后的参数名

- 可选参数与默认参数

  - 声明: `?`加标签名是可选参数, `=""`是默认参数, `val concat : ?(sep:string="") -> string list -> string`
  - 使用
    - 不使用可选参数的话, 传参时忽略即可
    - 使用可选参数的方法与标签参数一致, `String.concat ~sep:":" ...`
    - 想要给可选参数传递 Some 时, 语法稍有不同. `String.concat ?sep:(Some ":")`. 当不传入 Some 时, 可选参数默认为 None, 等价为`?sep:None`

- 操作符重定义

  ```ocaml
  let (+) x y = ...

  2 + 1;;
  ```

- 操作符自定义
  - 自定义的操作符必须以以下字符开头: `% & * + - . / : < = > ? @ ^ |`, 不能以`~ ! $`开头(本书第一版未提到这个)
  - 自定义操作符的优先级、结合性由开头的字符决定

# 泛型

- 和 java 中的泛型作用类似, 使用以`'`开头的小写字母声明
  ```ocaml
  let sum_if_true (test:'a->bool) (x:'a) (y:'a) = if test x then x else y
  (* abbr *)
  let sum_if_true test x y = if test x then x else y
  ```

# 数据结构

- tuple: 数据类型可以不同, 初始化后数量固定的集合. 支持解包操作
  ```ocaml
  let (x,y) = 1,"a"
  ```
- list: 数据类型相同的数量可以的集合

- [ ] option
- [ ] some
- [ ] control: for while ..

# array

- 使用`.(index)`索引数据, 使用`<-`赋值

# module

- main(): ocaml 中没有明确的 main 方法, 一般用`let ()`代替, 它表示捕获了一个没有返回值的函数
- 同其它语言一样, 模块及模块中的定义有作用域的概念

## 模块声明

- 语法
  ```ocaml
  (* 同时声明sig和struct的写法 *)
  module <name>: sig <signature> end = struct <implementation> end
  (* 分开声明的写法 *)
  (* sig *)
  module type <type-name> = sig <signature> end
  (* struct *)
  module <struct-name> = struct <implementation> end
  ```
  - name: 模块名称
  - signature: 签名. 有点像 c 里的.h 文件, 可以是纯声明, 也可以有实现
  - implementation: 对 signature 的实现

## 使用模块

- 文件顶部导入: `open Base`
- `let`绑定导入: `let open Base in`
  - 局部导入: `let module b = Base in`
- 直接引用: `Int64.((x + y) / if_int 2)`

## ml/mli

- ml 像是 c 里的源文件(.c), mli 像是 c 里的头文件(.h)
- Counter 例子中使用 ml/mli 组织模块的时候, 提到了封装模块内部的实现, 我理解的这种操作是:
  - 使用自定义的类型替代基础类型或者三方库中的类型, 比如`type t = string`
  - 有点像 c 中会使用 typedef 或者宏创建自己的业务类型

## open/include

- open 用于打开模块
- include 有点像是继承, 比如它可以扩展一个现有的模块

  ```ocaml
  (* ml *)
  let apply = function...
  include Option

  (* mli *)
  include module type of Option
  val apply: ...
  ```

  - ml 文件中定义了扩展的方法, 最后使用`include Option表示包含了Option模块的所有方法`
  - mli 文件中将 Option 类型作为此模块的类型
  - 学习<<realworldocaml>>中扩展 Option 的例子时, 使用自定义文件导入扩展的 ml 模块时, vscode 报错找不到模块的 cmi 文件. 查[资料](https://www2.ocaml.org/learn/tutorials/filenames.html)发现 cmi 是 mli 的中间文件, 需要用 ocamlc 编译

# record、mutable 和 ref

- record 与 rust 中的 struct 比较类似, 区别是 ocaml 是使用 type 关键字声明的
- record 中的字段默认不可变, 声明时添加 mutable 才能修改
- 通过 let 声明的变量是无法修改的, 通过 ref 声明的变量可以修改值
  ```ocaml
  let var1 = ref 0
  var1 := 1
  ```
- 通过 ref 了解到 ocaml 可以重载运算符

# error/exception

## error

## exception

# compile

## dune

- 使用 dune 组织、编译工程
- 每个工程使用有一个 dune-project, 可以有多个 dune 用于区分子目录
- 引入三方包: 在 dune 的 libraries 中声明
  ```
  // import base and stdio
  (executable
   (name main)
   (libraries base stdio))
  ```
- 编译&执行: dune build main

## ocamlfind

- 是一个调用其它 ocaml 工具链的工具: `ocamlfine ocamlopt -linkpkg -package base main.ml`

## ocamlopt/ocamlc

- ocamlopt: 本机代码编译器
- ocamlc: 字节码编译器
