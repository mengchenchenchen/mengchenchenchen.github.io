# let 和 const 命令

* 基本用法

  * es6 新增了let命令，用来声明变量。他的用法类似于var，只不过是在代码块里面有效果。

    ```js
    {
    	let a = 10;
         var b = 20;
    }
    console.log(a);//ReferenceError: a is not defined.
    console.log(b);//20
    ```

  * let 命令适用于 for 循环计数器：

    ```js
    for(let i = 0;i < 10; i++){
        //...
    }
    console.log(i);//ReferenceError: a is not defined.
    ```

    