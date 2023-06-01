# 2022-23学年第2学期

##  实 验 报 告

![](zucc.png)

-   课程名称: <u>编程语言原理与编译</u>

-   实验项目: <u>函数式语言，类型检查</u>

-   专业班级: <u>计算机2004</u>

-   学生学号: <u>32004151</u>

-   学生姓名: <u>徐韩</u>

-   实验指导教师:<u>郭鸣</u>



## 实验内容

1. 阅读 课件 [一阶函数语言，类型检查][ch04]，理解如下概念
    - 动态类型与静态类型的区别

      动态类型语言，在程序运行时检查类型

      静态类型语言，在编译时检查类型

    - 静态作用域/动态作用域的区别

      动态作用域，变量按代码`执行时`的流程上下文绑定值

      静态作用域，变量按代码`声明时`的`词法上下文`绑定值

    - 一阶函数式语言 与 高阶函数式语言的区别

      一阶函数式语言只支持函数作为值的使用，而高阶函数式语言除了支持函数作为值的使用外，还支持函数作为参数传递和返回值。

    - 类型检查的方法

      类型检查函数`typ` 需要参数`类型环境env` Using a type environment `[(“x”, TypI)]

    - （自选）阅读虎书课本第5章、15 章、16 章

1. 阅读 `3.monotype.p18-43.pdf` `type-rule-tutorial.pdf`
    - 理解各个语言语法构造类型检查的过程.
      1. 语法分析：在编程语言中，首先需要对源代码进行语法分析。
      2. 符号表构建：符号表是编程语言在编译或解释过程中用于存储变量、函数和其他符号信息的数据结构。
      3. 类型推断：类型推断是一种自动推断变量类型的过程，它可以在不显式指定类型的情况下确定表达式和变量的类型。
      4. 类型检查：类型检查是在编译或解释过程中验证代码中的类型是否符合语言的类型规则的过程。
      5. 错误处理：在类型检查过程中，如果发现类型错误，编译器或解释器通常会生成相应的错误消息，并停止继续编译或解释过程。
    - 掌握单态类型推理规则（自选）

1. 阅读`MicroML`[源代码](https://gitee.com/sigcc/plzoofs/blob/master/Fun/ReadME.md)

      - 函数定义/函数调用的实现

          ```F#
          // 函数定义
          let add x y =
              x + y
          
          // 函数调用
          let result = add 2 3
          ```

      - 阅读 结合教材第5章、课件里面的 环境与闭包 理解闭包概念
          - 结合代码，理解如何在环境中表示闭包
          
            闭包是指在一个函数内部定义的函数，它可以访问和修改其外部函数作用域中的变量。
          
            ```f#
            // 外部函数
            let createMultiplier factor =
                // 内部函数（闭包）
                let multiplyByFactor x =
                    x * factor
                multiplyByFactor
            
            // 创建闭包
            let multiplyByTwo = createMultiplier 2
            let multiplyByThree = createMultiplier 3
            
            // 使用闭包
            let result1 = multiplyByTwo 5
            let result2 = multiplyByThree 4
            
            // 打印结果
            printfn "结果1：%d" result1
            printfn "结果2：%d" result2
            ```
          
            
          
      - 静态作用域,动态作用域的实现
        - 类型检查的实现
        
          **静态类型检查**：静态类型检查是在编译时进行的类型检查。
        
          **动态类型检查**：动态类型检查是在程序运行时进行的类型检查。
        
          **类型推断**：类型推断是一种自动推导变量和表达式的类型的技术。
        
      - 高阶函数的实现方法（自选）
          -  [05 highOrder.typeInfer][ch05]
        - 多态函数的类型归并unify 的实现（自选）

1. 理解程序设计语言的类型系统

    - 查看并运行`ExprType.fs` 
      - 查看 `a b c e1 e2 e3 eval` 的类型并加以说明
      
        a list = []
      
        b a [] = [||]
      
        c int list = [1; 2]
      
        e1 expr 
      
        e2 expr 
      
        e3 expr 
      
        eval e:expr -> int
      
    - 请定义一个积类型 `string * string * int`，表达学生信息(姓名，学号，成绩) 请构造几个合法的值

      ```F#
      type Student = string * string * int
      
      let student1 : Student = ("Alice", "2021001", 85)
      let student2 : Student = ("Bob", "2021002", 92)
      let student3 : Student = ("Carol", "2021003", 78)
      ```

    - 请定义一个函数，使得函数类型为： `'a ->'a->'a`

      ```F#
      let myFunction (x: 'a) (y: 'a) : 'a =
          x
      ```

      ```F#
      let result1 = myFunction 10 20  // 返回值为 10，类型为 int
      let result2 = myFunction "Hello" "World"  // 返回值为 "Hello"，类型为 string
      let result3 = myFunction true false  // 返回值为 true，类型为 bool
      ```

    - 查看并运行`ExprEnv.fs` 理解什么是求值环境 `env`

      env` 包含了变量 `"a"`、`"c"`、`"baf"` 和 `"b"`，以及它们对应的值。

1. （自选）阅读 readings 下 `1.typecheck.ustc.pdf` 

    - 运行文件中 p39-45 例子程序,说明结果

    - 在`gcc` 里面 编译 p58 的程序,根据运行结果回答问题

    - 写出下面 p56 对应的 `fsharp` 代码 ,构造该类型的值,查看其类型.

    ```c
    
    typedef struct cell {
        int info;
        struct cell  next;
    } cell;
    
    ```

    - 学习p60多态函数部分 请给出一个多态的`Tree` 的定义,写出计算`Tree` 深度的多态函数 `depth  : 'a Tree -> int`

    - 理解`类型协变`与`类型逆变`

