# css部分

- 常见内核
  - IE : Trident (IE6~IE11)
  - Chrome : Webkit -> Blink
  - FireFox : Gecko
  - Opera : Presto -> Webkit -> Blink
  - Safari: Webkit

- 浏览器前缀
  - `-webkit-` : Google Chrome, Safari, Android Browser
  - `-moz-`    : Firefox
  - `-o-`      : Opera
  - `-ms-`     : Internet Explorer, Edge
  - 现在一般由 `autoprefix` 自动补全

  
- 简单判断用户的浏览器类型,通过`navigator.userAgent`
  - 判断[IE](https://juejin.im/post/6844903940719378446)
  - 判断微信
  ```js
    const isWechat =  navigator.userAgent.toLowerCase().includes('micromessenger')
  ```


- css盒模型: 盒模型分为`标准模型`和`IE盒模型`
  - 标准盒模型:包含`content`为边界的宽高
    - `box-sizing:content-box`
  - IE盒模型:包含`border`为边界的总宽高
    - `box-sizing:border-box`
  
  
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
    * 浮动元素，float除了none以外的值；
    * 定位元素，position（absolute，fixed）
    * display为以下其中之一的值inline-block，table-cell，table-caption
    * overflow除了visible以外的值（hidden，auto，scroll）
  * BFC的特性：
    *	内部的box会在垂直方向上一个接一个的放置；
    *	垂直方向上的距离由margin决定；
    *	bfc的区域不会与float的元素区域重叠；
    *	计算bfc的高度时，浮动元素也参与计算；
    *	bfc就是页面上的一个独立容器，容器里面的子元素不会影响外面的元素；
  

- 移动端字体、布局自适应方案
  - rem : 将`html`节点的`fontSize`,作为一个rem单位的基准,通过动态改变`html`节点的`fontSize`,可以改变所有使用rem单位的css属性的大小
    - 动态改变的方法有:
      - js 计算
      - 媒体查询
      - 使用 vw
  - vw/wh : 100vw 就是 100%的视窗宽度

* 问题：实现三栏布局（两侧定宽，中间自适应）

* 答案：五种解决方式：

  * 1 flex布局 ：

    
    ```html
    //html
    <div class="box">
        <div class="left"></div>
        <div class="center"></div>
        <div class="right"></div>
    </div>
    ```
    
    ```css
    .box{
            display: flex;
            justify-items: center;
            height: 200px;
        }
        .left{
            /* height: 100%; */
            width: 200px;
            background-color: red;
        }
        .center{
            background-color: blue;
            height: 100%;
            flex:1;
    }
        .right{
            background-color: pink;
            width: 200px;
            /* height: 100%; */
        }
    
    ```
    
  * 2 浮动方式，此方式 content 必须放在最下边

