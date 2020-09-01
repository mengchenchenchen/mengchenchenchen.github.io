# [grid](http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html)

> grid 布局 与 flex 布局：

* 有一定的相似性，但是flex 是 轴线布局，只能指定“元素”针对轴线的位置，可以看作一维布局。Grid是将容器分为行和列，产生单元格，然后指定“项目所在”的单元格，可以看作是二维布局。Grid布局远比Flex布局强大。（介绍这么说的，我还不太会）

> 基本概念：

* 容器和项目：

  * 采用网格布局的区域，称为“容器”（container），容器内部采用网格 定位的子元素，称为项目（item）。

    ```html
    <div class="container">
        <div class="item"><p>1</p></div>
        <div class="item"><p>2</p></div>
        <div class="item"><p>3</p></div>
    </div>
    ```

* 行和列：容器里面的水平区域称为行，垂直区域称为列；

* 单元格：行和列的交叉区域，称为单元格(cell);一般情况下，n行和m列会产生n*m个单元格。

* 网格线：划分网格的线；

> 容器的属性：

* display属性：

  * display：grid；指定一个容器采用网络布局。(容器元素是块级元素)

  * display：inline-grid;(容器元素是是行内元素)

* 注意事项：
  
  * 设置为网格布局以后，容器子元素(项目)的float、display:inlline-block、display：table-cell、vertical-align和colum-*等设置都将失效。
  
* grid-template-columns属性，grid-template-rows属性

  ```css
  .container {
    display: grid;
    grid-template-columns: 100px 100px 100px;
    grid-template-rows: 100px 100px 100px;
  }
  ```

  * 指定了三乘三的网格，列宽和行高都是100px,除了绝对的单位还可以使用百分比；

  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(3, 33.33%);
    grid-template-rows: repeat(3, 33.33%);
  }
  ```
  
  * repeat(),可以接受两个参数，第一个为重复次数，第二个 是要重复的值；
  
  ```css
  .container {
      display: grid;
      grid-template-columns: repeat(3, 33.33%);
      grid-template-rows: repeat(3, 33.33%);//第一种
      grid-template-columns: repeat(2, 100px 20px 80px);//第二种
  }
  ```
  
  * auto-fill 关键字：有时候单元格的大小是固定的，但是容器不固定，如果希望每一行或者每一列都能容纳更多的单元格，这时候auto-fill关键字表示自动填充。
  
  * fr关键字 ：如果两列的宽度分别为1fr 好人2fr，表示后者是前者的两倍。
  
    ```css
    .container{
        display:grid;
        grid-template-columns:1fr 2fr;
    }
    ```
  
    