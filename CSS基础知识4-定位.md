# css 就是找到这个标签，改变它的样式

整理一个项目的根目录：网站的第一级文件夹（这个文件放当前这个项目的所有的素材，比如：图片，html,css..）网站的根目录就是网站的第一级文件夹，这文件夹一般网站叫什么名字，她就叫什么名字
> + 包含内容：图片文件夹：images，样式文件夹:css，首页：index.html

#### 网页的常见布局方式
> 1. 标准流
>> + 块级元素独占一行-->垂直布局
>> + 行内元素/行内块元素 一行显示多个--> 水平布局
> 2. 浮动布局
>> + 可以让原本垂直布局的块级元素变成水平布局
> 3. 定位布局
>> + 可以让元素自由的摆放在网页的任意位置
>> + 一般用于盒子之间的层叠情况

## 使用定位布局的步骤 
+ + css书写步骤：首先确定定位模式（position:;），浮动方向(上下左右)，显示属性（display），设置盒子模型大小背景色，最后设置文字属性
![CSS书写顺序](./CSS%E7%9F%A5%E8%AF%86%E5%9B%BE4/CSS%E4%B9%A6%E5%86%99%E9%A1%BA%E5%BA%8F.png)


> 1. 设置定位的方式
>> + 属性名：position
>> + 常见属性值：

|定位方式|属性值|
|:---:|:---:|
|静态定位|static|
|相对定位|relative|
|绝对定位|absolute|
|固定定位|fixed|
> 2. 设置偏移值
>> + 偏移值设置分为两个方向，水平和垂直方向各选一个使用即可
>> + 选取的原则一般是就近原则（离哪个近用哪个）

|方向|属性名|属性值|含义|
|:---:|:---:|:---:|:---:|
|水平|left|数字+px|距离左边的距离|
|水平|right|数字+px|距离右边的距离|
|垂直|top|数字+px|距离上边的距离|
|垂直|bottom|数字+px|距离下边的距离|

### 相对定位  以左上角为基点 进行移动
> + 代码：position:relative;
> + 1. 需要配合方向属性实现自身移动
> + 2. 相对于自己原来的位置进行移动
> + 3. 在页面中占位置———>没有脱标
> + 4. 配合绝对定位组CP（子绝父相）父元素设置相对定位，子元素设置绝对定位，来实现子元素位置的绝对移动

![相对定位](./CSS%E7%9F%A5%E8%AF%86%E5%9B%BE4/%E7%9B%B8%E5%AF%B9%E5%AE%9A%E4%BD%8D.png)

### 绝对定位
+ + 先找已经定位的父级元素，如果有这样的父级元素，就以这个父级作为参照物进行位置移动，如果父级没有定位属性，则以浏览器窗口为参照物进行位置移动
+ + 一般情况下，父元素设置相对定位，子元素设置绝对定位，子元素在父元素的范围内移动，在选择父级元素的时候，这个父元素可以是父，爷，甚至祖父级别的，那个设置相对定位 就在哪个里面移动
+ + 绝对定位查找父级的方式：就近查找定位的父元素，如果逐层查找不到这样的父级元素，就以浏览器窗口参照进行位置一定
+ +  绝对定位的盒子不能使用左右margin auto居中
+ +  
        <style>
            .box{
                /* 绝对定位的盒子不能使用左右margin auto 进行居中 */
                position: absolute;
                /* margin: 0 auto; */
                /* 实际移动位置是以盒子做边框为基准的50% 浏览器中间偏右的位置*/

                /* 实现绝对定位的盒子水平垂直居中 */
                left: 50%;
                /* 把盒子向左侧偏移自己宽度的一半*/
                margin-left: -150px;
                top: 50%;
                /*把盒子向上偏移自己高度的一半 */
                margin-top: -150px;
                
                /* 位移：自身宽度和高度的一半  */
                transform: translate(-50%,-50%);
                width: 300px;
                height: 300px;
                background-color: pink;
            }
        </style>
            
        <body>
            <div class="box"></div>
        </body>

