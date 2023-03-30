# 所有的选择其都是找标签
## CSS 层叠样式表
选择器：
    
    标签选择器  p{} div{} body{}
    类选择器  class创建的类名 .类名{}
    id选择器  id创建的名字 #id名{}
    通配符选择器  *号{}
***
## 字体和文本样式
***
1.1 字体大小
> 属性名  font-size
值  数字+px(像素)
谷歌默认16px  单位需要设置 否则无效
***
1.2 字体粗细
> 属性名  font-weight
第一种 值   正常 normal  加粗 bold
第二种 值：直接取数字 正常400  加粗700
***
1.3 字体样式 倾斜
> 属性名 font-style
值  默认 normal  倾斜 italic
***
1.5 字体系列   无衬线字体(sans-serif)
属性名  font-family  字体选择有则用之 无则顺序下延
![字体系列](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E5%AD%97%E4%BD%93%E7%B3%BB%E5%88%97.jpg)
***
1.6 样式层叠问题
> 如果给同一个标签设置相同的样式属性，样式会发生层叠（覆盖），写在最下面的会生效
层叠样式表示可以一层一层的层叠覆盖
***
1.7 字体font相关属性的连写
> 属性名  font
取值 font:style weight size family;
取值 font:倾斜  粗细  大小 字体;
如果连写，只能忽略前两个会变为默认 
如果要同时设置**单独和连写**形式
单独样式写在连写下面 或 单独样式写在连写里面
***
#### 文本样式
>**文本样式**
>>文本缩进  text-indent
>>文本水平对齐方式  text-align
>>文本修饰  text-decoration
***
2.1 文本缩进
+ 属性名  text-indent
+ 值   数字+px
+ 数字+em (推荐使用：1em = 当前标签的font-size的大小)
***
2.2 文本水平对齐方式
+ 属性名： text-align
+ 值： left左 center居中 right右
***
> #### text-align:center; 能让哪些元素水平居中?
>> #### 1.文本 2.span标签 3.a标签 4.input标签 5.img标签
**如果需要让元素水平居中对齐，需要给以上元素的父元素设置：text-align: center ;**
***
2.3 文本修饰
+ 属性名： text-decoration
> + 值 ： underline 带下划线
> + line-through 删除线（不常用）
> + overline  上划线（几乎不用）
> + none 无装饰线 **开发中常用来清除a标签的下划线**
***
#### 行高  可以设置a标签在导航栏居中对齐
> 控制一行的上下间距
> 属性名： line-height
>取值：数字+px--或--倍数(当前文字的倍数，直接写数字) 
>应用：
> + 让**单行文本**垂直水平居中，可以为当前元素的**父元素**设置 line-height：值为当前元素的**父元素的高度** ；
>+ 如果同时设置了行高和font连写，注意覆盖问题
>font: style weight **size/line-height（40px/1.5）** family ;
***
## 扩展知识 标签水平居中方法总结：margin: 0 auto;

> **如果需要让 div p h(大盒子) 水平居中**
> + **可以通过 margin: 0 auto; 实现**
>**如果需要让 div p h(大盒子) 水平居中，直接给 # 当前元素本身#  直接设置即可**
>**margin: 0 auto;一般针对固定宽度的盒子，如果大盒子没有设置宽度，此时会默认占满父元素的宽度**
***

#### 选择器就是找标签的
1.1 后代选择器
> + 选择器1+空格+选择器2 {CSS代码}
在选择器1中找到满足后代选择器2的标签来设置样式
>后代选择器包括 儿 孙 重孙。。。选择器与选择器使用空格隔开

1.2子代选择器
> + 选择器1>选择器2{CSS代码}  子代选择器只能包括儿子那一代
***
### 选择器进阶
1.1  并集选择器

> + 可以同时选择多组标签 ，设置相同的样式 
    语法结构：选择器1,选择器2，选择器3。。。{css代码}
    结果:同时设置设置选择器1,2,3的样式

    1.2 交集选择器--紧挨着
