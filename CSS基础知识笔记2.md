# 所有的选择其都是找标签
# css优先级
###  优先级公式：继承（继承不计算权重） < 通配符选择器 < 标签选择器 < 类选择器< id选择器 < 行内样式选择器 < !important
+ 谁更精准找到想要的标签，谁生效
+ !important 提权  例子 color: red !important;

+ 选择器权重叠加计算  先算行内-id-类-标签（0,0,0,0）

+ div #one .class (行内=0 id=1 类=1 标签=1） 这个大
+ 0111>0011
+ div .class (行内=0 id=0 类=1 标签=1) 这个小
+ 如果优先级相同 则比较层叠性，谁在下面谁生效 
+ 注意： !important 如果不是继承 那么权重最高（慎重使用） 如果遇到继承 那么他最低

## 如果遇到样式出不来，要学会通过调试工具找错
![差错流程](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E6%9F%A5%E9%94%99%E6%B5%81%E7%A8%8B.jpg)

# 盒子模型 
> #### 盒子的概念
>> ##### 1. 页面中的每一个标签都是一个盒子，通过盒子的视角更方便布局
>> ##### 2.浏览器在渲染网页时，会将网页中的元素看做是一个个矩形区域，我们也形象的称之为 盒子
> #### 盒子模型
>> ##### css中规定每个盒子分别由： 内容区域（content），内边距区域（padding），边框区域（border），外边距区域（margin）构成，这就是盒子模型。
***
### 一个盒子的布局顺序
+ 1. 从外到内，从上往下  先看最外层，然后逐步分析
+ 2. 每一个盒子的样式
>> 每个盒子都有宽度和高度  辅助的背景色 盒子的组成边框，内边距，外边距。。。其他样式：color , font- , text-,....

# 新浪导航 
>> ##### 写法：从外到内：先宽高背景色，让后放内容，调节内容的位置，控制细节。。
```
    <style>
        * {
            box-sizing: border-box;
            /*让盒子以边框总尺寸*/
        }

        .box1 {
            height: 50px;
            border-top: 2px solid orange;
            border-bottom: 1px solid #edeef0;
        }

        .box1-1 {
            float: left;
        }

        .box1-2 {
            float: right;
        }

        .box2 {
            line-height: 48px;
            width: 100px;
            text-align: center;
        }

        .nova-a {
            text-decoration: none;
            padding: 13px;
            color: black;
        }

        .nova-a:hover {
            color: chocolate;
        }

        .box2:hover {
            background-color: #e6e6e6;
        }
    </style>
</head>

<body>
    <div class="box1">
        <div class="box1-1 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-1 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-1 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-1 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-2 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-2 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-2 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
        <div class="box1-2 box2">
            <a href="#" class="nova-a">新浪导航</a>
        </div>
    </div>
</body>
另外一种写法
    <style>
        *{
            box-sizing: border-box;
        }
        .box1{
            height: 40px;
            border-top: 1px solid orange;
            border-bottom: 1px solid #000;
        }
        .box1 a{
            padding: 0 16px;  /* 随内容撑开加padding属性 */
            /* width: 80px; */
            height: 40px;
            display: inline-block;
            text-align: center;
            line-height: 40px;
            font-size: 12px;
            text-decoration: none;
        }
        .box1 a:hover{
            background-color: #edeef0;
            color: orange;
        }
    </style>
</head>

<body>
    <div class="box1">
        <a href="">新浪导航</a>
        <a href="">新浪导航</a>
        <a href="">新浪导航</a>
        <a href="">新浪导航</a>
    </div>
</body>

```
![新浪导航](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E6%96%B0%E6%B5%AA%E5%AF%BC%E8%88%AA.jpg)

### 盒子模型（自动内减）（内减模式）
> ##### 给盒子设置属性 ： box-sizing:border-box; 浏览器会自动计算多余大小，自动在内容中减去
***
##  网页的有效内容居中 叫做 版心居中
+ 如果想让某个板块水平居中，那么就给这个板块设置 margin: 0 auto;

```
    <style>
        * {
            margin: 0;
            padding: 0;
            /* 为所有标签内减模式*/
            box-sizing: border-box;
        }

        .box1 {
            width: 500px;
            height: 400px;
            background-color: #bfc;
            border: 1px solid #ccc;
            margin: 50px auto;
            padding: 42px 30px 0;
        }

        .box1 h2 {
            border-bottom: 1px solid #ccc;
            padding-bottom: 5px;
            font-size: 30px;
        }
        ul{ /* 去掉列表符号 */
            list-style: none;
        }
        ul li{
            height: 50px;
            border-bottom: 1px dashed #ccc;
            /* dashed 虚线 solid 实线 */
            line-height: 50px; /*文字垂直居中显示 */
            /*padding-left:28px ; 调整文字位置*/
        }
        li a{
            text-decoration: none; /*去掉a链接下划线 */
            margin-left: 25px; /*调整文字位置 */
            color: #666;
            font-size: 18px;
        }
    </style>
</head>

<body>
    <div class="box1">
        <h2>最新文章/New Articles</h2>
        <ul>
            <li><a href="#">北京招聘网页设计，平面设计，php</a></li>
            <li><a href="#">北京招聘网页设计，平面设计，php</a></li>
            <li><a href="#">北京招聘网页设计，平面设计，php</a></li>
            <li><a href="#">北京招聘网页设计，平面设计，php</a></li>
            <li><a href="#">北京招聘网页设计，平面设计，php</a></li>
        </ul>
    </div>
</body>
</body>
```
![版心居中](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E7%89%88%E5%BF%83%E5%B1%85%E4%B8%AD.jpg)
***
> ##### 外边距折叠现象：
> 合并：垂直布局的块级元素，上下的margin会合并  最终两者距离为设置的margin的最大值的那一方生效  我们只需要给其中一个盒子设置margin即可

> 坍塌：互相嵌套的块级元素，子元素的margin-top会作用在父元素上
> 会导致父元素一起往下移动
> 解决办法 : 
> 1. 给父元素设置 border-top 或者 padding-top (分隔父子元素的 margin-yop)
> 2. 给父元素设置overflow: hidden ; 完美解决办法
> 3. 转换成行内块元素
> 4. 设置浮动 
```
    <style>
        .father {
            width: 300px;
            height: 300px;
            background-color: orange;
            /* 给父元素添加外边距也可能解决坍塌问题 */
            /* border: 1px solid #000; */
          /* 给父元素设置隐藏也可能解决坍塌问题 */ 
            overflow: hidden;
        }

        .son {
            width: 200px;
            height: 200px;
            background-color: pink;
            /* 给这个子元素设置margin-top会传递给父元素，导致父元素一起设置外上边距,所以会发生坍塌事件*/
            /* margin-top: 50px; */
        }
    </style>
</head>

<body>
    <div class="father">
        <div class="son">son</div>

    </div>
</body>
```
![解决坍塌](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E8%A7%A3%E5%86%B3%E5%9D%8D%E5%A1%8C.jpg)
***
