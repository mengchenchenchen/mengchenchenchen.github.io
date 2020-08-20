# css部分

* 问题：说一下css盒模型

* 答案：盒模型分为标准模型和怪异模型（IE盒模型）：
  * 标准盒模型：盒模型的宽高只是内容（content）的宽高；
  * 怪异盒模型：盒模型的宽高是内容（content）+ 内边距（padding）+ 外边距（margin）的总宽高；
  
* 问题：css如何设置两种模型

  ```js
  //标准模型
  box-sizing:content-box;
//IE模型
  box-sizing:border-box;
  ```
  
* 问题：有没有遇到过边距重叠，怎么解决边距重叠问题
  
* 答案：利用BFC的特性，把另一个盒子放入另一个独立的BFC中，从而使得两个盒子之前互相不受影响
  
  ```js
  <section class="top">
      <h1>上</h1>
      margin-bottom:30px;
  </section>
  <div style="overflow: hidden;">//添加新的div
      <section class="bottom">
      <h1>下</h1>
      margin-top:50px;
      </section>
  </div>
  ```
  
* 问题：说一下BFC

* 答案：
  * 什么是BFC
    * BFC是（block formatting context）格式化上下文，是web页面盒布局模型的css渲染模式，值得是一个独立的渲染区域或者说是一个隔离的独立容器。
  * 形成BFC 的条件
    *  浮动元素，float除了none意外的值；
    * 定位元素，position（absolute，fixed）
    * display为以下其中之一的值inline-block，table-cell，table-caption
    * overflow除了visible以外的值（hidden，auto，scroll）
  * BFC的特性：
    *	内部的box会在垂直方向上一个接一个的放置；
    *	垂直方向上的距离由margin决定；
    *	bfc的区域不会与float的元素区域重叠；
    *	计算bfc的高度时，浮动元素也参与计算；
    *	bfc就是页面上的一个独立容器，容器里面的子元素不会影响外面的元素；
  
* 问题：rem原理

*	答案：rem布局的本质是等比缩放，一般是基于宽度，假设将屏幕分为100份，每份宽度是1rem，1rem的宽度是屏幕宽度/100,然后子元素设置rem单位的属性。