## /* 位移：自身宽度和高度的一半  */
            transform: translate(-50%,-50%);

        <style>
        /* 因为有通栏:占满一行的原因,所以需要有一个沾满一行的格子 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        .nav {
            height: 40px;
            border-top: 1px solid #ccc;
            border-bottom: 1px solid #ccc;
        }

        ul {
            list-style: none;
            width: 1200px;
            margin: 0 auto;
        }

        ul li {
            float: left;
            width: 20%;
            height: 40px;
            border-right: 1px solid #ccc;
            text-align: center;
            line-height: 40px;
        }

        ul .last {
            border-right: none;
        }

        ul li a {
            /* a标签默认是行内元素，宽高由内容撑开，并且无法设置宽高，此时默认情况用户只能点击文字区域才能调整 */
            /* 如果把a标签转换成块级元素或者行内块元素，此时可以设置宽高，会让a标签范围更大，用户可以点击调整的区域也越大 */
            /* display: inline-block; */
            /* 如果设置行内块元素，padding生效 高度和宽度不生效 */
            display: block;
            /* 如果设置块元素，设置高生效，占满格子 块元素设置宽高生效 */
            /* 宽度不设置块元素会默认占满一行 */
            height: 40px;
            /* 设置padding 不会让元素占满 可以预留一点位置 */
            /* padding: 0 60px; */
            text-decoration: none;
            color: black;
        }
        .nav ul li .app{
            position: relative;
        }
        .nav ul li .app .ma{
            position: absolute;
            left: 50%;
            top: 50px;
            /* 水平居中translate写一个值就行 */
            transform: translate(-50%);
        }
    </style>
    </head>

    <body>
    <div class="nav">
        <ul>
            <li><a href="#">我要投aaa资</a></li>
            <li><a href="#">平台ggggg介绍</a></li>
            <li><a href="#">新手专区</a></li>
            <!-- 因为用户鼠标放在二维码图片上也能跳转，所以把img放在a的范围内，因此要把img写在a的内部 -->
            <li><a href="#" class="app">手机微金所 <img  class="ma" src="./CSS知识图4/二维码百度.png" alt=""></a></li>
            <li class="last"><a href="#">个人中心</a></li>
        </ul>
    </div>
    </body>

![导航居中](./CSS%E7%9F%A5%E8%AF%86%E5%9B%BE4/%E5%AF%BC%E8%88%AA%E5%B1%85%E4%B8%AD.png)

## 绝对定位小实例
    <style>
        .nav{
            position: relative;
            width: 1200px;
            height: 600px;
            background-color: pink;
            margin:0 auto;            
        }
        .span{
            position: absolute;
            display: block;
            /* 绝对定位的盒子显示模式具备行内块的特点：设置宽高生效，如果没有宽度，也没有内容，盒子的宽高尺寸就是 0  */
            width: 1200px;
            height: 150px;
            background-color:rgba(0, 0, 0, 0.2);
            /* 阴影效果 */
            /* box-shadow: -2px -2px 5px 5px #ccc; */
            bottom: 0;
            text-align: center;
            line-height: 150px;
        }
    </style>
    </head>

    <body>
    <div class="nav">
        <span class="span">啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊</span>
    </div>
    </body>

![绝对定位小实例](./CSS%E7%9F%A5%E8%AF%86%E5%9B%BE4/%E7%BB%9D%E5%AF%B9%E5%AE%9A%E4%BD%8D%E5%B0%8F%E5%AE%9E%E4%BE%8B.png)

## 固定定位
        <style>
        div{
            position: fixed;
            left: 0;
            top: 0;
          
            /* 固定定位：
                1. 脱标——不占位置
                2.改变位置是参开浏览器的窗口
                3.具备行内块特点（需要设置宽高）
                4.哪个元素需要固定定位就给谁设置position: fixed;
             */

            width: 200px;
            height: 200px;
            background-color: pink;
        }
        p{
            width: 200px;
        }
    </style>
    </head>

    <body>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <div></div>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>

    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p><p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>
    <p>PPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP</p>  
    </body>

# 元素层级为题
> + + 不同布局方式元素的层级关系
 > + + + 标准流（最底下） < 浮动 < 定位（在最上面）
> 不同定位之间的层级关系
> + 相对，绝对，固定默认层级相同
> + 此时HTML中写在最下面的元素层级更高，会覆盖上面的元素

        <style>
        div {
            width: 200px;
            height: 200px;
        }

        .two {
            position: absolute;
            top: 100px;
            left: 50px;
            background-color: orange;
            /* z-index: 1; */
        }

        .one {
            position: absolute;
            top: 50px;
            left: 20px;
            background-color: pink;
            z-index: -1;
        }

        /* 默认情况下，定位的盒子，哪个元素在后面，哪个元素的层级就高 */
        /* z-index: -1; 取整数值越大，层级越高，显示越靠前，可以设置负值 默认值是0  如果都取默认，后来者居上 ，z-index必须配合定位才能生效*/
    </style>
    </head>

    <body>
    <div class="two">two"</div>
    <div class="one">one"</div>
    </body>