1. (自选)阅读`4.unification.pdf`

    - 理解 多态类型推理的类型
    - 掌握归并unify算法

1. 设计你大作业的类型系统,在大作业最终报告里面说明

    - 提供哪些基本类型 int/double/char/string/bool
    - 提供哪些类型复合机制  pair list array tuple record...
    - 完成哪些类型检查/类型推理机制
      - 类型一致性检查：检查表达式、函数调用等处的类型是否匹配，例如确保加法运算符只用于数值类型。
      - 类型推理：根据上下文推断表达式的类型，例如推断变量的类型或函数的返回类型。
    - 强类型还是弱类型/静态类型还是动态类型 等.

1. 修改`MicroML` 的函数定义,支持多参数的函数

    ```F#
    (* 定义类型 *)
    type expr =
      | Fun of string list * expr  (* 多参数函数定义 *)
      
    let rec parseFuncDef tokens =
      match tokens with
      | Token.Let :: Token.Ident(funcName) :: args ->  (* 多参数函数定义规则 *)
          let argsList = parseArgs args
          let expr = parseExpr bodyTokens
          Fun(argsList, expr)
      | _ -> failwith "Invalid function definition"
    ```

    

#### Exercise 4.3

For simplicity, the current implementation of the functional language
requires all functions to take **exactly one** argument. This seriously limits the programs that can be written in the language (at least it limits what that can be written
without excessive cleverness and complications).

Modify the language to allow functions to **take one or more** arguments. Start by
modifying the abstract syntax in` Absyn.fs` to permit a list of parameter names in
`Letfun` and a list of argument expressions in `Call`.
Then modify the eval interpreter in file `Fun.fs` to work for the new abstract
syntax. You must modify the closure representation to accommodate a list of parameters. Also, modify the Letfun and `Call` clauses of the interpreter. You will
need a way to zip together a list of variable names and a list of variable values, to
get an environment in the form of an association list; so function `List.zip` might
be useful.

```F#
//Absyn.fs
module Absyn 

type expr = 
  | CstI of int   // 整数
  | CstB of bool  // 布尔数
  | Var of string   // 变量访问
  | Let of string * expr * expr // 局部变量声明，定义
  | Prim of string * expr * expr  // 基本操作 算术 * + - 、关系 < = 
  | If of expr * expr * expr    // if 表达式
  | Letfun of string * string * expr * expr    (* (f, x, fBody, letBody) *)  // 函数声明，定义
  | Letfun of (string list) * expr
  | Call of expr * expr   // 函数调用
```

```F#
//Fun.fs
module Fun

open Absyn
···
type value =
    | Int of int
    | Closure of string * string * expr * value env (* (f, x, fBody, fDeclEnv) *)
```



