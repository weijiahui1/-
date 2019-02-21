### 1.display: none;  与  visibility: hidden; 的区别
    联系：它们都能让元素不可见
    区别：
      1)display:none;会让元素完全从渲染树中消失，渲染的时候不占据任何空间；   
        visibility: hidden;不会让元素从渲染树消失，渲染的元素继续占据空间，只是内容不可见
      2)display: none;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示；
        visibility: hidden;是继承属性，子孙节点消失由于继承了hidden，通过设置visibility: visible;可以让子孙节点显式。
      3)修改常规流中元素的display通常会造成文档重排（回流+重绘）；
        修改visibility属性只会造成本元素的重绘。
      4)读屏器不会读取display: none;元素内容；
        读屏器会读取visibility: hidden;元素内容。
  
### 2.CSS里的 visibility 属性有个collapse属性值是干嘛用的？在不同浏览器下以后什么区别？
    对于普通元素visibility:collapse;会将元素完全隐藏,不占据页面布局空间,与display:none;表现相同. 
    如果目标元素为table,visibility:collapse;将table隐藏,但是会占据页面布局空间. 
    仅在Firefox下起作用,IE会显示元素,Chrome会将元素隐藏,但是占据空间.  

### 3.css sprite是什么,有什么优缺点？
    百度链接：https://baike.baidu.com/item/css%20sprite/1139316?fr=aladdin
    1)概念：CSSSprites在国内很多人叫css精灵，是一种网页图片应用处理方式。它允许你将一个页面涉及到的所有零星图片都包含到一张大图中去，这样一来，当访问该页面时，载入的图片就不会像以前那样一幅一幅地慢慢显示出来了。对于当前网络流行的速度而言，不高于200KB的单张图片的所需载入时间基本是差不多的，所以无需顾忌这个问题。
    2)原理：CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background- repeat”，“background-position”的组合进行背景定位，background-position可以用数字精确的定位出背景图片的位置。
    3)优点：
    利用CSS Sprites能很好地减少网页的http请求，从而大大的提高页面的性能，这也是CSS Sprites最大的优点，也是其被广泛传播和应用的主要原因；
    CSS Sprites能减少图片的字节，曾经比较过多次3张图片合并成1张图片的字节总是小于这3张图片的字节总和。
    解决了网页设计师在图片命名上的困扰，只需对一张集合的图片上命名就可以了，不需要对每一个小元素进行命名，从而提高了网页的制作效率。
    更换风格方便，只需要在一张或少张图片上修改图片的颜色或样式，整个网页的风格就可以改变。维护起来更加方便。
    4)缺点：
    图片合并麻烦；
    维护麻烦，修改一个图片可能需要从新布局整个图片，样式。
    
 ### 4.link与@import的区别
    1）link属于html标签，而@import是css提供的。
    2）页面被加载时，link会同时被加载，而@import引用的css会等到页面加载结束后加载。
    3）link是html标签，因此没有兼容性，而@import只有IE5以上才能识别。
    4）link方式样式的权重高于@import的。
 ### 5.css3有哪些新特性
    1）新增各种css选择器
    2）圆角  border-radius
    3）多列布局  http://www.w3school.com.cn/css3/css3_multiple_columns.asp                    
    4）阴影和反射 box-shadow  
    5）文字特效   text-shadow  http://www.w3school.com.cn/cssref/pr_text-shadow.asp
    6）线性渐变   Gradients   http://www.runoob.com/css3/css3-gradients.html
    7）多背景（ background-image:url(bg_flower.gif),url(bg_flower_2.gif);  ）
    8）CSS3动画：
                 链接：http://www.w3school.com.cn/cssref/pr_transform.asp
    依靠CSS3中提出的三个属性：transition、transform、animation
    1.  transition：定义了元素在变化过程中是怎么样的，包含
        transition: property duration timing-function delay;
    
    2.  transform：定义元素的变化结果，包含rotate、scale、skew、translate。
        transform: none|transform-functions;
        2D/3D 
        translate() 平移  根据给定的 left（x 坐标） 和 top（y 坐标） 位置参数。 
        rotate() 旋转  元素顺时针旋转给定的角度。允许负值，元素将逆时针旋转。 
        scale() 缩放  元素的尺寸会增加或减少，根据给定的宽度（X 轴）和高度（Y 轴）参数。 skew() 翻转(拉伸)  元素翻转给定的角度，根据给定的水平线（X 轴）和垂直线（Y 轴）参数。
    
    2.  animation：动画定义了动作的每一帧（@keyframes）有什么效果
    语法
        animation: name duration timing-function delay iteration-count direction;
        
    9)CSS3新增伪类有那些？
        p:first-of-type 选择属于其父元素的首个<p>元素的每个<p> 元素。
        p:last-of-type 选择属于其父元素的最后 <p> 元素的每个<p> 元素。
        p:only-of-type 选择属于其父元素唯一的 <p>元素的每个 <p> 元素。
        p:only-child 选择属于其父元素的唯一子元素的每个 <p> 元素。
        p:nth-child(2) 选择属于其父元素的第二个子元素的每个 <p> 元素。
        :after 在元素之前添加内容,也可以用来做清除浮动。
        :before 在元素之后添加内容
        :enabled
        :disabled 控制表单控件的禁用状态。
        :checked 单选框或复选框被选中
    
    
