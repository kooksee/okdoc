# [定义](http://nim-lang.org/docs/manual.html#definitions)

### 变量和 location

一个 Nim 程序，其实就是一套计算---计算基于内存完成，内存划分为许多组件，这些组件称为 location。我们使用变量表示 location 的名字。变量和 location，都属于某种类型。变量的类型，称为静态类型；location 的类型，称为动态类型。如果静态类型和动态类型不是同一种类型，那么它是此动态类型的祖先类型或者派生的子类型。



### 标识符

标识符是一种符号声明，用来作为变量、类型、过程、... 的名字。它声明的范围称为声明作用域。作用域可以嵌套。



### 表达式

表达式是一个计算，它能得出一个值或者 location。得出 location 的表达式称为 l-value。l-value 既可以表示 location，也可以表示 location 包含的值，这依赖当时的计算环境。

可以静态（在编译期）得出值的表达式，称为常量表达式，它们一定不是 l-value！

> 译注：location 依赖内存，所以只有在运行期才能获取。你无法在编译期通过表达式得出 location。



### 静态错误和运行期错误

静态错误，是程序执行前由编译器进行语法检查时发现的错误。

运行期错误，是程序执行期间发现的错误。出现这种错误，一般是抛出异常、或者致命错误引发崩溃。不管怎么样，我们提供选项，可以激活／禁用运行期的错误检查。查看 **pragmas** 了解更多细节。

运行期错误由异常引起的、还是致命错误引起的，要由实际的场景决定。下面这个程序总是无效的：

```nim
var a: array[0..1, char]
let i = 5
try:
    a[i] = 'N'
except IndexError:
    echo "invalid index"
```

为了编写安全的程序，应该总在适当的地方执行运行期错误检查。遗漏运行期错误检查，可能会导致无法预料的问题。




