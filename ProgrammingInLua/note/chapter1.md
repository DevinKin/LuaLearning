# 第1章-起点

## Chunks

- Chunk是一系列语句，Lua执行的每一块语句。
- 可以通过指定参数然Lua执行一系列Chunk。
  - 假定一个文件a内有单个语句`x=1`，另一个文件b有语句`print(x)`
  - `lua -la -lb`命令首先在一个Chunk内运行a然后运行b。
  - `-l`选项会调用`require`，将会在指定的目录下搜索文件。
- `-i`选项要求运行指定Chunk后进入交互模式。
  - `lua -i -la -lb`
- 另一个连接外部Chunk的方式是使用`dofile`函数，`dofile`函数加载文件并执行它。

## 全局变量

- 全局变量不需要声明。
- 访问一个没有初始值的全局变量不会报错，只不过得到的结果是`nil`。

## 词法约定

- lua的保留字。

  ```lua
  and	break	do	else	elseif
  end	false 	for function	if
  in	local	nil	not	or
  repeat return then true until
  while
  ```

- 单行注释`--`

- 多行注释`--[[ --]]`

## 命令行方式

- 语法

  ```shell
  lua [options][script [args]]
  ```

- options选项

  - `-e`直接将命令传入Lua，例`lua -e "print(math.sin(12))"`
  - `-l`加载一个文件。
  - `-i`进入交互模式。

- `_PROMPT`内置变量作为交互模式的提示符。

  - `lua -i -e "_PROMPT=' lua> '"`

- Lua的运行过程，在运行参数之前，Lua会查找环境变量`LUA_INIT`的值。

  - 如果变量存在并且值为`@filename`，Lua将加载指定文件。
  - 如果变量存在但不是以`@`开头，Lua假定filename为Lua代码文件并且运行它。
  - 利用这个特性，可以通过配置，灵活的设置交互模式的环境。可以加载包，修改提示符和路径，定义自己的函数，修改或者重命名函数等。

- 全局变量`arg`存放Lua的命令行参数。

