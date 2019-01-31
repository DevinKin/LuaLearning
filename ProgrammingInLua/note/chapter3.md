# 第3章-表达式

## 算术运算符

- 二元运算符
  - +
  - -
  - *
  - /
  - ^
- 一元运算符`-`负值。

## 关系运算符

```lua
<	>	<=	>=	==	~=
```

- `==`和`~=`比较两个值，如果两个值类型不同，Lua认为两者不同。
- `~=`用于比较两个值或类型是否不相等，不相等返回true，相等返回false。
- nil只和自己相等。
- Lua通过引用比较tables，userdata，funcitons。也就是说当且仅当两者表示同一个对象时相等。

## 逻辑操作符

```lua
and	or	not 
```

## 连接运算符

```lua
..
```

## 优先级

- 从高到低

  ```lua
  ^（幂）
  not -(负数)
  *	/
  +	-
  ..
  <	>	<=	>=	~=	==
  and
  or
  ```

- 除了`^`和`..`以外所有二元运算符都是左连接。

## 表的构造

- 构造器是创建和初始化表的表达式。

- 表是Lua特有的，最简单的构造函数是`{}`，用来创建一个空表。

- 构造函数可以使用任何表达式初始化。

-  不管用何种方式创建表，我们都可以向表中添加或者删除任何类型的域，构造函数仅仅影响表的初始化。

  ```lua
  w = {x = 0, y = 0, label="console"}
  x = {math.sin(0), math.sin(1), math.sin(2)}
  w[1] = "another field"
  x.f = w
  print(w["x"])
  print(w[1])
  print(x.f[1])
  w.x = nil
  ```

- 同一个构造函数中可以混合列表风格和record风格进行初始化。

  ```lua
  polyline = {color="blue", thickness=2, npoints=4,
      {x=0, y=0},
      {x=-10, y=0},
      {x=-10, y=1},
      {x=0, y=1}
  }
  
  print(polyline[2].x)
  ```

- 用`[expression]`显示的表示将被初始化的索引。

  ```lua
  opnames = {["+"] = "add", ["-"] = "sub",
      ["*"] = "mul", ["/"] = "div"
  }
  
  i = 20;
  s = "-"
  a = {[i+0] = s, [i+1] = s..s, [i+2] = s..s..s}
  print(opnames[s])
  print(a[22])
  ```

- list风格初始化和record风格初始化的特例

  - `{x=0,y=0}`对应`{["x"]=0,["y"]=0}`
  - `{"red","green","blue"}`对应`{[1]="red",[2]="green",[3]="blue"}`

- 数组下标从0开始，不推荐，很多标准库不能使用。

  ```lua
  days = {[0]="Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"}
  ```

- 构造函数的最后的`,`是可选的，方便以后扩展。

- 在狗仔函数域分隔符`,`，可以用分号`;`替代，通常我们使用分号用来分割不同类型的表元素。

  ```lua
  {x=10, y=45; "one", "two", "three"}
  ```

  