##### SASS 与 SCSS

```scss
###SASS格式
.main
	color:blue
	font-size:0.3em
###SCSS格式
.main{
    color:blue;
    font-szie:0.3em;
}
#
```

##### 配置

```scss
1.设置编码格式 ：    @charset "utf-8"
```

##### 定义变量

```scss
#定义变量，以$开头，接上名字
$name:20px;
#将局部变量变成全局变量,使用 !global
.main {
  $width: 5em !global;
  width: $width;
}
```

##### 数据类型

```
1.数字：  1, 2, 13, 10px
2.字符串，有引号字符串与无引号字符串   ："foo", 'bar', baz
3.颜色： blue, #04a3f9, rgba(255,0,0,0.5)
4.布尔型： true, false
5.空值： null
6.数组，用空格或逗号作分隔符： 1.5em 1em 0 --------2em, Helvetica, Arial, sans-serif

#案例，使用字符串变量
@mixin firefox-message($selector) {
  body.firefox #{$selector}:before {
    content: "Hi, Firefox users!";
  }
}
@include firefox-message(".header");
```

##### 运算

```
支持的运算：
	1.  ==  ， !=
	2.+, -, *, /,%         (不同单位间自动转化)
	
```

##### 插值语句

```
通过 #{} 插值语句可以在选择器或属性名中使用变量
```



##### 嵌套

```scss
.container{
    padding-left:20px;
    .row{
        padding-top:10px;
        div{
            /*&:父选择器,连接器*/
            &:hover{
                color:red;
            }
        }
    }
}
```

##### 属性嵌套

```
div{
    font:{
        family:"微软也黑";
        size:20px;
    }
}
```

##### 注释

```scsss
/*这种注释会编译到.css文件中*/
//这种注释不会编译到.css文件中

//插值语句 (interpolation) 也可写进多行注释中输出变量值
$version:"1.2.3";
/* 我是插值语句 #{$version}*/
```

##### 文件名

```
//被导入的文件，都是以_开头命名的文件,这种文件不会被编译
//  _common.scss
```

##### 导入

```
//导入上述    _common.scss文件
@import "common";
```

##### mixin

```
@mixin font($family,$size){
    font-family: $family;
    font-size: $size;
}

a{
    //bu neng you zhong wen,yong unicode bian ma
    @include font("\5FAE",30px);
}
```

##### 扩展

```
//此时test23也有test的样式  ，通过  @extend 继承了.test的样式
.test{
    font-size: 10px;
    color: red;
    background-color: #fff;
}

.test23{
    @extend .test;
    color: black;
}
//设置默认值
@mixin sexy-border($color, $width: 1px) {}
//关键词参数
p { @include sexy-border($color: blue); }
//不明确参数的具体个数，可以如下定义
@mixin box-shadow($shadows...) {}
```

##### 指令

```
#@for循环,范围 [start，end]
格式：@for $var from <start> through <end>
案例：	@for $i from 1 through 3 {
  		.item-#{$i} { width: 2em * $i; }
	   }
	   
#@each 遍历数组
格式 ： @each $var in <list>
例子1： @each $animal in puma, sea-slug, egret, salamander {
        .#{$animal}-icon {
          background-image: url('/images/#{$animal}.png');
        }
      }
例子2:  @each $animal, $color, $cursor in (puma, black, default),
                                           (sea-slug, blue, pointer),
                                           (egret, white, move) {
           .#{$animal}-icon {
             background-image: url('/images/#{$animal}.png');
             border: 2px solid $color;
             cursor: $cursor;
           }
         }         
```

##### 函数

```
/*
 * 这是一个将单位px转成rem的函数
 */

$num:100;//一个屏幕分成rem的份数
$designWidth:650;//设计稿的宽度(px)
@function px2rem($px){
    @return $px / $designWidth * $num *1rem;
}

a{
    width: px2rem(650);
}

```