>选择页面中 同时满足多个选择器的标签
选择器语法：选择器1选择器2{css代码} 1和2 紧挨着
既能被1选中又能被2选中,如果选择器中有标签选择器，标签选择器必须写在最前面
```
    <style>
      a.aaa{  /* 选择了a标签里面的aaa类名 */
        color: red; 
      }
      div.box1{ /* 选择了div标签里面的box1类名 */
        color:blue;
      }
    </style>
</head>
<body>
    <div class="box1"> 
        我是谁      
        <a href="#" class="aaa">你是谁</a>
    </div>
</body>
```
***
### 1.3 hover 伪类选择器
> ##### 选中鼠标悬停在元素上的状态，设置样式
>使用方法： 选择器:hover{css代码}
>注意点：伪类选择器选中的是这个元素上鼠标悬停时候的状态,任何一个标签都可以添加伪类
***
### 背景图片
background-image: url();

> + 背景平铺
属性名： background-repeat
值： repeat 水平和垂直方向都平铺
no-repeat  不平铺
repeat-x   水平方向平铺
repeat-y   垂直方向平铺

> + 背景位置
属性名： background-position();
水平垂直居中写法：background-position(center center);
![属性值](./CSS%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%9B%BE/%E8%83%8C%E6%99%AF%E5%9B%BE%E4%BD%8D%E7%BD%AE.jpg)
数字写法支持 负数！正数向右向下移动 负数向左向上移动
背景色和背景图只显示在盒子里面

### 背景相关属性的连写形式
+ 属性名： background()
+ 值：单个属性值得合写，取值之间以空格隔开
+ 书写顺序 ：background(color image repeat position);
``` background: pink url(相对路径) no-repeat center bottom; ```
+ 如果盒子大小和背景图大小一致，可以直接添加图片就行

## img标签和背景图片的区别
> + 直接写img标签，不设置宽高默认会以原尺寸显示
> + div标签+背景图片 需要设置div的宽高，背景图片只是装饰的CSS样式，不能撑开div标签
****
### 元素显示模式 display转换元素显示模式
1.1 块级元素
+ div p h ul li dl dt dd form header.....
+ 独占一行（一行只能显示一个）
+ 宽度默认是父级元素的宽度，高度默认由内容撑开
+ 可以设置宽高

1.2 行内元素
+ a span b u i s strong ins em del......
+ 一行可以显示多个
+ 宽度和高度默认由内容撑开
+ 不可可以设置宽高

1.3 行内块元素
+ input textarea button select.....
+ 一行可以显示多个 并且 可以设置宽高

### html嵌套规范注意点
+ 块级元素一般作为大容器，可以嵌套文本，块级元素，行内元素，行内块元素等等
但是：p标签中不要嵌套div p h 等块级元素
+ a标签内部可以嵌套任意元素
 但是A标签不能嵌套a标签
***

### CSS 的特性
1.1 继承性的介绍
+ 特性：子元素有默认继承父元素样式的特点
+  可以继承的常见属性（文字控制属性都可以继承，除了控制文字其他都不能继承）
+ 可以通过调试工具判断样式是否可以继承
+ 如果元素有自己的特性，就用自己的 不会去继承 主要针对a标签

1.2 层叠性的介绍
+ 给同一个标签设置不同的样式，样式会层层叠加，写在最后的样式会生效
+ 当样式冲突时，当选择器优先级相同时，才能通过层叠判断结果
***
# 案例1
```
    <style>
        .nova{
            background-color: red;
            text-decoration: none;
            color: aliceblue;
            display: inline-block;
            width: 100px;
            height: 50px;
            text-align: center;
            line-height: 50px;
        }
        .nova:hover{
            background-color: sandybrown;
        }
    </style>
    <div >
        <a href="#" class="nova">导航1</a>
        <a href="#" class="nova">导航2</a>
        <a href="#" class="nova">导航3</a>
        <a href="#" class="nova">导航4</a>
        <a href="#" class="nova">导航5</a>
    </div>
    


     <style>
        a{
            text-decoration: none;
            display: inline-block;
            width: 89px;
            height: 51px;
            text-align: center;
            line-height: 40px;
            color: rgb(211, 216, 219);
        }
        .nova1{
            background-image: url(./CSS基础知识图/122333444.png);
        }
        .nova2{
            background-image: url(./CSS基础知识图/2.png);
        }
        .nova1:hover{
           background-image: url(./CSS基础知识图/2.png);
        }
        .nova2:hover{
           background-image: url(./CSS基础知识图/122333444.png);
        }
    </style>


    <a href="#" class="nova1">导航1</a>
    <a href="#" class="nova2">导航2</a>
