
#1、React Native 环境搭建
React Native 的宗旨是，学习一次，高效编写跨平台原生应用。

在Windows下搭建React Native Android开发环境

1.安装jdk

2.安装sdk
 
在被墙的环境下，为了速度我选择了使用http://androiddevtools.cn/

3.安装C++环境

择Windows SDK、cygwin或mingw等其他C++环境。编译node.js的C++模块时需要用到。

4.安装Node.js与Git

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。Node.js 的包管理器 npm，是全球最大的开源库生态系统

 [点击下载msysgit](https://git-for-windows.github.io/)

建议设置npm镜像以加速后面的过程（或使用科学上网工具）。

设置全局使用指定的镜像

npm config set registry https://registry.npm.taobao.org

npm config set disturl https://npm.taobao.org/dist

5.安装React Native命令行工具

github下载

npm install -g react-native-cli

6.创建项目

react-native init Sanji

7.运行packager  进入工程目录

react-native start

可以用浏览器访问http://localhost:8081/index.android.bundle?platform=android看看是否可以看到打包后的脚本

8.准备模拟器或真机 运行android

react-native run-android

问题：找不到sdk  或者 无法正常化 sdk路径  解决办法：环境变量

问题：failed to find target with hash string 'android-23' in: F:\Android_SDK    解决版本：更新23版本的sdk

问题：build成功后是红色的：没有连接服务器js Server
解决方法：ip地址+8081端口  例子：192.168.1.100:8081

9.调试app
  菜单  reload js


#2、React Native 从React到RN
###React简介
RN是基于React设计，了解React有助于我们开发RN应用；
React希望将功能分解化，让开发变得像搭积木一样，快速而且可维护

React主要有如下3个特点：

* 作为UI（Just the UI）

* 虚拟DOM（Virtual DOM）

这是亮点  是React最重要的一个特性  放进内存   最小更新的视图

差异部分更新 diff算法

* 数据流（Date Flow）单向数据流

学习React需要掌握哪些知识？

* JSX语法   类似XML

* ES6相关知识

* 前端基础  CSS+DIV  JS

举例说明React的用法，IDE工具：WebStorm(JavaScript 开发工具 Web前端开发神器  插件很丰富)

比如：ReactNative 代码智能提醒（webstorm）

`git clone https://github.com/virtoolswebplayer/ReactNative-LiveTemplate`

下载模板：https://github.com/wix/react-templates安装命令
`npm install react-templates -g`

[点击下载WebStorm](https://www.jetbrains.com/webstorm/download/)


[点击下载WebStorm破解版](http://www.cr173.com/soft/130969.html)

1.（简单组件和数据传递）
使用this.props 指向自己的属性

从http://facebook.github.io/react/downloads.html下载react Kit

react.js react-dom.js：React的核心文件

JSXTransformer.js browser.min.js：讲JSX转译成js和html的工具

最新的react版本：react-v15.6.1

>在react 0.14前，浏览器端实现对jsx的编译依赖jsxtransformer.js 
>
>在react 0.14后，这个依赖的库改为browser.js，页面script标签的type也由text/jsx改为text/babel
但是以上只能用来测试学习react
生产环境需要借助编译工具事先将jsx编译成js 

例如可以使用Node.js做预编译，可以安装react-tools工具
npm install -g react-tools


###React Native简介与代码分析

###为什么要使用React Native
如何在开发成本和用户体验做到更好的平衡？
很多时候，前端都有一种乐观的想法：H5可以替代原生应用
RN不仅可以使用前端开发的模式来开发应用，还能调用原生应用的UI组件和API



#3、React Native flexbox布局(RN基础)

>1.弹性盒模型（The Flexible Box Module）,又叫Flexbox，意为“弹性布局”，旨在通过弹性的方式来对齐和分布容器中内容的空间，使其能适应不同屏幕，为盒装模型提供最大的灵活性。


>Flex布局主要思想是：让容器有能力让其子项目能够改变其宽度、高度（甚至是顺序），以最佳方式填充可用空间；

>flexbox布局是伸缩容器(container)和伸缩项目(item)组成

>Flexbox布局的主体思想是元素可以改变大小以适应可用空间，当可用空间变大，Flex元素将伸展大小以填充可用空间，当Flex元素超出可用空间时将自动缩小。总之，Flex元素是可以让你的布局根据浏览器的大小变化进行自动伸缩。


===================
>###2.容器有主轴和交叉轴组成！ 主轴既可以是水平轴，也可以是垂直轴
>###容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。
>
>
>###项目默认沿主轴排列，单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

![flexBox](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112443816-1567167496.jpg)


###根据伸缩项目排列方式的不同，主轴和侧轴方向也有所变化
![flexBox](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112508660-1085716225.png)
###伸缩容器的属性

###3.在React中，Flexbox有6种容器属性，6种项目属性。而在React Native中，有4个容器属性，2个项目属性，分别是：

>###容器属性：
>####flexDirection 、 flexWrap 、  justifyContent 、 alignItems
>
>###项目属性：
>####flex 、 alignSelf


###3.1: flexDirection容器属性: `row | row-reverse | column | column-reverse`

>该属性决定主轴的方向（即项目的排列方向）。

>row：主轴为水平方向，起点在左端。

>row-reverse：主轴为水平方向，起点在右端。

>column(默认值)：主轴为垂直方向，起点在上沿。

>column-reverse：主轴为垂直方向，起点在下沿。

![flexDirection](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112540957-1647471085.jpg)

###3.2:flexWrap容器属性: 
###`nowrap | wrap | wrap-reverse`
>默认情况下，项目都排在一条线（又称"轴线"）上。
>flex-wrap属性定义，如果一条轴线排不下，如何换行。

![flexWrap](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112606254-1463006992.jpg)

####3.2.1 nowrap(默认值)：不换行
![nowrap](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112625676-1828317029.png)

####3.2.2 wrap：换行，第一行在上方
![wrap](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112645566-1751782976.jpg)

####3.2.3 wrap-reverse：换行，第一行在下方。（和wrap相反）
![wrap-reverse](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112704332-1522922474.png)

###3.3 justifyContent容器属性:
###`flex-start | flex-end | center | space-between | space-around`
>定义了伸缩项目在主轴线的对齐方式

>flex-start(默认值)：伸缩项目向一行的起始位置靠齐。

>flex-end：伸缩项目向一行的结束位置靠齐。

>center：伸缩项目向一行的中间位置靠齐。

>space-between：两端对齐，项目之间的间隔都相等。

>space-around：伸缩项目会平均地分布在行里，两端保留一半的空间。

![justifyContent](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112733144-838889631.png)

###3.4:alignItems容器属性:
###`flex-start | flex-end | center | baseline | stretch`
>定义项目在交叉轴上如何对齐，可以把其想像成侧轴（垂直于主轴）的“对齐方式”。

>flex-start：交叉轴的起点对齐。

>flex-end：交叉轴的终点对齐 。

>center：交叉轴的中点对齐。

>baseline：项目的第一行文字的基线对齐。

>stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

![alignItems](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112814598-846413905.png)

###3.5:flex项目属性:
###`flex-grow`、`flex-shrink`和`flex-basis`三个属性的缩写， 其中第二个和第三个参数（flex-shrink、flex-basis）是可选参数。默认值为`0 1 auto`。

####`宽度 ＝ 弹性宽度 * ( flexGrow / sum( flexGorw ) )`

![flex](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112838426-2099705286.png)

###3.6alignSelf项目属性
###`auto | flex-start | flex-end | center | baseline | stretch`
>align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。

>默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

![alignSelf](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905112905457-955838599.png)

#4、React Native 布局
### 1：获取当前屏幕的宽度、高度、分辨率
```import Dimensions from 'Dimensions';

let { width, height, scale } = Dimensions.get('window');

render() {
  return (
    <View>
      <Text>
        屏幕的宽度：{width + '\n'}
        屏幕的高度：{height + '\n'}
        屏幕的分辨率：{scale + '\n'}
      </Text>
    </View>
  );
}
```

###2：默认宽度
>###我们都知道块级标签如果不设置宽度，通常都是独占一行的，在React Native中的组件中需要设置flexDirection：'row'，才能在同一行显示，flex的元素如果不设置宽度，都会百分之百的占满父容器。
>

###3：水平、垂直居中
>#####当alignItems、justifyContent传center时与flexDirection的关系：
>![](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905161943723-1180621476.png)
>
>####想理解这个很简单，看我上班讲的alignItems、justifyContent，心里想着主轴和次轴就可以理解，justifyContent是主轴方向居中，而alignItems是次轴方向居中，flexDirection默认为column，所以误区会认为alignItems为水平居中，justifyContent为垂直居中。

###4.padding和margin
>#####margin是指从自身边框到另一个容器边框之间的距离，就是容器外距离。在CSS中padding是指自身边框到自身内部另一个容器边框之间的距离，就是容器内距离，下面这张是CSS的效果图，只是名字不一样（marginTop），原理都是一样；
>
>![](http://images2015.cnblogs.com/blog/80291/201609/80291-20160905162012426-59354887.jpg)

###5：关于样式
>（1）普通内联样式:{{}},第一层｛｝是表达式，第二层｛｝是js对象；

                  <View style={{fontSize:40, width:80,}}> </View>
>（2）调用样式表:{样式类.属性}

                  <View style={styles.container}></View>

>（3）样式表和内联样式共存:{[]}

                  <View style={[styles.container, {fontSize:40, width:80}]}>

>（4）多个样式表:{[样式类1， 样式类2]}

                  <View style={[styles.container, styles.color]}>





#5、React Native常用组件样式总结

###样式表的几种使用方法

样式的声明

```
const styles = StyleSheet.create({
  base: {
    width: 38,
    height: 38,
  },
  background: {
    backgroundColor: '#222222',
  },
  active: {
    borderWidth: 2,
    borderColor: '#00ff00',
  },
});

```
使用样式

>```
><Text style={styles.base} />
><View style={styles.background} />
>```

也可以接收一个数组

>```
><View style={[styles.base, styles.background]} />
>```

也可以根据条件来应用样式

>```
><View style={[styles.base, this.state.active && styles.active]} />
>```

假如this.state.active是true，styles.active就会被应用，如果为false，styles.active就不会被应用。

当然也是支持下面的这种写法

>```
><View
>  style={[styles.base, {
>    width: this.state.width,
>    height: this.state.width * this.state.aspectRatio
>  }]}
>/>
>
>```

下面是样式表中的具体属性

##定位
定位分为绝对定位和相对定位，属性名为position，属性值为absolute和relative。

当使用绝对布局时，定位根据屏幕来进行。

>```
>import React, { Component } from 'react';
import {
    StyleSheet,
    Text,
    View,
    Image,
} from 'react-native';
export default class test extends Component {
    render() {
        return (
            <View style={styles.container}>
                <View style={styles.box1}/>
                <View style={styles.box2}/>
                <View style={styles.box3}/>
                <View style={styles.box4}/>
            </View>
        );
    }
}
const styles = StyleSheet.create({
    container:{
        flex:1,
        backgroundColor:'#ff0'//黄色
    },
    box1:{
        width:50,
        height:50,
        backgroundColor:'#f00',//红色
        position :'absolute',
        left:30,//左边距离屏幕左侧30单位
    },
    box2:{
        width:50,
        height:50,
        backgroundColor:'#0f0',//绿色
        position :'absolute',
        top:30,//上边距离屏幕上侧30单位
    },
    box3:{
        width:50,
        height:50,
        backgroundColor:'#f0f',//紫色
        position :'absolute',
        right:30,//右边距离屏幕右侧30单位
    },
    box4:{
        width:50,
        height:50,
        backgroundColor:'#00f',//蓝色
        position :'absolute',
        bottom:30//下边距离屏幕下侧30单位
    }
});
>```

效果图如下

![](http://img.blog.csdn.net/20151124185338044)

当对应的值为负数时，方向与原方向相反，即如果top为-50，则会整个移出到屏幕外（向上移到50个单位）。

那么相对布局又是怎么样的呢

```
import React, { Component } from 'react';
import {
    StyleSheet,
    Text,
    View,
    Image,
} from 'react-native';
export default class test extends Component {
    render() {
        return (
            <View style={styles.container}>
                <View style={styles.box1}/>
            </View>
        );
    }
}
const styles = StyleSheet.create({
    container:{
        flex:1,
        backgroundColor:'#ff0'//黄色
    },
    box1:{
        width:50,
        height:50,
        backgroundColor:'#f00',//红色
        position :'relative',
        left:30,
        top:30,
    },
});
```

效果图如下

![](http://img.blog.csdn.net/20151124185405893)

可以看到设置了top和left后，相对于不使用定位的位置向右向下移动了30单位，如果值为负数，也是往相反的方向移到。

但是如果设置了right和bottom后，又会怎么样呢

```
const styles = StyleSheet.create({
  container:{
    flex:1,
    backgroundColor:'#ff0'//黄色
  },
  box1:{
    width:50,
    height:50,
    backgroundColor:'#f00',//红色
    position :'relative',
    right:30,
    bottom:30,
  },
});
```
![](http://img.blog.csdn.net/20151124185517285)

其实它的效果就是对应的top和left为负值的情况。距离原来位置的右侧30单位，距离原来位置下侧30单位，即向上向左平移30单位。原来位置就是不使用定位时的位置。如图

![](http://img.blog.csdn.net/20151124185755791)

默认情况下使用的是相对定位

##边框宽度
>```
>borderBottomWidth //底部边框宽度
>borderLeftWidth  //左边边框宽度
>borderRightWidth //右边边框宽度
>borderTopWidth //顶部边框宽度
>borderWidth  //所有边框宽度
>```
你可以使用设置所有边框的宽度，也可以设置指定某条边的宽度。

##边框颜色
>```
>borderBottomColor
>borderLeftColor
>borderRightColor
>borderTopColor
>borderColor
>```

##外边距
>```
>marginBottom
>marginLeft
>marginRight
>marginTop
>marginVertical
>marginHorizontal
>margin
>```

值得注意的是marginVertical相当于同时设置marginTop和marginBottom，marginHorizontal相当于同时设置marginLeft和marginRight，margin相当于同时设置四个

##内边距
>```
>paddingBottom  
>paddingLeft  
>paddingRight  
>paddingTop  
>paddingVertical
>paddingHorizontal  
>padding 
>```

##背景色
>```
>背景色，属性值为字符串类型的rgb表示方式
>backgroundColor
>```

##边框圆角
>```
>borderTopLeftRadius
>borderTopRightRadius
>borderBottomLeftRadius
>borderBottomRightRadius
>borderRadius
>```

##宽高
>```
>width 
>height
>```

##Flex布局相关
>```
>flex number 
>flexDirection enum('row', 'column') 
>flexWrap enum('wrap', 'nowrap') 
>alignItems enum('flex-start', 'flex-end', 'center', 'stretch') 
>alignSelf enum('auto', 'flex-start', 'flex-end', 'center', 'stretch') 
>justifyContent enum('flex-start', 'flex-end', 'center', 'space-between', 'space-around') 
>```

##字体相关属性
>```
>color 字体颜色
>fontFamily 字体族
>fontSize 字体大小
>fontStyle 字体样式，正常，倾斜等，值为enum('normal', 'italic')
>fontWeight 字体粗细，值为enum("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')
>letterSpacing 字符间隔
>lineHeight 行高
>textAlign 字体对齐方式，值为enum("auto", 'left', 'right', 'center', 'justify')
>textDecorationLine 貌似没效果，字体修饰，上划线，下划线，删除线，无修饰，值为enum("none", 'underline', 'line-through', 'underline line-through')
>textDecorationStyle enum("solid", 'double', 'dotted', 'dashed') 貌似没效果，修饰的线的类型
>textDecorationColor 貌似没效果，修饰的线的颜色
>writingDirection enum("auto", 'ltr', 'rtl') 不知道什么属性，写作方向？从左到右？从右到左？
>```

##图片相关属性
>```
>resizeMode enum('cover', 'contain', 'stretch')
>overflow enum('visible', 'hidden') 超出部分是否显示，hidden为隐藏
>tintColor 着色，rgb字符串类型
>opacity 透明度
>```

其中resizeMode 中的三个属性，contain是指无论如何图片都包含在指定区域内，假设设置的宽度高度比图片大，则图片居中显示，否则，图片等比缩小显示

```
import React, { Component } from 'react';
import {
    StyleSheet,
    Text,
    View,
    Image,
} from 'react-native';
export default class test extends Component {
    render() {
        return (
            <View style={styles.container}>
                <Image source={{uri:'https://ss0.bdstatic.com/5aV1bjqh_Q23odCf/static/superman/img/logo/bd_logo1_31bdc765.png'}} style={styles.img}></Image>
            </View>
        );
    }
}
const styles = StyleSheet.create({
    container:{
        backgroundColor:'#ff0'//黄色
    },
    img:{
        flex:1,
        height:150,
        resizeMode:"contain"
    },

});
```

效果图如下图显示

![](http://img.blog.csdn.net/20151124185610157)

将高度改成50，则进行缩小

![](http://img.blog.csdn.net/20151124185626463)


cover是指按实际大小进行显示，超出部分进行裁剪，将属性值改成cover之后的效果图如下

![](http://img.blog.csdn.net/20151124185644319)

stretch是指将图像进行拉伸显示，将属性值改为stretch后的效果如下图所示

![](http://img.blog.csdn.net/20151124185701815)

##图像变换
>```
>scaleX:水平方向缩放
>scaleY:垂直方向缩放
>rotation:旋转
>translateX:水平方向平移
>translateY:水平方向平移
>```

##阴影
>```
>shadowColor
>shadowOffset
>shadowOpacity
>shadowRadius
>```

#6、React Native JSX入门

React是由ReactJS与React Native组成，其中ReactJS是Facebook开源的一个前端框架，React Native是ReactJS思想在native上的体现！

JSX并不是一门新的语言，仅仅是个语法糖，允许开发者在JavaScript中书写HTML语法。，最后每个HTML标签都转化为JavaScript代码来运行

1.环境

2.载入方式

3.标签  HTML标签 与  ReactJS创建的组件类标签(首字母一定要大写)

4.转换 解析器

  `<h3>输入</h3>`  转换成：

React.createElement("h3",null,"输入") 返回一个ReactElement对象

5.执行JavaScript表达式

var msg="Test";

`<h1>{msg}</h1>`

React.createElement("h1",null,msg)

6.注释
   单行：//
   多行：/*注释文本*/

7.属性

  `var msg=<h1 width="10px">Test</h1>`

  React.createElement("h1",{width:"10px"},"Test")

8.延展属性
 
 使用ES6的语法

 var props={};
 props.foo="1";
 props.bar="1";

 `<h1 {...props} foo="2" >hit me</h1>` 转换成：

React.createElement("h1",React.__spread({},props,{foo:"2"}),"hit me")

9.自定义属性(HTML5给出了方案，凡是以data-开头的自定义属性，可渲染到页面)

10.显示HTML 显示一段HMTL字符串，而不是html节点

借助一个属性 _html

`<div>{{_html:'<h1>hit me</h1>'}}</div>`

11.样式的使用

style属性   js对象  外层{}按照JSX语法  内层{}是JavaScript对象

12.事件绑定

 注意：onClick  调用bind方法（设定作用域，要传递的参数）




#7、React Native ReactJS

ReactJS核心思想：组件化  维护自己的状态和UI  自动重新渲染  

多个组件组成了一个ReactJS应用

React是全局对象   顶层API与组件API

React.createClass创建组件类的方法

React.render渲染，将指定组件渲染到指定DOM节点

render:组件级API,返回组件的内部结构


React.render被ReactDOM.render替代


#8、React Native ReactJS组件生命周期
1.创建阶段
该阶段主要发生在创建组件类的时候，在这个阶段中会初始化组件的属性类型和默认属性。

getDefaultProps：处理props的默认值 在React.createClass调用

在ES6里，可以统一使用static成员来实现.

```
//ES6
static defaultProps = {
        autoPlay: false,
        maxLoops: 10,
};  // 注意这里有分号
static propTypes = {
        autoPlay: React.PropTypes.bool.isRequired,
        maxLoops: React.PropTypes.number.isRequired,
        posterFrameSrc: React.PropTypes.string.isRequired,
        videoSrc: React.PropTypes.string.isRequired,
};  // 注意这里有分号
```


2.实例化阶段

##该阶段主要发生在组件类被调用(实例化)的时候。
##组件类被实例化的时候，触发一系列流程：

###1) constructor(props) / getInitialState()

这里是对控件的一些状态进行初始化，由于该函数不同于getDefaultProps，在以后的过程中，会再次调用，所以可以将控制控件的状态的一些变量放在这里初始化，如控件上显示的文字，可以通过this.state来获取值，通过this.setState来修改state值。

####在ES6里，通过constructor(构造器)对状态进行初始化

```
constructor(props){
        super(props);
        this.state = {
            loopsRemaining: this.props.maxLoops,
        };
}
```

###2) componentWillMount()

准备加载组件。
这个调用时机是在组件创建，并初始化了状态之后，在第一次绘制 render() 之前。可以在这里做一些业务初始化操作，也可以设置组件状态。这个函数在整个生命周期中只被调用一次。
如果在这个函数里面调用setState，本次的render函数可以看到更新后的state，并且只渲染一次。

###3) render()

render是一个组件必须有的方法，形式为一个函数，渲染界面，并返回JSX或其他组件来构成DOM，和Android的XML布局、WPF的XAML布局类似，只能返回一个顶级元素。

###4) componentDidUpdate()

调用了render方法后，组件加载成功并被成功渲染出来以后所执行的hook函数，一般会将网络请求等加载数据的操作，放在这个函数里进行，来保证不会出现UI上的错误。

##3. 运行(更新)阶段

该阶段主要发生在用户操作之后，或者父组件有更新的时候，此时会根据用户的操作行为，进行相应的界面结构调整。
触发的流程如下：

###1) componentWillReceiveProps(nextProps)

当组件接收到新的props时，会触发该函数。在该函数中，通常可以调用setState()来完成对state的修改。
输入参数 nextProps 是即将被设置的属性，旧的属性还是可以通过 this.props 来获取。在这个回调函数里面，你可以根据属性的变化，通过调用 this.setState() 来更新你的组件状态，这里调用更新状态是安全的，并不会触发额外的 render() 调用。如下：

```
componentWillReceiveProps: function(nextProps) {  
  this.setState({
    likesIncreasing: nextProps.likeCount > this.props.likeCount
  });
}
```

###2) shouldComponentUpdate(nextProps, nextState)

####```返回布尔值（决定是否需要更新组件）```
输入参数 nextProps 和上面的 componentWillReceiveProps 函数一样，nextState 表示组件即将更新的状态值。这个函数的返回值决定是否需要更新组件，如果 true 表示需要更新，继续走后面的更新流程。否者，则不更新，直接进入等待状态。
默认情况下，这个函数永远返回 true 用来保证数据变化的时候 UI 能够同步更新。在大型项目中，你可以自己重载这个函数，通过检查变化前后属性和状态，来决定 UI 是否需要更新，能有效提高应用性能。

###3) componentWillUpdate(nextProps, nextState)

shouldComponentUpdate返回true或者调用forceUpdate之后，就会开始准更新组件，并调用 componentWillUpdate()。
输入参数与 shouldComponentUpdate 一样，在这个回调中，可以做一些在更新界面之前要做的事情。需要特别注意的是，在这个函数里面，你就不能使用 this.setState 来修改状态。这个函数调用之后，就会把 nextProps 和 nextState 分别设置到 this.props 和 this.state 中。紧接着这个函数，就会调用 render() 来更新界面了。

###4) render()

再确定需要更新组件时，调用render，根据diff算法，渲染界面，生成需要更新的虚拟DOM数据。

###5) componentDidUpdate()

虚拟DOM同步到DOM中后，执行该方法，可以在这个方法中做DOM操作。
除了首次render之后调用componentDidMount，其它render结束之后都是调用componentDidUpdate。

```
componentWillMount、componentDidMount和componentWillUpdate、componentDidUpdate
可以对应起来。
区别在于，前者只有在挂载的时候会被调用；而后者在以后的每次更新渲染之后都会被调用。
```
####ps：绝对不要在componentWillUpdate和componentDidUpdate中调用this.setState方法，否则将导致无限循环调用。


###4. 销毁阶段
该阶段主要发生组件销亡的时候，触发componentWillUnmount。当组件需要从DOM中移除的时候，通常需要做一些取消事件绑定，移除虚拟DOM中对应的组件数据结构，销毁一些无效的定时器等工作，都可以在这个方法中处理。

####componentWillUnmount()
当组件要被从界面上移除的时候，就会调用 componentWillUnmount。
在这个函数中，可以做一些组件相关的清理工作，例如取消计时器、网络请求等。

###三、组件更新的方式
更新组件（重新渲染界面）的方式有以下四种：

#####1.首次渲染Initial Render，即首次加载组件
#####2.调用this.setState，状态发生改变（并不是一次setState会触发一次render，React可能会合并操作，再一次性进行render）
#####3.父组件发生更新（一般就是props发生改变，但是就算props没有改变或者父子组件之间没有数据交换也会触发render）
#####4.调用this.forceUpdate，强制更新
用图来表示这四种方式如下：

![更新组件的方式](http://upload-images.jianshu.io/upload_images/2428275-d11e03f614e79ffb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###四、总结
####1.组件生命周期总体流程图
![组件生命周期](http://upload-images.jianshu.io/upload_images/2428275-f08403a3ea1b80f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####2. 生命周期的回调函数总结

生命周期        |调用次数      |能否使用 setSate()|
--------------|-------------|-----------------|
defaultProps / getDefaultProps|	1(全局调用一次)|	否|
constructor / getInitialState |	1  |       否|
componentWillMount	          |1    |       是| 
render                        |	>=1|  	否   |
componentDidMount            |	1	|   是   |
componentWillReceiveProps    |	>=0|	是    |
shouldComponentUpdate	      |  >=0 | 	否    |
componentWillUpdate	         |  >=0	|   否   |
componentDidUpdate            |	>=0|	否    |
componentWillUnmount          |	1	|   否    |



#9、ReactNative组件间的通信

###父组件向子组件通信
* 父组件向子组件传值
  * 通过`props`传递 在父组件中`name='我是父组件向子组件传递的参数'`
  * 在子组件中通过`this.props.name`获取
* 父组件向子组件传递方法
  * 与传递参数方法相同，通过`props`方法这样传递`test={this.onParentClick1} `
  * 在子组件中触发这个方法`this.props.test();`

###子组件向父组件通信
* 子组件向父组件传值
  * 在子组件`state`中定义一个参数`this.state = {name : '我是子组件向父组件传递的参数' }; `
  * 在父组件中给子组件绑定`ref`,如  `<Childern ref='childern'  />`
  * 在父组件中获取子组件的`state`,如`this.refs.childern.state.name`
* 子组件向父组件传递方法
  * 同样通过`ref`来获得，前两部与传参方法相同。 
  * 获取方法的方式也同样`this.refs.childern.onChildenCilck2();`

###非父子组件之间的传值
* 组件之间无关联的形式与子组件向父组件传值的方式相同
* 通过`ref`给组件标记一个名字，同样通过`this.refs.***.state/function`方法相互调用。

##Navigator传值
* `push`传值
  * 首先在路由上配置`{...route.params}`

```
  render() {
let rootViewName = 'FirstView';
let rootComponent = FirstView;

return (
  <Navigator
    initialRoute = {{ name: rootViewName, component: rootComponent }}
    configureScene = {(route) => {
      return Navigator.SceneConfigs.HorizontalSwipeJump ;
    }}
    renderScene = {(route, navigator) => {
      let Component = route.component;
      return <Component {...route.params} navigator = {navigator} />
    }} />
);
}
 
``` 
* 然后在push的时候传`params`属性，下面的`id: Id`,就是我们要传递下去的参数

```
push = (Id) =>{
var _this = this;
const navigator = this.props.navigator;
if (navigator) {
  navigator.push({
    name: 'SecondView',
    component: SecondView,
    params: {
      id: Id,
      getUser: function(user) {
        _this.setState({
          user: user
        })
      }
    }
  });
}
}

```

*最后在二级界面通过`props`属性来接收,`this.props.id`就是上个界面传递过来的参数

```
componentDidMount() {
  this.setState({
    Id : this.props.id
  });
}

```

* `pop`回调
  * 首先在一级界面将一个方法通过`params`向二级界面传递。下面的`getUser: function(user)` 方法就是我们传递下去的方法

```
	push = (Id) =>{
var _this = this;
const navigator = this.props.navigator;
if (navigator) {
  navigator.push({
    name: 'SecondView',
    component: SecondView,
    params: {
      id: Id,
      getUser: function(user) {
        _this.setState({
          user: user
        })
      }
    }
  });
}
}


```  

* 在二级界面`pop`回调的时候，通过`props`触发这个方法。这样就实现了回调

```
	pop = () =>{
if (this.props.navigator) {
  this.props.navigator.pop();
  let user = USER_MODELS[this.state.Id];
  this.props.getUser(user);
}
}

```

* 上面的`user`就是回传的参数，在回调方法`getUser`中进行处理


#10、React Native JSX

React Native中没有DOM的概念，只有组件的概念，所以我们在ReactJS中使用的Html标签以及对DOM的操作是不起作用的，但是组件的生命周期、JSX的语法、事件绑定、自定义属性等，在RN和ReactJS中是一样的。


#11、React Native 调试与打包发布

http://localhost:8081/index.android.bundle?platform=android；当应用启动运行的时候，会自动拉取这个bundle文件，该文件里存放的是应用的全部逻辑代码，在目录中并不存在这个文件，事实上，这个地址只是一个请求地址，而非真正的静态资源文件，是通过包服务器packager通过动态分析index.android.js中的依赖，并对其进行合并得到的，而且该服务允许代码实时渲染。

1.生成一个签名密钥

`keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000`

最后它会生成一个叫做my-release-key.keystore的密钥库文件

2.找到路径/android/app/src/main，并在该目录下新建assets文件夹

3.在工程目录下将index.android.bundle下载并保存到assets资源文件夹中

`curl -k "http://localhost:8081/index.android.bundle" > android/app/src/main/assets/index.android.bundle`

这句命令是重点，如果assets目录中不存在该文件，则打包的apk在执行时显示空白。

Protocol 'http not supported or disabled in libcurl

Windows下安装使用curl命令:http://jingyan.baidu.com/article/a681b0dec4c67a3b1943467c.html

4.添加gradle的android keystore配置

打包的apk在未签名的情况下,在手机中（非root）是不允许安装的

在build.gradle文件中

  //签名
`signingConfigs{
    release {
        storeFile file("/my-release-key.keystore")
        storePassword "密码"
        keyAlias "keyAlias的名字"
        keyPassword "密码"
    }
}
 buildTypes {
    release {
        minifyEnabled false
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        signingConfig signingConfigs.release //添加这句话引用签名配置
    }
}`


5.启用Proguard代码混淆来缩小APK文件的大小

Proguard是一个Java字节码混淆压缩工具，它可以移除掉React Native Java（和它的依赖库中）中没有被使用到的部分，最终有效的减少APK的大小。

重要：启用Proguard之后，你必须再次全面地测试你的应用。Proguard有时候需要为你引入的每个原生库做一些额外的配置。参见app/proguard-rules.pro文件。

def enableProguardInReleaseBuilds = true


6.在/android/目录中执行gradle assembleRelease命令，打包后的文件在 android/app/build/outputs/apk目录中，例如app-release.apk。如果打包碰到问题可以先执行 gradle clean 清理一下。

安装gradle工具（版本与android\gradle\wrapper下的一致），并配置环境变量，配置GRADLE_HOME到你的gradle根目录当中，然后把%GRADLE_HOME%/bin（linux或mac的是$GRADLE_HOME/bin）加到PATH的环境变量。

配置完成之后，运行gradle -v，检查一下是否安装无误


7.将apk发布到各大应用市场（BUILD SUCCESSFUL）




#12、React Native View组件

在React Native里有一个类似于div的组件，那就是View组件，支持多层嵌套，支持flexbox布局

实例步骤：

1.加载View组件

2.创建组件

3.添加样式表

4.注册入口

5.外层布局

 ``` 
  <View style={styles.container}>

        <View style={styles.item}></View>
        <View style={styles.item}></View>
        <View style={styles.item}></View>

      </View>
 ```

6.flexbox水平三栏布局

  外联样式：`style={styles.container}`

  内联样式：`style={{flex:1,borderWidth:1,borderColor:'red',flexDirection:'row'}}`

  多个样式：`style=
  {[styles.container,styles.flex,{borderWidth:1,borderColor:'red'}]}`

  

7.上下两栏布局
 
 ```
 <View style={[styles.center,styles.flex]}>
            <Text>团购</Text>
          </View>

          <View style={[styles.center,styles.flex]}>
            <Text>客栈，公寓</Text>

          </View>
 ```

8.完善效果

``` 
		<View style={[styles.item,styles.lineLeftRight]}>

          <View style={[styles.center,styles.flex,styles.lineCenter]}>
            <Text style={styles.font}>海外酒店</Text>
          </View>

          <View style={[styles.center,styles.flex]}>
            <Text style={styles.font}>特惠酒店</Text>

          </View>



        </View>
```
#13、React Native Text组件

Text组件主要用于显示文本；具有响应性，可以嵌套，可以继承样式

内部Text组件可以继承外部Text组件的样式

Text组件的特性：

1.onPress

2.numberOfLines 最多显示多少行

3.onLayout

案例：网易新闻客户端 Text组件实现

组件的颗粒度设计主要取决于应用的结构设计

1.头部组件 单独封装 独立成一个文件

 `module.exports=Header;`

`const Header=require('./header');`



2.列表组件

` <List title='一线城市楼市退烧 有房源一夜跌价160万'></List>`



3.重要新闻 组件

`<ImportantNews
                news={[
                '解放军报报社大楼正在拆除 标识已被卸下(图)',
                '韩国停签东三省52家旅行社 或为阻止朝旅游创汇',
                '南京大学生发起亲吻陌生人活动 有女生献初吻-南京大学生发起亲吻陌生人活动 有女生献初吻-南京大学生发起亲吻陌生人活动 有女生献初吻',
                '防总部署长江防汛:以防御98年量级大洪水为目标'
                ]}>
            </ImportantNews>`

`<Text
                onPress={this.show.bind(this,this.props.news[i])}
                    numberOfLines={2}
                    style={styles.news_item}>{this.props.news[i]}</Text>
                    `



#14、React Native Navigator组件初探

一个应用往往是由多功能视图组成！多页面的切换：路由或导航

在RN中专门负责视图切换的组件：Navigator,NavigatorIOS

导航器对比：

Navigator和NavigatorIOS都可以用来管理应用中“场景”的导航（也可以称作屏幕）。导航器建立了一个路由栈，用来弹出，推入或者替换路由状态。它们和html5中的history API很类似。主要的区别在于NavigatorIOS使用了iOS中的UINavigationController类，而Navigator则完全用js重写了一个类似功能的React组件。因此Navigator可以兼容iOS和Android，而NavigatorIOS只能用于iOS。

NavigatorIOS
轻量、受限的API设置，使其相对Navigator来说不太方便定制。
由开源社区主导开发 —— React Native的官方团队并不在自己的应用中使用。
对于大多数正式的App开发，我们建议使用Navigator —— 使用NavigatorIOS实现复杂的需求很容易碰到麻烦。

导航器通过路由对象来分辨不同的场景。利用renderScene方法，导航栏可以根据指定的路由来渲染场景。
可以通过configureScene属性获取指定路由对象的配置信息，从而改变场景的动画或者手势。

最后的几行: 
renderScene={(route, navigator) => {
let Component = route.component;
return <Component {...route.params} navigator={navigator} />
}} />
);

这里是每个人最疑惑的，我们先看到回调里的两个参数:route, navigator。通过打印我们发现route里其实就是我们传递的name,component这两个货，navigator是一个Navigator的对象，为什么呢，因为它有push pop jump...等方法，这是我们等下用来跳转页面用的那个navigator对象。

return <Component {...route.params} navigator={navigator} />
这里有一个判断，也就是如果传递进来的component存在，那我们就是返回一个这个component，结合前面 initialRoute 的参数，我们就是知道，这是一个会被render出来给用户看到的component，然后navigator作为props传递给了这个component。

所以下一步，我们可以直接拿到这个 props.navigator:


#15、React Native Navigator参数传递

怎么传递参数过去，或者从对方获取参数。


##从列表页To详情页：
传递参数，通过push就可以了。

params: {
                    id: this.state.id
                }

这个语法是把 routes.params 里的每个key 作为props的一个属性：{...route.params}

 componentDidMount() {
        //这里获取从列表页传递过来的参数: id
        this.setState({
            id: this.props.id
        });
    }

使用这个参数：{this.state.id}

##从详情页To列表页：

综合实例：从列表页传递用户id给详情页，详情页跟进用户id查询用户信息，并把
用户信息回传给列表页显示出来

```
const self=this;

 params:{
                    id:this.state.id,
                    //从详情页获取user
                    getUser: function(user) {
                        self.setState({
                            user: user
                        })
                    }
                }

 if(this.props.getUser) {
            let user = USER_MODELS[this.props.id];
            this.props.getUser(user);
        }

        if(navigator) {
            //很熟悉吧，入栈出栈~ 把当前的页面pop掉，这里就返回到了上一个页面:List了
            navigator.pop();
        }

```


#16、React Native TextInput组件

文本输入框：基本组件 自动补全的搜索功能

调试apk目录：DongFang\android\app\build\outputs\apk

TextInput的主要属性和事件如下：

autoCapitalize：枚举类型，可选值有none sentences words characters 当用户输入时，用于提示

placeholder：占位符，在输入前显示的文本内容

value：文本输入框的默认值

placeholderTextColor：占位符文本的颜色

password：boolean类型 true表示密码输入显示*

multiline：多行输入

editable：文本框是否可输入

autoFocus:自动聚焦

clearButtonMode：枚举类型，never while-editing unless-editing always 用于显示清除按钮

maxLength：能够输入的最长字符数

enablesReturnKeyAutomatically：如果为true 表示没有文本时键盘是不能有返回键的，其默认值为false

returnKeyType：枚举类型 default go google join next route search send yahoo done emergency-call 表示软键盘返回键显示的字符串

secureTextEntry：隐藏输入内容，默认值为false

onChangeText：当文本输入框的内容变化时，调用改函数；onChangeText接收一个文本的参数对象

onChange：当文本变化时，调用该函数

onEndEditing：当结束编辑时，调用改函数

onBlur：失去焦点触发事件

onFocus：获得焦点时触发事件

onSubmitEditing：当结束编辑后，点击键盘的提交按钮触发该事件



#17、React Native TextInput自动提示的搜索框



很多app的搜索都是这样的：我们输入一个关键词的时候，会列出相关的搜索结果列表，一般情况下，完成该功能需要一个搜索服务，返回N条结果，并将其展示出来;这里我们用静态数据模拟出来。



#18、React Native Touchable类组件

React Native没有像Web开发那样给元素绑定click事件，前面讲的Text组件有onPress事件回调，View组件是没有的，但是在实际项目开发中，很多其他的组件也是需要可以被点击的，RN提供了3个组件来赋予被点击的能力（去包裹其他组件即可），这3个组件被称为“Touchable类组件”：

1.TouchableHighlight  高亮

属性：activeOpacity(设置透明度)、onHideUnderlay、onShowUnderlay、underlayColor(点击时背景阴影效果的背景颜色)

2.TouchableOpacity   透明度

属性：activeOpacity

3.TouchableWithoutFeedback 无反馈 不会出现任何视觉变化

不建议使用；属性：onLongPress、onPressIn、onPressOut

在app中我们希望点击的时候会有一些视觉上的变化，这个变化会提醒我们已经点击过了，从而避免重复点击



#19、React Native 图片Image组件

React Native的Image组件调用的图片途径比较多：网络图片、本地图片、照相机图片

#Image组件的属性：

resizeMode：图片适用的模式 cover、contain、stretch

source:图片的引用地址

网络图片：source={{uri:'http://.png'}}

本地图片：source={require('./baidulogo.png')}

静态图片资源：注意：如果你添加图片的时候packager正在运行，则你需要重启packager以便能正确引入新添加的图片。

这样会带来如下的一些好处:

iOS和Android一致的文件系统。
图片和JS代码处在相同的文件夹，这样组件就可以包含自己所用的图片而不用单独去设置。
不需要全局命名。你不用再担心图片名字的冲突问题了。
只有实际被用到（即被require）的图片才会被打包到你的app。
现在在开发期间，增加和修改图片不需要重新编译了，只要和修改js代码一样刷新你的模拟器就可以了。
与访问网络图片相比，Packager可以得知图片大小了，不需要在代码里再声明一遍尺寸。
现在通过npm来分发组件或库可以包含图片了。

注意：为了使新的图片资源机制正常工作，require中的图片名字必须是一个静态字符串。

#使用混合App的图片资源

如果你在编写一个混合App（一部分UI使用React Native，而另一部分使用平台原生代码），也可以使用已经打包到App中的图片资源（通过Xcode的asset类目或者Android的drawable文件夹打包）

<Image source={{uri: 'app_icon'}} style={{width: 40, height: 40}} />

注意：这一做法并没有任何安全检查。你需要自己确保图片在应用中确实存在，而且还需要指定尺寸

注意：网络图片，你需要手动指定图片的尺寸

关于图片的尺寸，React Native会自动为你选好。如果没有，则会选择最接近的尺寸进行缩放，但也至少缩放到比所需尺寸大出50%，以使图片看起来仍然足够清晰。这一切过程都是自动完成的，所以你不用操心自己去完成这些繁琐且易错的代码。




#20、React Native Picker组件和箭头函数

本组件可以在iOS和Android上渲染原生的选择器（Picker）

#21、React Native ProgressBar组件

分平台的：ProgressBarAndroid  ProgressViewIOS

styleAttr：进度条的样式 Horizontal Small Large Inverse SmallInverse LargeInverse

progress：当前的进度值（在0到1之间）



#22、React Native DrawerLayoutAndroid组件

封装了平台DrawerLayout（仅限安卓平台）的React组件。抽屉（通常用于导航切换）是通过renderNavigationView方法渲染的，并且DrawerLayoutAndroid的直接子视图会成为主视图（用于放置你的内容）。导航视图一开始在屏幕上并不可见，不过可以从drawerPosition指定的窗口侧面拖拽出来，并且抽屉的宽度可以使用drawerWidth属性来指定。

drawerPosition：DrawerLayoutAndroid.positions.Right 左右 默认左

drawerWidth：指定抽屉的宽度，也就是从屏幕边缘拖进的视图的宽度

onDrawerClose

onDrawerOpen

onDrawerSlide：每当导航视图（抽屉）产生交互的时候调用此回调函数

onDrawerStateChanged：idle（空闲） dragging（拖拽中） settling（停靠中）

renderNavigationView：渲染一个可以从屏幕一边拖入的导航视图

drawerLockMode：设置抽屉的锁定模式 有三种模式：

1.unlocked (默认值)，意味着此时抽屉可以响应打开和关闭的手势操作

2.locked-closed，意味着此时抽屉将保持关闭，不可用手势打开。

3.locked-open，意味着此时抽屉将保持打开，不可用手势关闭。

无论抽屉处于那种状态，都仍然可以调用openDrawer/closeDrawer这两个方法打开和关闭


#23、React Native ViewPagerAndroid组件初探

一个允许在子视图之间左右翻页的容器。每一个ViewPagerAndroid的子容器会被视作一个单独的页，并且会被拉伸填满ViewPagerAndroid。

注意所有的子视图都必须是纯View，而不能是自定义的复合容器

属性：

1.initialPage 初始选中页的下标

2.onPageScroll 当在页间切换时（不论是由于动画还是由于用户在页间滑动/拖拽）执行

回调参数中的event.nativeEvent对象会包含如下数据：
position offset 一个在[0,1)（大于等于0，小于1）之间的范围，代表当前页面切换的状态

3.onPageScrollStateChanged idle dragging settling

4.onPageSelected 这个回调会在页面切换完成后（当用户在页面间滑动）调用

回调参数中的event.nativeEvent对象会包含如下的字段： position

5.scrollEnabled boolean



#24、React Native 仿异步获取网络数据

进入首页HomeUI获取网络数据

Android原生开发：子线程 handler机制  异步任务AsyncTask

ReactNative 擅长UI界面处理  通过this.state来触发

RN中的网络请求：XMLHttpRequest Fetch  post get

MVC mListView.setAdapter(new myAdapter)  

Item封装成一个组件   <Item ></Item>



#25、React Native 开源轮播组件react-native-swiper

github上搜索 react-native-swiper

在项目的根目录（即package.json文件所在的目录）

npm的命令：

安装模块：npm i react-native-swiper --save

查看模块：npm view react-native-swiper

删除模块：npm rm react-native-swiper --save

清理缓存：npm cache clean

查看帮助命令：npm help 命令

入口组件：DfyProject01  

注意：设置轮播组件Swiper的包裹容器高度，使用属性设置，不能通过样式设置

实现滚动视图：ScrollView 计算步长


#26、React Native WebView组件

Hybrid App（混合模式移动应用）是指介于web-app、native-app这两者之间的app，兼具“Native App良好用户交互体验的优势”和“Web App跨平台开发的优势”。

重点理解：为什么rn中会有WebView？

automaticallyAdjustContentInsets：是否自动调整内部内容

bounces（IOS）：回弹效果 如果为false，则内容拉到底部或头部不回弹，默认为true

domStorageEnabled(Android)：仅限Android平台。指定是否开启DOM本地存储

javaScriptEnabled：仅限Android平台。iOS平台JavaScript是默认开启的

contentInset：内部内容偏移值 该值为一个JavaScript对象{top:number,left:number,bottom:number,right:number}

source:{{uri:'网址'}}在WebView中载入一段静态的html代码或是一个url（还可以附带一些header选项）{{html:'html代码块'}}

injectedJavaScript:注入的js代码，其值为字符串，如果加上了该属性，就会在webview里面执行js代码（在网页加载之前注入）

mediaPlaybackRequiresUserAction：设置页面中的HTML5音视频是否需要在用户点击后再开始播放。默认值为false

onNavigationStateChange：监听导航状态变化的函数（当发现浏览器地址改变时，触发事件）

renderError：监听渲染页面出错的函数

startInLoadingState：是否开启页面加载的状态

renderLoading:webview组件正在渲染页面时触发的函数，需要同startInLoadingState一起使用，当startInLoadingState为true时该函数才起作用

scrollEnabled（IOS）：表示webview里面页面是否能滚动，如果其值为true则可以滚动，否则禁止滚动

scalesPageToFit：按照页面比例和内容宽高比例自动缩放内容

#27、React Native 常用IDE开发工具

Web前端：WebStorm Sublime  都是收费的 

FaceBook官方：nuclide 只支持Mac 基于Atom（github的）（Atom最大的特色就是可以安装很多的插件来完成我们的需求）炫酷插件

跨平台免费的：微软老大哥的 Visual Studio Code 免费的 

Visual Studio Code (简称 VS Code / VSC) 是一款免费开源的现代化轻量级代码编辑器，支持几乎所有主流的开发语言的语法高亮、智能代码补全、自定义热键、括号匹配、代码片段、代码对比 Diff、GIT 等特性，支持插件扩展，并针对网页开发和云端应用开发做了优化。软件跨平台支持 Win、Mac 以及 Linux，运行流畅，可谓是微软的良心之作

Visual Studio Code 现在已经支持大量的扩展插件，大家可以根据自己的需求打造出最适合自己使用的编辑器了
插件：https://marketplace.visualstudio.com/VSCode



#28、React Native ListView组件

原生：mListView mAdapter List集合数据  MVC

ListView组件是React Native中一个比较核心的组件，用途非常的广。该组件设计用来高效的展示垂直滚动的数据列表。最简单的API就是创建一个ListView.DataSource对象，同时给该对象传入一个简单的数据集合。并且使用数据源(data source)实例化一个ListView组件,定义一个renderRow回调方法(该方法的参数是一个数组)，该renderRow方法会返回一个可渲染的组件(该就是列表的每一行的item)

由于平台差异性，React Native 中的滚动列表组件 ListView 并没有直接映射为 android 中的 ListView 或 iOS 中的 UITableView，而是在ScrollView 的基础上使用 JS 做了一次封装。这样，滚动体验部分由 Native 负责，而 React 部分则专注于组件何时渲染、如何渲染等问题。

数据源默认的格式有三个维度：

第一个维度是 sectionId ，标识属于哪一段， 可以手动指定或隐式地使用数组索引或对象的 key 值；
第二个维度是 rowId ，标识某个数据段下的某一个行，同样可以手动指定或隐式地使用数组索引或对象的 key 值；
第三个维度是具体的数据对象，根据实际的需要而定。
需要注意的是，上面只是 默认的数据格式 ，如果它不符合实际的需求， 完全可以使用自定义的数据结构 。唯一的区别就是需要额外指定给 ListView 数据源中哪些是 id，哪些是 rowData。

![listview数据格式](http://image18-c.poco.cn/mypoco/myphoto/20160601/22/17351665220160601220430096.png?755x561_130) 

DataSource 的构造函数接收以下4个参数（都是可选）：
rowHasChanged : 用于在数据变化的时候，计算出变化的部分，在更新时只渲染脏数据；
sectionHeaderHasChanged : 同理，在列表带分段标题时需要实现；
getRowData/getSectionHeaderData : 如果遵循默认的数据源格式，这两个方法就没有必要实现，用内部默认的即可；而当数据源格式是自定义时，需要手动实现这两个方法。

DataSource 的初始化一般在 constructor 方法中

数据源确定后，下一个工作就是列表的渲染。在渲染时发挥重要作用的是 renderRow 属性，它接收数据源中保存的数据对象，并通过返回值确定该行该如何进行展现。我们可以对所有行统一进行展现，也可以根据里面的字段做出不同的展现。在列表包含 sectionHeader 时，还需要实现 renderSectionHeader 方法。

#注意

要更新datasource中的数据，请（每次都重新）调用cloneWithRows方法（如果用到了section，则对应cloneWithRowsAndSections方法）。数据源中的数据本身是不可修改的，所以请勿直接尝试修改。clone方法会自动提取新数据并进行逐行对比（使用rowHasChanged方法中的策略），这样ListView就知道哪些行需要重新渲染了。

#React Native ListView sticky效果实现

dataBlob{The dataBlob is a data structure (generally an object) that holds all the data powering the ListView}：dataBlob 包含ListView所需的所有数据（section header 和 rows），在ListView渲染数据时，使用 getSectionData 和 getRowData 来渲染每一行数据。 dataBlob 的 key 值包含 sectionID + rowId


![dataBlob](http://image18-c.poco.cn/mypoco/myphoto/20160601/22/17351665220160601221412055.png?677x356_130) 

sectionIDs[]：用于标识每组section

![dataBlob](http://image18-c.poco.cn/mypoco/myphoto/20160601/22/1735166522016060122232005.png?958x356_130) 

rowIDs[]：用于描述每个 section 里的每行数据的位置及是否需要渲染。在ListView渲染时，会先遍历 rowIDs 获取到对应的 dataBlob 数据。
![dataBlob](http://image18-c.poco.cn/mypoco/myphoto/20160601/22/1735166522016060122220803.png?576x340_130) 

片段头sticky失效原因：

1.Found this out by accident, but if you put your ListView inside a ScrollView, the headers will not be sticky

2.iOS RCTScrollView implements sticky headers 而android没有

3.ListView的Android版本不支持sticky-header特性

4.用这个替代：https://github.com/emilsjolander/StickyScrollViewItems



#29、React Native ListView高级特性

##分页

当数据量很大的时候如何分页加载 。这种情形分两种情况考虑：

1.数据一次性拿到，边滚动边加载

2.数据不是一次性拿到，而是有可能分屏取数据

对于第一种情况，在 ListView 内部其实已经做了分页的处理：

ListView 内部通过 curRenderedRowsCount 状态保存已渲染的行数；
初始状态下，要加载的数据条数等于 initialListSize （默认为 10 条）；
在滚动时检测当前滚动的位置和最底部的距离，如果小于 scrollRenderAheadDistance (默认为 1000)，就更新 curRenderedRowsCount ，在它原有值基础上加 pageSize 个（默认为 1 条）；
由于属性变化，触发了 ListView 重新的 render 。在渲染过程中， curRenderedRowsCount 起到截断数据的作用，React 的 diff 算法使得只有新加入的数据才会渲染到了界面上。
整个过程类似于 Web 端懒加载机制，即 每次在和底部的距离达到一个阈值时，加载接下来的 pageSize 个数据 。

对于第二种情况，ListView 提供了相关的属性：

onEndReachedThreshold ，在滚动即将到达底部时触发；
onEndReached ，在已经到达底部时触发；

我们可以在这两个方法中调用接口去拿数据，取到数据后再更新数据源。

##多列(Grid效果)

很多页面中的列表并非单列的，乍一看似乎要做出不少调整，但实际上只通过布局即可达到相关效果。ListView 并没有强制要求一个 rowData 在展示时一定要占满一行，在多列的情况下，我们适时调整每个 rowData 占据的宽度即可。

![grid](http://image18-c.poco.cn/mypoco/myphoto/20160602/23/17351665220160602230133097.png?319x112_130) 

由于 React Native 使用 Flexbox 进行布局，给ListView设置属性contentContainerStyle；在实现多列时，主要用到的是 flexWrap：wrap 属性：它的效果类似于 float，即水平地排列每一项，当放不下时进行折行处理。在设置每行视图占据一半宽度后就达到了两列的效果，多列的类似。

##滚动

ListView 只是整合了数据和展现，但实际滚动的功能还是由 ScrollView 全权负责。ScrollView 实现完全和平台相关：在 iOS 上，它映射为 RCTScrollView ；在 Android 上，它映射为 RCTScrollView 和 AndroidHorizontalScrollView 。

React Native 让不同端上的技术融合在了一起，同时也给开发人员提出了更高的要求。以 ScrollView 为例，大量的属性其实原封不动映射给了 UIScrollView ，这就意味着如果想再深入地研究下去，必须对客户端相关技术有足够了解。无论是前端还是客户端，跳出自己熟悉的那片领域也许才是更进一步的关键。

谈到滚动，有一点不得不说的就是 列表的无限加载 ，这牵涉到滚动的性能。

Github 上的这个 issue 对此展开了热烈的讨论。其中有人就提到，数据量很大情况下，ListView 在加载时所占用的 CPU 和内存会大大增加，滚动到最后就导致了应用 crash。

为此，ListView 中新添加了一个实验性的属性： removeClippedSubviews ，它能在滚动时及时删掉列表中处于视窗的之外的行，以此达到降低内存消耗的目的。不幸的是，即使设置了这个属性，程序虽然各项占用减少了不少，但还是没避免崩溃的命运。处于好奇，我也在最新版的 ListView 基础上做了简单尝试，不断加载一个无限大的列表，但并没有出现崩溃的情况：

即使加载了 3000、4000 行，Android 真机、iOS 真机和 iOS 模拟器上都没有崩溃；
Android 上明显感到数据加载有 阶段性的延时 ，即滚动一定程度后，再次滚动数据始终加载不出来或要等一段时间才加载出来，体验较差；iOS 相比要流畅的多；
但不崩溃并非最终的目的，很多 React Native 使用者都在试图改进 ListView 的性能表现，相比于直接使用 Native 端的组件，ListView 性能还是差强人意，有很大优化空间。

##总结

ListView 并没有创造出新的东西，它只是集各家所长，很好地将 React 的视图渲染和 Native 端很成熟的滚动机制融合在了一起，使用起来和其他组件无差，静态地定义View、动态地组织数据，是给人带来的直观感受。



#30、React Native 开源Tab导航组件react-native-tab-navigator

##Visual Studio Code编辑工具：

1.解决修改字体或其他报错的问题

2.使用技巧：拆分编辑器 ctrl+\

3.无插件化的代码diff：右键文件--->选择以进行比较

4.格式化js文件  右键代码区域--->格式代码 Alt+Shift+F

开源组件react-native-tab-navigator：

React Native原生的控件仅有TabBarIOS可供iOS平台使用

React的核心思想：组件化   特别适合一个团队开发项目

##react-native-tab-navigator的好处：

1.跨平台 纯js 支持android与ios


#31、React Native 开源侧边栏组件react-native-side-menu

当前项目目录：npm i react-native-side-menu --save

导入：import SideMenu from 'react-native-side-menu';

用RN实现仿QQ的侧边栏效果

注意：Menu组件里面 使用ScrollView必须设置scrollsToTop={false}


#32、React Native Windows下玩苹果

RN开发android与ios；ios的系统也是必须要的

mac电脑：可以直接调试ios与android

windows：只能调试android

黑苹果：自从苹果采用Intel的处理器，OS X被黑客破解后可以安装在Intel CPU与部分AMD CPU的机器上。从而出现了一大批未购买苹果机而使用苹果操作系统的机器，被称为黑苹果(Hackintosh)；在Mac苹果机上面安装原版Mac系统的被称为白苹果（Macintosh），与黑苹果相对。

虚拟机装苹果：系统要给力点  Host

http://jingyan.baidu.com/article/d621e8da27fe7c2865913fde.html

软件工具下载：http://pan.baidu.com/s/1bItYsm



#33、React Native Mac环境搭建(Windows虚拟机)

1.安装Homebrew /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2.brew install node

3.brew install watchman

4.推荐您定期运行brew update && brew upgrade来保持上述几个程序为最新版本

5.安装Xcode 7.1 不要安装最新版本 注意安全风险发生

6.npm install -g react-native-cli

7.将npm仓库源替换为国内镜像

8.react-native init DongFang

9.运行iOS应用


Win7是Server，Mac是Client，VMware上运行Mac系统
1、在VMware的Options菜单中选择Shared Folders选项
2、选择Always enabled选项
3、然后选择要在Win7系统上共享的文件夹路径名
4、在Win7系统下将改文件夹设为共享
5、进入MAC系统桌面右键点击Finder前往菜单Connectting to Server
6、在连接服务器对话框中输入[smb://Windows主机的IP地址],其中smb是访问Windows共享文件夹所使用的协议名称
7、连接到Windows主机之后会显示该主机所共享的文件夹，选择想要访问的一个即可
8、这样再次打开Finder的时候就可以直接访问到共享文件夹了


#34、React Native 如何调试

(Android 5.0及以上)不用设置ip和端口：

开启USB调试，使用adb reverse命令，运行adb reverse tcp:8081 tcp:8081 就可以使用Reload JS和其它的开发选项了

大部分现代的安卓设备已经没有了硬件"Menu"按键，这是我们用来调出开发者菜单的。在这种情况下你可以通过摇晃设备来打开开发者菜单(重新加载、调试，等等……)

(Android 5.0以下)需要设置ip+端口：

摇晃设备，或者运行adb shell input keyevent 82，可以打开开发者菜单


1.调试输出 console.log();

2.打断点breakpoint 看value





#36、React Native API学习AppRegistry

只有配合使用React Native的常用组件和常用API，才能更好的开发应用程序

AppRegistry是JS运行所有React Native应用的入口。应用的根组件应当通过AppRegistry.registerComponent方法注册自己，当注册完后，原生系统才可以加载应用的bundle包并且触发AppRegistry.runApplication来真正运行应用。



#37、React Native API学习AsyncStorage

AsyncStorage是一个简单的、具有异步特性的键值对的存储系统，全局的！替代LocalStorage

AsyncStorage里面都有一个回调函数，而回调的第一个参数都是错误对象，如果发生错误，该对象就会展示错误信息，否则为null；每个方法都会返回一个Promise对象。

案例：购物车（数据共享）

列表页 结算页

1.数据模型构建

2.列表项Item组件（es6中默认属性与属性类型的定义）

3.列表组件List

guid代码 生成

4.购物车组件

去取AsyncStorage中存储的数据，一定是在DidMount生命周期里，不能在WillMount里

5.将组件串联起来

推荐由React Native中文网封装维护的react-native-storage模块，提供了较多便利功能。


#38、React Native 物理back键详解

在上一代码的基础上：


```
componentWillMount() {
    if (Platform.OS === 'android') {
      BackAndroid.addEventListener('hardwareBackPress', this.onBackAndroid);
    }
  }
  componentWillUnmount() {
    if (Platform.OS === 'android') {
      BackAndroid.removeEventListener('hardwareBackPress', this.onBackAndroid);
    }
  }

 onBackAndroid = () => {
        const { navigator } = this.props;
        const routers = navigator.getCurrentRoutes();
        console.log('当前路由长度：'+routers.length);
        if (routers.length > 1) {
            navigator.pop();
            return true;//接管默认行为
        }
        return false;//默认行为
	};
```	
	

说明：BackAndroid在iOS平台下是一个空实现，所以理论上不做这个Platform.OS === 'android'判断也是安全的。
如果所有事件监听函数中，没有任何一个返回真值，就会默认调用默认行为

navigator是同一个，这个事件在最外层注册就行（不是initialRoute的组件，是AppRegistry的组件），
否则会调用多次pop的，这个代码接管的是整个应用的后退键

放到initialRoute里会有问题，你两三个页面测不出来，页面层次多了组件会unmount，然后事件就丢了

addEventListener()第三个参数useCapture (Boolean)详细解析：
•true 的触发顺序总是在 false 之前；

•如果多个均为 true，则外层的触发先于内层；

•如果多个均为 false，则内层的触发先于外层。


需要注意的是，不论是bind还是箭头函数，
每次被执行都返回的是一个新的函数引用，
因此如果你还需要函数的引用去做一些别的事情（譬如卸载监听器），那么你必须自己保存这个引用

```
// 错误的做法
class PauseMenu extends React.Component{
    componentWillMount(){
        AppStateIOS.addEventListener('change', this.onAppPaused.bind(this));
    }
    componentDidUnmount(){
        AppStateIOS.removeEventListener('change', this.onAppPaused.bind(this));
    }
    onAppPaused(event){
    }
}
// 正确的做法1
class PauseMenu extends React.Component{
    constructor(props){
        super(props);
        this._onAppPaused = this.onAppPaused.bind(this);
    }
    componentWillMount(){
        AppStateIOS.addEventListener('change', this._onAppPaused);
    }
    componentDidUnmount(){
        AppStateIOS.removeEventListener('change', this._onAppPaused);
    }
    onAppPaused(event){
    }
}


// 正确的做法2
class PauseMenu extends React.Component{
    componentWillMount(){
        AppStateIOS.addEventListener('change', this.onAppPaused);
    }
    componentDidUnmount(){
        AppStateIOS.removeEventListener('change', this.onAppPaused);
    }
    onAppPaused = (event) => {
        //把方法直接作为一个arrow function的属性来定义，初始化的时候就绑定好了this指针
    }
}
```

例子：“再按一次退出应用”
//到了主页了

```
      if (this.lastBackPressed && this.lastBackPressed + 2000 >= Date.now()) {
        //最近2秒内按过back键，可以退出应用。
        return false;
      }
      this.lastBackPressed = Date.now();
      ToastAndroid.show('再按一次退出应用',ToastAndroid.SHORT);
      return true;
```    
      
我们在监听函数中不能决定是否要调用默认行为，要等待一个异步操作之后才调用默认行为，此时可以通过第二种办法：

使用BackAndroid.exitApp()来退出应用。

例子：在退出应用之前保存数据

写法1：
 
 ```
 onBackAndroid = () =>{
    
    saveData().then(()=>{
      BackAndroid.exitApp();
    });
    return true;
  }
 ``` 
  在监听函数中，我们开始异步事件，并直接return true。此时默认行为不会被调用。当保存完毕后，我们调用exitApp()，触发默认行为，退出应用。
  
  写法2：
  
  ```
   onBackAndroid = async () =>{
    
    await saveData();
    BackAndroid.exitApp();
  }
  ```
  这里我们用了async函数，async 函数总是返回一个Promise，Promise作为一个对象，也被认为是一个“真值”，所以这种情况下默认行为总是不会被调用。当保存完毕后，我们调用exitApp()，触发默认行为，退出应用。
  
  根据当前界面决定作何动作
  有时候我们有这样的需求：当用户处于某些界面下时，back键要做特殊的动作，如：提示用户是否要保存数据，或者解锁界面禁止back键返回等等。此时，最佳实践是在route或route中对应的Component上保存关于如何处理back键的信息：
 
 
 ```
 onBackAndroid = () => {
    const nav = this.navigator;
    const routers = nav.getCurrentRoutes();
    if (routers.length > 1) {
      const top = routers[routers.length - 1];
      if (top.ignoreBack || top.component.ignoreBack){
        // 路由或组件上决定这个界面忽略back键
        return true;
      }
      const handleBack = top.handleBack || top.component.handleBack;
      if (handleBack) {
        // 路由或组件上决定这个界面自行处理back键
        return handleBack();
      }
      // 默认行为： 退出当前界面。
      nav.pop();
      return true;
    }
    return false;
  };
  
 ```


#39、React Native 复杂的组件通讯三种方案
接着上面的代码，从一个bug入手，透过问题去学习，大大提升学习效率
解决bug：组件pop之后，之前的组件没有更新？
例子：在购物车里清空了，但是pop之后，商品详情页并没有更新？
3.更新阶段
主要发生在用户操作之后或父组件有更新的时候，此时会根据用户的操作行为进行相应的页面结构的调整
componentWillReceiveProps、shouldComponentUpdate、componentWillUpdate、render、componentDidUpdate
pop之后，数据已经改变了，但是之前的组件没什么变化，组件的数据不同步了，解决方案：

```
方案1：监听didfocus事件，focus到当前路由的时候重新加载数据
            navigationContext.addListener('didfocus', callback)来替代
            componentWillMount() {
        console.log('List---componentWillMount');
        let navigator = this.props.navigator;


        let callback = (event) => {
            console.log(
                'List : 事件类型',
                {
                    route: JSON.stringify(event.data.route),
                    target: event.target,
                    type: event.type,
                }
            );
        };

        // Observe focus change events from this component.
        this._listeners = [
            navigator.navigationContext.addListener('willfocus', callback),
            navigator.navigationContext.addListener('didfocus', callback),
        ];
    }


    componentWillUnmount(){
        console.log('List---componentWillUnmount');
        this._listeners && this._listeners.forEach(listener => listener.remove());
    }
    更新去取数据不用放到componentDidMount，直接放到didfocus的回调即可 不太稳定 
```   

``` 
方案2：Navigator参数传递：往下一个路由push的时候传递参数（一个回调），在组件pop之前先调用此回调刷新数据
navigator.push({
                name: 'GouWu',
                component: GouWu,
                params: {

                    fetchData: function () {

                        console.log('启动fetchData里的方法了');

                        AsyncStorage.clear(function (err) {
                            if (!err) {
                                _that.setState({
                                    count: 0,
                                });

                                alert('购物车已经清空');
                            }
                        });

                    }
                }
            })
            
            这是在点击清空购物车之后，马上pop，同时去触发回调
            clearStorage() {
        let _that = this;

        //触发一下回调 让数据同步
        console.log('点击了清空购物车');
        if (this.props.fetchData) {
            console.log('点击了清空购物车----回调去影响List页面');
            this.props.fetchData();

        }

        const { navigator } = this.props;
        if (navigator) {

            navigator.pop();
        }


    }
```
还有一种情况：在点击清空购物车之后，不马上pop，而是通过点击物理back键去触发回调
这个就要复杂很多，
错误做法：

```
const top = routers[routers.length - 1];
      console.log('栈顶的路由---'+top.component);
      if (top.component.props.fetchData) {
        console.log('回调fetchData了');
        top.component.props.fetchData();
      }
```
  注意：  route.component是一个class 而不是一个object instance ，在里面找props是不可能找得到的，
  如果一定需要从route上找到instance，需要在renderScene里给render的东西指定ref
类似 <Component ref={r=>route.ref = r} />，然后通过route.ref来访问，但注意不应该假设route.ref总是有值
一定要判断下 if(route.ref)


 

方案3：采用redux/event等方式完成跨组件通讯

社区主流还是redux，但是建议大家抛弃redux了，因为太繁琐了，我们马上有更方便的架构，来自nodejs社区的，不是前端的方案
RN官方并不提供这个方案，redux也不是官方的
涉及到十几个插件 核心是decorator   都是npm上的插件
主要是一种 前端后端 结构和风格一致 的思想


注意：方案1不推荐，推荐方案2或3




#40、React Native 安装Nuclide与API学习AlertIOS

安装mac下React Native的开发工具Nuclide

FaceBook官方：nuclide 只支持Mac 基于Atom（github的）（Atom最大的特色就是可以安装很多的插件来完成我们的需求）炫酷插件

https://atom.io/ 下载atom 

https://nuclide.io/ 

https://github.com/facebook/nuclide

打开atom，如果nuclide安装成功，则可以看到nuclide的欢迎界面

brew update && brew upgrade

flow 一个静态的对js类型检查器

brew install flow

保存：mac (command+s)  windows(win+s)

AlertIOS他的静态方法有两个：

alert(title,message,[] buttons) 普通对话框

prompt(title,message,[] buttons) 提供输入的对话框

如果buttons为空数组，默认也会有一个ok按钮，如果数据的长度过长，按钮就会垂直排列！



#41、React Native API学习DatePickerAndroid与TimePickerAndroid

日期、时间选择器  Android中是以api的形式，IOS是以组件的形式

DatePickerAndroid：

static open(options: Object) 

打开一个标准的Android日期选择器的对话框

可选的options对象的key值如下：

date (Date对象或毫秒时间戳) - 默认显示的日期
minDate (Date对象或毫秒时间戳) - 可选的最小日期
maxDate (Date对象或毫秒时间戳) - 可选的最大日期
在用户选好日期后返回一个Promise，回调参数为一个对象，其中包含有action, year, month (0-11), day。如果用户取消了对话框，Promise仍然会执行，返回的action为DatePickerAndroid.dismissedAction，其他几项参数则为undefined。所以请在使用其他值之前务必先检查action的值。

注意：当Android手机操作系统低于5.0时，设置最小和最大日期会导致api异常，最好不要设置，而是在用户选择完成后再进行检查；api中的Open函数打开的界面是系统的界面，不能设置其任何显示样式，如何手机显示不同是因为系统被厂商深度定制了

TimePickerAndroid：

static open(options: Object)

打开一个标准的Android时间选择器的对话框。

可选的options对象的key值如下：

hour (0-23) - 要显示的小时，默认为当前时间。
minute (0-59) - 要显示的分钟，默认为当前时间。
is24Hour (boolean) - 如果设为true，则选择器会使用24小时制。如果设为false，则会额外显示AM/PM的选项。如果不设定，则采取当前地区的默认设置。
在用户选好时间后返回一个Promise，回调参数为一个对象，其中包含有action, hour (0-23), minute (0-59)。如果用户取消了对话框，Promise仍然会执行，返回的action为TimePickerAndroid.dismissedAction，其他几项参数则为undefined。所以请在使用其他值之前务必先检查action的值。一般用TimePickerAndroid.timeSetAction的取反来判断

注意：is24Hour在某些手机上不会产生作用，用户没有选择时间是因为按下了返回键或取消键；同样的api中的Open打开的是系统的界面



#42、React Native IOS日期时间组件DatePickerIOS
 
nuclide代码自动补全提示的插件：
atom-react-native-css atom-react-native-autocomplete

nuclide自动保存代码的插件：
autosave 需要setting enable


日期时间选择器 在IOS中是以组件的形式 DatePickerIOS支持View组件的所有属性，可以设置他的宽度、高度、位置等

这是一个受约束的(Controlled)组件，所以你必须监听onDateChange回调函数并且及时更新date属性来使得组件更新，否则用户的修改会立刻被撤销来确保当前显示值和props.date一致。

除了View组件的属性，DatePickerIOS组件还支持如下属性：

date 当前被选中的日期和时间 Date类型

maximumDate minimumDate

minuteInterval (1, 2, 3, 4, 5, 6, 10, 12, 15, 20, 30)
用来设置可选的最小分钟单位

mode ('date', 'time', 'datetime') 选择器模式

onDateChange 当用户修改日期或时间时调用此回调函数。
唯一的参数是一个Date对象，表示新的日期和时间（也就是用户选择的）

timeZoneOffsetInMinutes 以分钟为单位的时区时间差 默认情况下，选择器会选择设备的默认时区。通过此参数，可以指定一个时区。举个例子，要使用北京时间（东八区），可以传递8 * 60。

注意：必须要把一个日期类型的状态机变量赋值给DatePickerIOS组件的date属性，并且在用户操作DatePickerIOS组件修改后，用onDateChange回调的新的date去更新对应的状态机变量，否则会出现用户使用DatePickerIOS组件修改改了时间，几秒钟后，DatePickerIOS组件又回到了原来的时间的情况。

warning：Invalid prop 'date' of type 'Number'

warning：Required prop 'onDateChange' was not specified

警告的解决方案：

这是一个bug，升级到0.28即可，如果不想升级，可以照这个修改：

node_modules/react-native/Libraries/Components/DatePicker

https://github.com/facebook/react-native/commit/cec913e7ce05d26181ab4d46e2e41d72acdfb87d

http://stackoverflow.com/questions/35764088/prop-issues-with-datepickerios-in-react-native



#43、React Native API学习ActionSheetIOS

需求：分享和弹出多项选择操作！在IOS开发中，ActionSheet提供了这样的功能，而React Native同样封装了该功能，那就是ActionSheetIOS

提供了两个静态方法：

static showActionSheetWithOptions(options,callback):

在iOS设备上显示一个ActionSheet弹出框，其中options参数为一个对象，其属性必须包含以下一项或多项：

options（字符串数组） - 一组按钮的标题（必选）

cancelButtonIndex（整型） - 选项中取消按钮所在的位置（索引）

destructiveButtonIndex（整型） - 红色高亮显示的位置（索引）

title（字符串） - 弹出框顶部的标题

message（字符串） - 弹出框顶部标题下方的信息

static showShareActionSheetWithOptions(options,failureCallback,successCallback)：

在iOS设备上显示一个分享弹出框，其中options参数为一个对象，其属性必须包含以下一项或多项：

message（字符串） - 要分享的信息

url（字符串） - 要分享的URL地址

注：如果url指向本地文件，或者是一个base64编码的url，则会直接读取并分享相应的文件。你可以用这样的方式来分享图片、视频以及PDF文件等。


#44、React Native API学习-网络状态与数据交互

##先来看看Android原生的：
（安装最新版的AS）
地址（翻墙）：https://sites.google.com/a/android.com/tools/download/studio/canary/latest

Latest Android Studio Canary Build: 2.2 Preview 4

Windows（用迅雷下载）: https://dl.google.com/dl/android/studio/ide-zips/2.2.0.3/android-studio-ide-145.3001415-windows.zip (436.8 MB)
Mac: https://dl.google.com/dl/android/studio/ide-zips/2.2.0.3/android-studio-ide-145.3001415-mac.zip  (436.9 MB)
Linux:  https://dl.google.com/dl/android/studio/ide-zips/2.2.0.3/android-studio-ide-145.3001415-linux.zip  (436.4 MB) 

Android_SDK也得更新一下

这里有一个坑：用最新版的as去打开之前的项目，报错：Error:Could not find com.android.tools.build:gradle-core:2.2.0-alpha2

解决办法：复制旧版本的as中的2.2.0-alpha2到新版本as（有10几处地方），打开后会提示升级，升级到最新版本的alpha4

启用gradle_daemon加速器：https://docs.gradle.org/2.9/userguide/gradle_daemon.html

##网络连接状态NetInfo：

获取网络状态是异步的，使用了js的Promise机制

Android平台的网络连接类型状态如下:

1.NONE   设备没有网络连接

2.BLUETOOTH  蓝牙数据连接

3.DUMMY   虚拟数据连接

4.ETHERNET  以太网数据连接

5.MOBILE  手机移动网络数据连接

6.MOBILE_DUN  拨号移动网络数据连接

7.MOBILE_HIPRI  高权限的移动网络数据连接

8.MOBILE_MMS   彩信移动网络数据连接

9.MOBILE_SUPL   SUP网络数据连接

10.VPN   虚拟网络连接 ，最低支持Android API 21版本

11.WIFI   无线网络连接

12.WIMAX   wimax网络连接

13.UNKNOWN  未知网络数据连接

根据文档说明:除此之外的其他一些网络连接状态已经被Android API隐藏了，但是我们可以在有需要的时候进行使用。

IOS平台的网络连接类型状态如下:

1.none   设备没有联网

2.wifi     设备联网并且是连接的wifi网络，或者当前是iOS模拟器

3.cell      设备联网是通过连接Edge,3G,WiMax或者LET网络

4.unknown  该检测发生异常错误或者网络状态无从知道

NetInfo有两个监听：

1.网络状态改变的监听 回调当前网络的状态

2.网络是否连接的监听 回调true或false

Android独有的特色：

1.NetInfo.isConnectionExpensive判断当前网络是否计费

2.AndroidManifest.xml文件中添加如下权限字段：(需视频演示)

<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

##数据交互（网络请求与响应）


IE中打开httpwatch的方法： shift+F2  Record Stop clear

通过http或https协议与网络服务器交互，react native集成了node-fetch包以支持开发者的这种需求

网络协议：http https

网络请求方法：get post 等 默认是get

1.GET使用URL或Cookie传参。而POST将数据放在BODY中。

2.GET的URL会有长度上的限制，则POST的数据则可以非常大。

3.POST比GET安全，因为数据在地址栏上不可见。

百度一下：不再以讹传讹，GET和POST的真正区别

建议：
1.get方式的安全性较Post方式要差些，包含机密信息的话，建议用Post数据提交方式；

2.在做数据查询时，建议用Get方式；而在做数据添加、修改或删除时，建议用Post方式；

准备需要传输的消息头：（标准消息头 自定义消息头）

React Native使用http协议框架支持Accept-Encoding: gzip, deflate格式编码，开发者不需要对此进行设置

自定义消息头可以在一些约定好的http消息头中填入身份认证信息

RN中的网络访问api：Fetch(推荐) XMLHttpRequest

fetch是一个更好的网络API，它由标准委员会提出，并已经在Chrome中实现。它在React Native中也默认可以使用。fetch的返回值是一个Promise对象，你可以用两种办法来使用它：1、使用then和catch指定回调函数 2、使用ES7的async/await语法来发起一个异步调用

  //如果你的服务器无法识别上面POST的数据格式，那么可以尝试传统的form格式
 map.body = 'username=13667377378&password=dfy889&act=signin';

    map.follow = 10;//设置请求允许的最大重定向次数，0为不允许重定向

    map.timeout = 8000;//设置超时时间，0为没有超时时间，这个值在重定向时会被重置

    map.size = 0;//设置请求回应中的消息体最大允许长度，0为没有限制

XMLHttpRequest的实现几乎跟Web一样，唯一的区别就是(安全机制)rn中的XMLHttpRequest不存在跨域的限制，而是作为全局api实现的，你可以访问任何网站。但是，XMLHttpRequest基于iOS网络的

let request=new XMLHttpRequest();
    request.onreadystatechange= (e)=>{
      if(request.readyState!==4){
        return ;
      }
      if(request.status===200){
        alert(request.resonsesText);
      }else{
        alert('出错啦');
      }

    };
    request.open('GET','http://www.reactnative.vip/');
    request.send();



#45、React Native API学习CameraRoll

CameraRoll模块提供了对手机中保存的图片、视频文件进行遍历访问与操作。
提供两个静态方法

##static getPhotos(params: object) 

可以得到手机中所有的图片和视频（不仅仅是使用摄像头拍摄的照片、视频，还有各个应用自己下载到手机的图片与视频）

params：对象 一些筛选的规则 有4个成员变量

1.first 数值 希望获取多少张图片的信息

2.groupTypes 字符串 默认为SavedPhotos [Album All Event Faces Library PhotoStream] 仅支持IOS平台 用来指定获取图片或视频的类型

3.assetType 字符串 默认为Photos 表示只获取图片 [All Videos]

4.after 字符串 用来记录上一次获取图片的结束标志 方便可以接着上次的位置继续获取 它的值不能由开发者随意赋予，而是应当在上一次获取图片后保存其值。通常，在Android平台，一开始就给这个值为null，但是在IOS平台，设置为null会抛一个无法捕捉的异常，导致红屏。

返回一个带有图片标识符JSON对象的Promise



![X](http://image18-c.poco.cn/mypoco/myphoto/20160630/11/1735166522016063011073201.png?512x638_130)

注意：不管是android平台还是ios平台，得到的image对象，可以作为一个整体，传递给Image组件，用来显示图片 

可以分批次读取手机中的所有图片：监听ScrollView滑动到底部时，继续getPhotos，这时需要用after成员变量，递归调用getPhotos，当page_info.has_next_page为false时返回

CameralRoll在IOS平台中需要添加链接库才能运行，否则报错找不到api：

1.\node_modules\react-native\Libraries\CameraRoll下的Xcode项目文件RCTCameraRoll.xcodeproj拖动到当前Xcode项目的Libraries目录

2.选中当前项目，在右边选择Build Phases，点击打开子项目Link Binary With Libraris

3.打开第一步插入的RCTCameraRoll.xcodeproj，再打开它的子目录Products，将子目录下的libRCTCameraRoll.a文件拖到Link Binary With Libraris列表中

4.使用Xcode重新运行项目


##static saveImageWithTag(tag) 保存一个图片到相册

 tag 在安卓上，本参数是一个本地URI（是把本地的图片保存到相册中），例如"file:///sdcard/img.png".

在iOS设备上可能是以下之一：

1、本地URI  2、资源库的标签  3、非以上两种类型，表示图片数据将会存储在内存中（并且在本进程持续的时候一直会占用内存）。

返回一个Promise，操作成功时返回新的URI。



#46、React Native 开源组件react-native-camera

推荐一个跨平台的rn-camera-roll：https://www.npmjs.com/package/rn-camera-roll

A Camera component for React Native. Also supports barcode scanning!二维码扫描

原生Android Zxing google

npm install rnpm -g

rnpm link不是安装，而是添加原生依赖，对应的组件已经安装好了才能rnpm link

通过这个例子来理解下react native的架构：js环境 jsBridge native环境

业务逻辑是reactJs处理  ui用react写 但实际桥接成native

ref的两种属性：String属性 回调属性（组件render渲染完成后的回调）

官网：https://facebook.github.io/react/docs/more-about-refs.html#the-ref-callback-attribute

this callback will be executed immediately after the component is mounted（组件render之后DidMount之前）


#47、React Native API学习定时器与手机定位Geolocation

定时器API：setTimeout、setInterval、setImmediate、requestAnimationFrame 跟浏览器中的一致

setTimeout：设置定时任务，隔多久去执行

setInterval：设置循环执行的任务，每隔多久循环执行一次

setImmediate：设置立即执行的任务

requestAnimationFrame：用递归来设置动画；相对setTimeout(fn, 0)来说，有优势：能够在动画流刷新后执行，即上一个动画流会完整执行。

requestAnimationFrame(fn)和setTimeout(fn, 0)不同，前者会在每帧刷新之后执行一次，而后者则会尽可能快的执行（在iPhone5S上有可能每秒1000次以上）。

用js来实现动画，我们一般是借助setTimeout或setInterval这两个函数，css3动画出来后，我们又可以使用css3来实现动画了，而且性能和流畅度也得到了很大的提升。但是css3动画还是有不少局限性，比如不是所有属性都能参与动画、动画缓动效果太少、无法完全控制动画过程等等。所以有的时候我们还是不得不使用setTimeout或setInterval的方式来实现动画，可是setTimeout和setInterval有着严重的性能问题，虽然某些现代浏览器对这两函个数进行了一些优化，但还是无法跟css3的动画性能相提并论。这个时候，就该requestAnimationFrame出马了。requestAnimationFrame 是专门为实现高性能的帧动画而设计的一个API。

setImmediate则会在当前JavaScript执行块结束的时候执行，就在将要发送批量响应数据到原生之前。注意如果你在setImmediate的回调函数中又执行了setImmediate，它会紧接着立刻执行，而不会在调用之前等待原生代码。Promise的实现就使用了setImmediate来执行异步调用。

安装react-timer-mixin：npm i react-timer-mixin --save

注意：Mixin属于ES5语法（js的混合封装方法），对于ES6代码来说，无法直接使用Mixin。如果你的项目是用ES6代码编写，同时又使用了计时器，那么你只需铭记在unmount组件时清除所有用到的定时器，那么也可以实现和TimerMixin同样的效果。我们发现很多React Native应用发生致命错误（闪退）是与计时器有关。具体来说，是在某个组件被卸载（unmount）之后，计时器却仍然被激活。


使用moment.js轻松管理日期和时间：官网：http://momentjs.com/

安装monent（时间格式化）：npm i moment --save

moment().format('YYYY-MM-DD HH:mm:ss')：取当前时间并格式化

手机定位的api：Geolocation

提供四个静态方法：getCurrentPosition watchPosition clearWacth stopObserving

Android需要在清单文件(AndroidManifest.xml)中加权限：

<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>

IOS需要在Info.plist中增加NSLocationWhenInUseUsageDescription字段来启用定位功能。如果你使用react-native init创建项目，定位会被默认启用。

综合案例：TimerDemo



#48、React Native API学习PanResponder手势识别

这节课是PanResponder手势识别初探，高级部分放到vip专属课程里

PanResponder平底锅的响应者

PanResponder类可以将多点触摸操作协调成一个手势。它使得一个单点触摸可以接受更多的触摸操作，也可以用于识别简单的多点触摸手势。

RN框架底层的手势响应系统提供了响应处理器，PanResponder将这些手势响应处理器再次进行封装，以便开发者更容易对手势进行处理，更容易预测用户的手势，对每一个手势响应处理器，PanResponder除了为其提供代表触摸行为的原生事件外，还提供了一个新的手势状态对象用来详细描述手势的状态

PanResponder的基本思想是：监视屏幕上指定大小、位置的矩形区域，当用手指按压这个区域中的某点后，开发者会收到这个事件，当按压后拖动手指时，会收到手势引发的各类事件，当手指离开这个矩形区域时，开发者也会收到相应的事件

注意：开发者可以任意指定监视矩形区域的大小，但在这个区域里，只有第一个按下的事件会上报和继续监视处理，如果第一个手指按下还没有离开，接着第二个手指又来按下了，那么对第二个手指的各种触摸事件无法捕获

注意：开发者可以在屏幕上指定多个监视矩形区域，但是不能同时监视多个矩形区域的不同触摸事件

注意：监视区域会阻止被监视区域覆盖的组件接收触摸事件，比如监视区域覆盖了一个按钮，那么就无法通过按这个按钮来触发其对应的事件，只能在PanResponder监视器的事件处理中对触摸行为进行处理

利用PanResponder实现监视器有以下几个步骤：

1、指定监视区域

如果监视区域有多个，一定不能重叠，否则都失效

2、定义监视器相关变量

指向监视器的变量（必须有）、指向监视器监视区域的变量（可以有）、记录监视区域左上角顶点坐标的两个数值变量（可以有）、上一次触摸点的横纵坐标变量（可以有）

3、准备监视器的事件处理函数（有13个---高级课程会详叙）

4、建立监视器（PanResponder.create）

5、将监视器与监视区域关联 {...this.watcher.panHandlers}

实例：点击、拖动选择百分百参数  比如说播放器的音量大小

一个gestureState对象有如下的字段：

stateID - 触摸状态的ID。在屏幕上有至少一个触摸点的情况下，这个ID会一直有效。

moveX - 最近一次移动时的屏幕横坐标

moveY - 最近一次移动时的屏幕纵坐标

x0 - 当响应器产生时的屏幕坐标

y0 - 当响应器产生时的屏幕坐标

dx - 从触摸操作开始时的累计横向路程

dy - 从触摸操作开始时的累计纵向路程

vx - 当前的横向移动速度

vy - 当前的纵向移动速度

numberActiveTouches - 当前在屏幕上的有效触摸点的数量


#49、React Native 运行官方项目UIExplorer(Android&IOS)

马上就要进入vip专属课程了，我们用一个项目将之前讲的知识点串起来，适配Android与IOS！

地址：https://github.com/facebook/react-native/tree/master/Examples/UIExplorer

Android环境跑UIExplorer：

1.下载ReactNative项目 80M左右

git clone https://github.com/facebook/react-native.git

2.进入react-native目录 编译android项目

方式一：gradlew :Examples:UIExplorer:android:app:installDebug

会去下载gradle可能报错：java.net.SocketTimeoutException: Read timed out javax.net.ssl.SSLHandshakeException: Remote host clos
ed connection during handshake 这是网络问题引起 不用理 再一次运行gradlew命令 下载gradle比较慢 耐心等待即可

![gradlew](http://image18-c.poco.cn/mypoco/myphoto/20160710/15/17351665220160710151710035.png?670x168_130)

方式二：gradle :Examples:UIExplorer:android:app:installDebug

区别：Gradlew是包装器，自动下载包装里定义好的gradle 版本，保证编译环境统一，gradle 是用本地的gradle 如果是看过我的视频教程的就知道已经安装了gradle 在第11讲打包时

报错：ndk找不到 ndk-build binary cannot be found, check if you've set $ANDROID_NDK environment variable correctly or if ndk.dir is setup in local.properties

3.使用Android Studio安装配置ndk

可以配置ANDROID_NDK环境变量或者在react-native目录下新建文件local.properties（里面设置了sdk与ndk路径）

说到NDK开发，其实是为了有些时候为了项目需求需要调用底层的一些 C/C++ 的一些东西；另外就是为了效率更加高些；代码保护(apk的java层代码很容易被反编译，而C/C++库反汇难度较大)

打开项目结构Project Structure：sdk jdk ndk(没有就会提示下载) ，as安装的话会安装到sdk目录下的ndk-bundle文件夹里

下载地址（迅雷下载）：https://dl.google.com/android/repository/android-ndk-r12b-windows-x86_64.zip

下载地址（迅雷下载）：https://dl.google.com/android/repository/android-ndk-r10e-windows-x86_64.zip


Download https://downloads.sourceforge.net/project/boost/boost/1.57.0/boost_1_57_0.zip 放到目录\react-native\ReactAndroid\build\downloads

boost_1_57_0下载地址：https://yunpan.cn/cBBT7LTwhg77i  访问密码 f1e7

报错：Execution failed for task ':ReactAndroid:buildReactNdkLib'.
> Process 'command 'F:\Android_SDK\ndk-bundle\android-ndk-r12b\ndk-build.cmd'' finished with non-zero exit value 2  解决方案：修改ndk的版本为r10e，不能使用最新版r12b

4.BUILD SUCCESSFUL后开启packager服务器

打开./packager/packager.sh 闪退的问题  解决方案：在react-native目录下npm install 在打开./packager/packager.sh 启动packager服务

IOS环境跑UIExplorer：

直接用Xcode打开UIExplorer.xcodeproj即可

报错：packager抛出异常Error: Cannot find module 'chalk'

解决：ls-l 在cd react-native目录下 npm install chalk

npm install lodash  直接npm install 直到successful


#50、React Native 混合原生开发_RN调用原生方法的步骤

RN调用原生的方法，此讲适配Android原生与RN的混合开发，步骤如下：

1.用AS打开一个已存在的项目，在RN项目中选择android/build.gradle文件

2.在Android原生这边创建一个类继承ReactContextBaseJavaModule，这个类里面放我们需要被rn调用的方法，封装成了一个原生模块

3.在Android原生这边创建一个类实现接口ReactPackage包管理器，并把第二步创建的类加到原生模块(NativeModule)列表里

4.将第三步创建的包管理器添加到ReactPackage列表里（getPackages方法里）

5.在RN中去调用原生模块 添加NativeModules从react-native


报错： outDexFolder must be a folder 解决方法：不理它  或者 clean

报错：> Failed to create \android\app\buildintermediates\debug\merging 解决方法：不理它  或者 clean

报错：Could not delete path \android\app\build\generated\source\r\debug\com'.   解决方法：用AS build clean




#63、React Native API学习Linking跨app的通信方法_适配Android&IOS

Linking提供了一个通用的接口来与传入和传出的App链接进行交互。

方法：

1.addEventListener(url,func) 添加一个监听Linking变化的事件

2.removeEventListener(url,func) 删除一个事件监听

3.openURL(url) 尝试使用设备上已经安装的应用打开指定的url 

  http网址：http://www.reactnative.vip

  https网址：https://www.baidu.com

  发短信：smsto:13667377378

打电话：tel:13667377378

发邮件：mailto:309623978@qq.com

发位置：geo:37.484847,-122.148386 这个不一定看地图处理应用而定

打开其他应用监听的意图url

4.canOpenURL 判断设备上是否有已经安装的应用可以处理指定的URL 对于iOS 9以上版本，你还需要在Info.plist中添加LSApplicationQueriesSchemes字段

5.getInitialURL() 如果应用是被一个链接调起的，则会返回相应的链接地址。否则它会返回null。

注：如果要在Android上支持深度链接，请参阅http://developer.android.com/training/app-indexing/deep-linking.html#handling-intents

意图过滤器需要单独列出：

 <intent-filter>
        	<action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <!-- Accepts URIs that begin with "http://www.example.com/gizmos” -->
        <data android:scheme="dfy"
              android:host="reactnative.vip"
              android:pathPrefix="/data" />
        	</intent-filter>

能否通过adb启动activity：adb shell am start -n com.linkingdemo/.MainActivity

测试是否能用url的形式打开app对应的activity：adb shell am start -W -a android.intent.action.VIEW -d "dfy://reactnative.vip/data" com.linkingdemo

IOS

首先我们需要在AppDelegate.m文件中引入RCTLinkingManager.h头文件，那么就需要我们引入相关配置了，关于库的引入默认项目都默认已经配置好的，但是我们需要配置一个库头文件搜索路径







