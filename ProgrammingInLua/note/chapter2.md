# 第2章-类型和值

- Lua是动态类型语言，变量不要类型定义。
- Lua有8个基本类型
  - nil
  - boolean
  - number
  - string
  - userdata
  - function
  - thread
  - table
- 函数`type`可以测试给定变量或值的类型。

## NIl

- 全局变量没有被赋值以前默认值是`nil`。

## Boolean

- 取值为`true`和`false`。
- 控制结构的条件中除了`false`和`nil`为假，其他值都为真。
- Lua认为0和空字符串都是真。

## Number

- Lua中没有整数，Numbers表示实数。

## String

- `string`指字符的序列。

- lua是8位字节，所以字符串可以包含任何数值字符。

- `string`和其他对象一样，Lua自动进行内存分配和释放。

- Lua可以高效的处理长字符串。

- 可以使用单引号或者双引号表示字符串。

- Lua中的转义序列有

  - `\a`bell
  - `\b`back space（后退）
  - `\f`form feed（换页）
  - `\n`newline（换行）
  - `\r`carriage return（回车）
  - `\t`horizontal tab（制表）
  - `\v`vertical tab
  - `\\`backslash
  - `\"`double quote（双引号）
  - `\'`single quote（单引号）
  - `\[`left square bracket（左中括号）
  - `\]`right square bracket（右中括号）

- Lua还可以使用`[[...]]`表示字符串，这种形式的字符串可以包含多行，可以嵌套且不会解释转义序列，如果第一个字符是换行符会被自动忽略掉。

  - `[=[]=]`转义嵌套`[[]]`字符串。

  - 示例

    ```lua
    page = [=[
    <HTML>
    <HEAD>
    <TITLE>An HTML Page</TITLE>
    </HEAD>
    <BODY>
    Lua
    [[
    a text between double brackets
    ]]
    </BODY>
    </HTML>
    ]=]
    
    io.write(page)
    ```

    