#### Exercise 4.4

In continuation of Exercise 4.3, modify the parser specification to
accept a language where functions may take any (non-zero) number of arguments.
The resulting parser should permit function declarations such as these:

```fsharp
let pow x n = if n=0 then 1 else x * pow x (n-1) in pow 3 8 end
let max2 a b = if a<b then b else a
in let max3 a b c = max2 a (max2 b c)
in max3 25 6 62 end
end
```

```F#
// Parser.fsy

%{
open Lexing
open Parser

// 定义抽象语法树的类型
type expr =
    | ...
    | Fun of string list * expr
%}

// Tokens
%token <string> IDENT
%token LET IN END

// 起始符号
%start <expr> program

// 优先级和结合性
%left OR
%left AND
%left EQUAL LESS GREATER PLUS MINUS TIMES DIVIDE
%right POW
%nonassoc IF THEN ELSE
%nonassoc FUN
%nonassoc COLON

// 语法规则
program:
    | expr EOF { $1 }

expr:
    | ...
    | LET letBindings IN expr END { Let($2, $4) }
    | FUN LPAREN IDENT COLON IDENT (COMMA IDENT COLON IDENT)* RPAREN expr { Fun(List.map fst $4, $8) }

letBindings:
    | letBinding { [$1] }
    | letBinding SEMICOLON letBindings { $1 :: $3 }

letBinding:
    | IDENT funDecl { ($1, $2) }

funDecl:
    | LPAREN IDENT (COMMA IDENT)* RPAREN EQ expr { Fun(List.map fst $2, $6) }

```



### 附加题 (完成数量不限,需要单独提交)

#### Exercise 4.6

Extend the abstract syntax, the concrete syntax, and the interpreter for
the untyped functional language to handle tuple constructors `(...)` and component
selectors `#i` (where the first component is` #1`):

```fsharp

type expr =
| ...
| Tup of expr list
| Sel of int * expr
| ...

```

If we use the concrete syntax `#2(e)` for `Sel(2, e)` and the concrete syntax
`(e1, e2)` for `Tup[e1; e2]` then you should be able to write programs such as
these:

```fsharp

let t = (1+2, false, 5>8)
in if #3(t) then #1(t) else 14 end
and
let max xy = if #1(xy) > #2(xy) then #1(xy) else #2(xy)
in max (3, 88) end

```

This permits functions to take multiple arguments and return multiple results.
To extend the interpreter correspondingly, you need to introduce a new kind of
value, namely a tuple value `TupV(vs)`, and to allow eval to return a result of
type value (not just an integer):

```fsharp

type value =
| Int of int
| TupV of value list
| Closure of string * string list * expr * value env
let rec eval (e : expr) (env : value env) : value = ...
```

Note that this requires some changes elsewhere in the eval interpreter. For instance, the primitive operations currently work because eval always returns an
`int`, but with the suggested change, they will have to check (by pattern matching)
that eval returns an `Int i`.

#### Exercise 4.7

Modify the abstract syntax tyexpr and the type checker functions
typ and typeCheck in `TypedFun/TypedFun.fs `to allow functions to take
any number of typed parameters.
This exercise is similar to Exercise 4.3, but concerns the typed language. The
changes to the interpreter function eval are very similar to those in Exercise 4.3
and can be omitted; just delete the eval function.

#### Exercise 4.8

Add lists (`CstN` is the empty list `[]`, `ConC(e1,e2)` is `e1::e2`),
and list pattern matching expressions to the untyped functional language, where
`Match(e0, e1, (h,t, e2))` is match `e0` with
` [] -> e1 | h::t-> e2.`

```fsharp
type expr =
| ...
| CstN
| ConC of expr * expr
| Match of expr * expr * (string * string * expr)
| ..

```
## 实验要求

1. 完成各题目，zip包上传
2. 使用Markdown文件完成，推荐Typora
3. 使用[Git](https://learngitbranching.js.org/)工具管理作业代码、文本文件


[ch04]: https://plc2023.pages.dev/#/04/funlang.type
[ch05]: https://plc2023.pages.dev/#/05/highOrder.typeInfer
