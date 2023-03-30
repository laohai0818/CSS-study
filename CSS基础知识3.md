# 所有的选择器都是找标签
### 行内元素 如果想要通过margin 或 padding 改变行内标签的垂直位置，无法生效，如果想要改变行内元素的垂直位置给这个元素设置行高（ line-height: *** ; ）
***

### 结构伪类选择器
> + 根据元素在HTML中的结构关系查找元素
> + 减少对于HTML中 类 的依赖，有利于保持代码整洁
> + 常用于查找某父级选择器中的子元素

|选择器|说明|
|:---:|:---:|
|E:first-child{}|匹配父元素中的第一个子元素，并且是E元素|
|E:last-child{}|匹配父元素中最后一个子元素，并且是E元素|
|E:nth-child{n}|匹配父元素中的第n个子元素，并且是E元素|
|E:nth-last-child{n}|匹配父元素中倒数的第n个子元素，并且是E元素|
+ **n**是从0开始的
 >可以填公式 2n代表偶数，意思是全选择2，4，6，8，10...的偶数，如果是4n,则选的是4，8，16.。。如果是2n+1或者-1 取到的是奇数3，5，7..，如果是-n+5,代表选择是前五个，-n+3代表前三个， 如果是n+5 代表的是从第5个往后的
```
    <style>
        li:first-child {
            /*正数第一个li*/
            color: blue;
        }

        li:last-child {
            /*倒数第1个li*/
            color: aqua;
        }

        li:nth-child(6) { 
            /*正数第6个li 一般都使用这个*/
            color: blue;
        }

        li:nth-last-child(5) {
            /*倒数第5个li*/
            color: blueviolet;
        }
    </style>
</head>

<body>
    <ul>
        <li>这是第1个li</li>
        <li>这是第2个li</li>
        <li>这是第3个li</li>
        <li>这是第4个li</li>
        <li>这是第5个li</li>
        <li>这是第6个li</li>
        <li>这是第7个li</li>
        <li>这是第8个li</li>
    </ul>
</body>
```

![结构伪类选择器](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E7%BB%93%E6%9E%84%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8.jpg)

## 伪元素：一般页面中的非主体内容可以使用伪元素
> 区别：元素为html设置的标签，伪元素为通过CSS模拟创建出来的假标签，一般用来设置装饰性的小图，找到父级元素，在这个父级元素内容里面创建子标签

|伪元素|作用|
|:---:|:---:|
|::before|在父元素'内容']'的最前面添加一个伪元素|
|::after|在父元素'内容'的最后面添加一个伪元素|
|必须设置content属性才能生效|伪元素默认是行内元素|

# 浮动布局
> 1. 让哪个元素浮动就给哪个元素添加 float: left 或者 right;
> 2. 浮动的标签是顶部对齐的，浮动找浮动，下一个浮动会在上一个浮动元素的后面左右浮动
> 3. 浮动的元素一行可以显示多个，并且可以设置宽高--浮动后的元素具备行内块特点
> 4. 浮动后的元素，不能通过text-align:center;或者margin:0 auto; 来设置元素居中，
> 4. 如果父级元素的宽度不够，子级会自动换行
### CSS的书写顺序
> 1. 给元素添加的浮动或者display 属性 要放在第一位
> 2. 添加盒子模型相关的属性：宽高边距
> 3. 添加文字的样式

```
    <style>
        body {
            /* 给整个网页设置背景颜色 */
            background-color: rgb(141, 193, 238);
        }
        /** 浏览器在解析行内块元素和行内元素的时候，如果代码换行，会产生一个空格的间距 */
        /* 给头部设置样式 */
        .header { 
            width: 80%;
            height: 70px;
            background-color: pink;
            margin: 0 auto; /*让这个元素在整个页面中水平居中*/
            text-align: center; /*让内容水平居中*/
            line-height: 70px; /*让内容垂直居中*/
        }

        .content {
            width: 80%;
            height: 400px;
            margin: 10px auto;
            text-align: center;
            line-height: 200px;
        }

        .footer {
            width: 80%;
            height: 70px;
            background-color: lemonchiffon;
            margin: 0 auto;
            text-align: center;
            line-height: 100px;
        }

        .left_content {
            width: 70%;
            height: 100%;
            background-color: orange;
            float: left;
            

        }

        .sidebar {
            width: 27%;
            height: 100%;
            background-color: aquamarine;
            float: right; 
            /* 单独的一个块，不在中间内容的大局域里面，左右单独设置 */
        }

        .part1 {
            width: 30%;
            height: 100%;
            background-color: aqua;
            float: left;
            margin-right: 2.5%;
        }

        .part2 {
            width: 35%;
            height: 100%;
            background-color: rgb(0, 255, 157);
            float: left;
        }

        .part3 {
            width: 30%;
            height: 100%;
            background-color: rgb(0, 110, 255);
            float: right;
        }
    </style>
    </head>
    <body>
    <div>
        <div class="header">头部</div>
        <div class="content">
            <!-- 内容栏 -->
            <div class="left_content">
                <div class="part1">part1</div>
                <div class="part2">part2</div>
                <div class="part3">part3</div>
            </div>
            <!-- 侧边栏 -->
            <div class="sidebar">侧边</div>
        </div>
        <div class="footer">底部</div>
    </div>
```
![浮动的布局](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE2/%E6%B5%AE%E5%8A%A8%E7%9A%84%E5%B8%83%E5%B1%80.jpg)

    <style>
        * {
            margin: 0;
            padding: 0;
        }
        .box1 {
            width: 1226px;
            height: 614px;
            /* background-color: #666; */
            margin: 50px auto;
        }
        .zuo {
            float: left;
            width: 234px;
            height: 614px;
            background-color: #800080;
        }
        .you {
            float: right;
            width: 978px;
            height: 614px;
            /* background-color: pink; */
        }
        ul {
            /*清除UL里面li的无序列表样式*/
            list-style: none;
        }
        .you li {
            /* 让小块统一左浮动 */
            float: left;
            width: 234px;
            height: 300px;
            background-color: aqua;
            margin-right: 14px;
            margin-top: 14px;
        }
        /*取消第4个和第8个的右间距*/
        .you li:nth-child(4n) {
            margin-right: 0;
        }
        /*取消前4个的上间距*/
        .you li:nth-child(-n+4) {
            margin-top: 0;
        }
    </style>
    </head>
    <body>
    <div class="box1">
        <div class="zuo"></div>
        <div class="you">
            <ul>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
                <li></li>
            </ul>
        </div>
    </div>
    </body>

