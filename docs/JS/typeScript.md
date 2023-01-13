# typeScript

## typeScript 是什么
* typeScript 是一种由微软开发的自由和开源的编程语言。它是JavaScript的一个超集，TypeScript 在 JavaScript 的基础上添加了可选的静态类型和基于类的面向对象编程。

* 其实TypeScript 就是相当于 JavaScript 的增强版，但是 最后运行时还需要编译成JavaScript。TypeScript 最大的目的是 让程序员更具创造性，提高生产力，它将极大增强JavaScript 编写应用的开发和调试环节，让JavaScript 能够 方便用于编写大型应用和进行多人协作。

## TypeScript和JavaScript 的对比

* TypeScript 是一个应用程序级别的JavaScript 开发语言。
*  TypeScript 是JavaScript 的超集，可以编译成纯JavaScript。这个和我们css使用less 和scss 是很像的，我们用更好的代码编写方式来进行编写，最后还是会生成原生的JavaScript语言。

## TypeScript

* typeScript 的类型有
  * undefined
  * Number:数字类型
  * String：字符串类型
  * Boolean:布尔类型
  * enum:枚举类型
  * any:任意类型，一个能兼容所有的类型
  * void:空类型
  * Array:数组类型
  * Tuple:元祖类型
  * Null:空类型
* Undefined类型
  * 在js中当你定义了一个变量，但是没有给他赋予任何值的时候，他就是Undefined类型。
  * 比如声明一个年龄的变量 `age`,我们要使用数值类型，也就是 `number`,不给他任何值，我们只是在控制台给他输出，观察结果。

  ```ts
  //声明数值类型的变量age,但不予赋值
  
  var age:numberconsole.log(age)
  
  ```
