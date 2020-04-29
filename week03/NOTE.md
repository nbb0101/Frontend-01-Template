# 每周总结可以写在这里

### JavaScript语句

* Atom
* Expression
* Statement
* Structure
* Program/Module

#### Grammar

简单语句

* Expression Statement 表达式语句
* Empty Statement 空语句
* Debugger Statement debugger语句，运行时不产生作用
* Throw Statement
* Continue Statement(与循环相互匹配)
* Break Statement(与循环匹配)
* Return Statement

组合语句

* Block Statement
* Iteration

声明

* FunctionDeclaration
* GeneratorDeclaration
* AsyncFunctionDeclaration
* AsyncGeneratorDeclaration
* VariableStatemeny
* ClassDeclaration
* LexicalDeclaration

标签、循环、break、continue

* LabelledStatement
* IterationStatement
* ContinueStatement
* BreakStatement
* SwitchStatement

Runtime

* Complection Record

    [[type]]: normal, break, continue, return, throw
    [[value]]: Types
    [[target]]: label

* Lexical Enviorment

### Javascript对象机制

#### Object

* 任何一个对象都是唯一的，这与它本身的状态无关。
* 即使状态完全一致的两个对象。也并不相等。
* 我们用状态来描述对象。
* 状态的改变即是行为。
* 标示性（Identifier）指针（state）行为（behavior）

#### 基于类的面向对象

* 类是一种常见的描述对象的方式。而“归类”和“分类”则是两个主要的流派。
* 对于“归类”方法而言，多继承是非常自然的事情。如C++。
* 而采用分类思想的计算机语言，则是单继承结构。并且会有一个基类Object。
* 原型是一种更接近人类原始认知的描述对象的方法。
* 我们并不试图做严谨的分类，而是采用“相似”这样的方式去描述对象。
* 任何对象仅仅需要描述它自己与原型的区别即可。

### stringToNumber

``` js

function convertStringToNumber(string, radix = 10) {
  if (radix > 10) {
    return;
  }
  let flag = /e|E/.test(string);
  if (!flag) {
    let chars = string.split('');
    let number = 0;
    let i = 0;
    while (i < chars.length && chars[i] != '.') {
      number = number * radix;
      number += chars[i].codePointAt(0) - '0'.codePointAt(0);
      i++;
    }
    if (chars[i] === '.') {
      i++;
    }
    let fraction = 1;
    while (i < chars.length) {
      fraction /= radix;
      number += (chars[i].codePointAt(0) - '0'.codePointAt(0)) * fraction;
      i++;
    }
    return number;
  } else {
    let logNumber = Number(string.match(/\d+$/)[0]);
    let number = string.match(/^[\d\.]+/)[0].replace(/\./, '');
    if (/e-|E-/.test(string)) {
      return Number(number.padEnd(logNumber + 1, 0));
    } else {
      return Number(number.padStart(logNumber + number.length, 0).replace(/^0/, '0.'));
    }
  }
}

```
### numberToString

```  js

function convertNumberToString(number, radix) {
  let integer = Math.floor(number);
  let fraction = String(number).match(/\.\d+$/);
  if (fraction) {
    fraction = fraction[0].replace('.', '');
  }
  let string = '';
  while (integer > 0) {
    string = String(integer % radix) + string;
    integer = Math.floor(integer / radix);
  }
  return fraction ? `${string}.${fraction}` : string;
}

```