![浮动布局小案例](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE2/%E6%B5%AE%E5%8A%A8%E5%B8%83%E5%B1%80%E5%B0%8F%E6%A1%88%E4%BE%8B.jpg)

### 网页主导航浮动案例

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .box {
            width: 640px;
            height: 50px;
            background-color: #ffc0cb;
            margin: 50px auto;
        }
        .box li {
            float: left;
            list-style: none;
        }
        .box li a {
            /* a标签属于行内元素，需要设置宽高必须转给块元素 */
            display: inline-block;
            width: 80px;
            height: 50px;
            /* 内容水平居中 */
            text-align: center;
            /* 行高垂直居中 */
            line-height: 50px;
            text-decoration: none;
            color: aliceblue;
            
            /* 让A标签的区域大一点加padding属性 */
            /* padding: 10px 10px; */
           
        }
        .box li:hover {
            background-color: #008000;
        }
    </style>
    </head>
    <!-- 做网站的主导航，必须是li里面套a -->
    <body>
        <div class="box">
            <ul>
                <li><a href="#">新闻1</a></li>
                <li><a href="#">新闻2</a></li>
                <li><a href="#">新闻3</a></li>
                <li><a href="#">新闻4</a></li>
                <li><a href="#">新闻5</a></li>
                <li><a href="#">新闻6</a></li>
                <li><a href="#">新闻7</a></li>
                <li><a href="#">新闻8</a></li>
            </ul>
        </div>
    </body>
![网站主导航浮动案例](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE2/%E7%BD%91%E7%AB%99%E4%B8%BB%E5%AF%BC%E8%88%AA%E6%B5%AE%E5%8A%A8%E6%A1%88%E4%BE%8B.jpg)

## 受浮动影响的情况：父子级标签，子级标签浮动，且父级标签没有高度，那么后面的标准流盒子会受到影响，会显示到上面的位置
 >  解决高度坍塌的方法就是 在父元素 “内容” 的后面添加一个元素，给这个元素设置为块，然后清除浮动的影响：父元素::after{ content: ""; display: block; clear: both;} 使用这个方法，例子如下：
       
        <style>
            .box1{
                /*父级标签没有高度，高度随着子元素的高度而改变*/
                width: 300px;
                border: 5px solid red;
            
            }
            .box2{
                float: left;
                width: 100px;
                height: 200px;
                background-color: aqua;
            
            }
            .box3{
                float: left;
                width: 100px;
                height: 100px;
                background-color: rgb(0, 255, 85);           
            }
            /* 解决高度坍塌最优办法 */
            .clearfix::after{  
                content: ""; /* 伪元素必须添加content属性，否则，这个伪元素不生效 */
                display: block; /*伪元素为行内，给他变为块标签*/
                clear: both;
                /* 补充代码，是为了解决兼容性的，在网页中看不到伪元素 */
                height: 0 ;
                visibility: hidden ;
            }

           /*.clearfix::before 这个主要解决外边距塌陷问题
           外边距塌陷：父子级标签，都是块级，子级加margin会影响父级的位置 所以display就没有转为块 而是转为表单*/
            /*解决高度坍塌第二个方法 */
            .clearfix::before, /* 并集标签不要忘了逗号 */
            .clearfix::after {
                content:'';
                display:table;
            }
            .clearfix::after{
                /* 真正清除浮动的标签 */
                clear:both;
            }

            /* 解决高度坍塌 
            直接给父元素设置 overflow: hidden;*/
            .box1{
                overflow: hidden;
            }

        </style>
    </head>
    <body>
        <div class="box1 clearfix">
            <div class="box2"></div>
            <div class="box3"></div>
        </div>
    </body>

![解决高度坍塌的问题](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE2/%E8%A7%A3%E5%86%B3%E9%AB%98%E5%BA%A6%E5%9D%8D%E5%A1%8C.jpg)