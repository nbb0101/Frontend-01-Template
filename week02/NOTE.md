# 编程语言通识与javascript语言设计

### 语言按语法分类

* 非形式语言
1. 中文，英文
* 形式语言（乔姆斯基谱系）
1. 0型 无限制文法
2. 1型 上下文相关文法
3. 2型 上下午无关文法
4. 3型 正则文法

### 产生式（BNF）

* 用尖括号括起来的名称来表示语法结构名
* 语法结构分成基础结构和需要用其他语法结构定义的复合结构
* 引号和中间的字符表示终结符
* 可以有括号
* *表示重复多次
* ｜表示或
* +表示至少一次

# 词法 类型

### Unicode

* A的码点撕65，a的是97，最初的字符集ASCII,共128个。

### Input Element

* WhiteSpace
* LineTermaintor
* Comment
* Token
      Punctuator
      Keywords
      IdentifierName
      Literal

### WhiteSpace

* < TAB > >>>U+0009
* < VT >  >>>U+0011
* < FFF > >>>U+000C 
* < SP > >>>U+0020
* < NBSP > >>>U+00A0
* < ZWNBSP > >>>U+00A0
* < USP >    U+FEFE
 
### Literal
* Number
* String
* Boolean
* Null
* Undefined
* Symbol
* Bigint
* Object