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
- 函数签名
  - 参数列表使用 -> 连接, 最后一个参数是函数的返回值, `=<fun>`标识这是一个函数
    ```ocaml
    let square x = x * x;;
    val square : int -> int = <fun>
    ```

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

# record、mutable 和 ref

- record 与 rust 中的 struct 比较类似, 区别是 ocaml 是使用 type 关键字声明的
- record 中的字段默认不可变, 声明时添加 mutable 才能修改
- 通过 let 声明的变量是无法修改的, 通过 ref 声明的变量可以修改值
  ```ocaml
  let var1 = ref 0
  var1 := 1
  ```
- 通过 ref 了解到 ocaml 可以重载运算符

# compile

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
