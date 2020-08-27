# css 部分

- 常见内核

  - IE : Trident (IE6~IE11)
  - Chrome : Webkit -> Blink
  - FireFox : Gecko
  - Opera : Presto -> Webkit -> Blink
  - Safari: Webkit

- 浏览器前缀

  - `-webkit-` : Google Chrome, Safari, Android Browser
  - `-moz-` : Firefox
  - `-o-` : Opera
  - `-ms-` : Internet Explorer, Edge
  - 现在一般由 `autoprefix` 自动补全

- 简单判断用户的浏览器类型,通过`navigator.userAgent`
  - 判断[IE](https://juejin.im/post/6844903940719378446)
  - 判断微信
  ```js
  const isWechat = navigator.userAgent.toLowerCase().includes("micromessenger");
  ```

* css 盒模型: 盒模型分为`标准模型`和`IE盒模型`

  - 标准盒模型:包含`content`为边界的宽高
    - `box-sizing:content-box`
  - IE 盒模型:包含`border`为边界的总宽高
    - `box-sizing:border-box`

- 问题：有没有遇到过边距重叠，怎么解决边距重叠问题

- 答案：利用 BFC 的特性，把另一个盒子放入另一个独立的 BFC 中，从而使得两个盒子之前互相不受影响

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

- 问题：说一下 BFC

- 答案：

  - 什么是 BFC
    - BFC 是（block formatting context）格式化上下文，是 web 页面盒布局模型的 css 渲染模式，值得是一个独立的渲染区域或者说是一个隔离的独立容器。
  - 形成 BFC 的条件
    - 浮动元素，float 除了 none 以外的值；
    - 定位元素，position（absolute，fixed）
    - display 为以下其中之一的值 inline-block，table-cell，table-caption
    - overflow 除了 visible 以外的值（hidden，auto，scroll）
  - BFC 的特性：
    - 内部的 box 会在垂直方向上一个接一个的放置；
    - 垂直方向上的距离由 margin 决定；
    - bfc 的区域不会与 float 的元素区域重叠；
    - 计算 bfc 的高度时，浮动元素也参与计算；
    - bfc 就是页面上的一个独立容器，容器里面的子元素不会影响外面的元素；

* 移动端字体、布局自适应方案
  - rem : 将`html`节点的`fontSize`,作为一个 rem 单位的基准,通过动态改变`html`节点的`fontSize`,可以改变所有使用 rem 单位的 css 属性的大小
    - 动态改变的方法有:
      - js 计算
      - 媒体查询
      - 使用 vw
  - vw/wh : 100vw 就是 100%的视窗宽度

- 问题：实现三栏布局（两侧定宽，中间自适应）

- 答案：五种解决方式：

  - 1 flex 布局 ：
    <vuep template="#example"></vuep>

    <script v-pre type="text/x-template" id="example">
      <style scoped>
        .wx-wrapper {
          width: 100%;
          display: flex;
          justify-content: space-between;
        }
        .left {
          width: 100px;
          background-color: blue;
        }
        .right {
          width: 100px;
          background-color: red;
        }
        .center {
          flex: 1 1 auto;
          background-color: pink;
        }
      </style>
      <template>
        <div class="wx-wrapper">
          <div class="left">left</div>
          <div class="center">center</div>
          <div class="right">right</div>
        </div>
      </template>

      <script>
        module.exports = {
          data () {
            return { }
          }
        }
      </script>
    </script>

  - 2 浮动方式，此方式 content 必须放在最下边
    <vuep template="#example"></vuep>

    <script v-pre type="text/x-template" id="example">
      <style scoped>
        .wx-wrapper {
          width: 100%;
          height:200px;
        }
        .left {
          width: 100px;
          background-color: blue;
        }
        .right {
          width: 100px;
          background-color: red;
        }
        .center {
          flex: 1 1 auto;
          background-color: pink;
        }
      </style>
      <template>
        <div class="wx-wrapper">
          <div class="left">left</div>
          <div class="right">right</div>
          <div class="center">center</div>
        </div>
      </template>

      <script>
        module.exports = {
          data () {
            return { }
          }
        }
      </script>
    </script>
    
  - 绝对定位方式实现
  <vuep template="#example"></vuep>

    <script v-pre type="text/x-template" id="example">
      <style scoped>
        .wx-wrapper {
          height:200px;
          position:relative;
        }
        .left {
          position:absolute;
          width: 100px;
          background-color: blue;
          left:0;
        }
        .right {
          position:absolute;
          width: 100px;
          right:0;
          background-color: red;
        }
        .center {
          position:absolute;
          left:100px;
          right:100px;
          background-color: pink;
        }
      </style>
      <template>
        <div class="wx-wrapper">
          <div class="left">left</div>
          <div class="center">center</div>
          <div class="right">right</div>
        </div>
      </template>

      <script>
        module.exports = {
          data () {
            return { }
          }
        }
      </script>
    </script>

  - 表格布局实现方式（有问题）
  <vuep template="#example"></vuep>

    <script v-pre type="text/x-template" id="example">
      <style scoped>
        .left4{
          width: 200px;
          background-color: red;
          display: table-cell;
        }
        .center4{
          background-color: yellow;
          display: table-cell;
        }
        .right4{
          width: 200px;
          background-color: green;
          display: table-cell;
        }
      </style>
      <template>
          <div class="box4">
          <div class="left4"></div>
          <div class="center4"></div>
          <div class="right4"></div>
      </div>
      </template>

      <script>
        module.exports = {
          data () {
            return { }
          }
        }
      </script>
    </script>
    
  - grid 布局方式
  
    ```css
    
    ```
  
    
  



​    

  


