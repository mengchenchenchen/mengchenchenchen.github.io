# felx

* flex 布局 为弹性布局，任何一个容器都可以成为flex布局：

  ```less
  //块级元素
  .box{
      display:flex;
  }
  //行内元素
  .box{
      display:inline-flex;
  }
  //webkit 内核浏览器 必须加上-webkit前缀
  .box{
     display:-webkit-flex;//safari
     display:flex;
  }
  ```

* 基本概念：

  * flex-direction 决定方向，项目的排列方向

    ```less
    .box{
    	flex-direction:row | row-reverse | column | column-reverse;//默认row
    }
    ```

  * flex-wrap  可让同一行的元素 换行

    ```less
    .box{
        flex-wrap:nowrap|wrap|wrap-reverse;//默认 nowrap;wrap-reverse 第一行在下面
    }
    ```
    
  * flex-flow 是flex-direction || flex-wrap 属性的简写形式，默认值  row | nowrap

    ```less
    .box{
    	 flex-flow: <flex-direction> || <flex-wrap>;
    }
    ```

  * justify-content 在主轴上的对齐方式

    ```less
    .box {
      justify-content: flex-start | flex-end | center | space-between | space-around;//默认值 flex-start
    }
    ```

  * align-item 在交叉轴上的对齐方式

    ```less
    .box {
      align-items: flex-start | flex-end | center | baseline | stretch;
    }
    ```

  * align-content  定义了多根轴线的对齐方式

    ```js
    .box {
      align-content: flex-start | flex-end | center | space-between | space-around | stretch;
    }
    ```

  * order 定义项目的排列顺序，数值越小，排列越靠前，默认0

    ```less
    .item {
      order: <integer>;
    }
    ```

  * flex-grow  定义项目的放大比例，默认0，即使有剩余空间，也不放大。

    * 如果flex-grow都为1，则等分剩余空间，如果其中一个属性为2，其他都为1，则占据着都将比其他项多一倍。

    ```less
    .item {
      flex-grow: <number>; /* default 0 */
    }
    ```

  * flex-shrink 定义等比缩小，默认1，空间不足，该项目缩小

    * 如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。

    ```less
    .item {
        flex-shrink: <number>; /* default 1 */
  }  
    ```
    
  * flex-basis 定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

    * 它可以设为跟`width`或`height`属性一样的值（比如350px），则项目将占据固定空间

    ```less
    .item {
      flex-basis: <length> | auto; /* default auto */
    }
    ```

  * flex 属性是flex-grow，flex-shrink和flex-basis的简写，默认值为0 1 auto

    * 该属性有两个快捷值：`auto` (`1 1 auto`) 和 none (`0 0 auto`)。

    ```less
    .item {
      flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
    }
    ```

    

