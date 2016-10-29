---
layout: post
title: RN系列教程(二)Image&&ScrollView
categories: [blog ]
tags: [React Native基础系列, ]
description: 
---

接下来，我们接着(一)继续讲，今天我们学习的是Image组件和ScrollView组件。  

###   Image组件  

Image:一个用于显示多种不同类型图片的React组件。那么要如何使用呢？  

引入本地图片:

	<Image source={require('../images/myHeader.png')}/>  
	
引入网络图片

	<Image style={styles.imageStyle} source={{uri: 'https://facebook.github.io/react/img/logo_og.png'}}/>  
	
这里要说的是加载网络图片的话，必须指定图片大小,例如logo_og.png，否则会遇到无法显示的问题，而引入本地图片的话,如果不指定图片的大小，那么默认的是图片的原大小，例如myHeader这张图片，大小为250 * 250，默认显示的是250 * 250.  
安卓和iOS的图片尺寸不一样，那么给图片命名为my-icon.android.png/my-icon.ios.png,系统会自动判断系统来加载图片.    

那么现在咱们来说一下Image的属性

```
	width:320,
    height:100,

    //cover:保持图片宽高放大显示图片，保证把Image填满，显示放大图片的中心
    //contain: 在保持图片宽高比的前提下缩放图片，完整显示图片，未填充的区域保留
    //stretch：拉伸图片,不维持宽高比，填满Image设置的大小。
    //repeat:类似于平铺效果
    resizeMode: 'cover',
    backgroundColor:'gray',
    // tintColor: 'red',为所有非透明的像素指定一个颜色
    // borderBottomLeftRadius ReactPropTypes.number
    // borderBottomRightRadius ReactPropTypes.number
    // borderColor color
    // borderRadius number
    // borderTopLeftRadius ReactPropTypes.number
    // borderTopRightRadius ReactPropTypes.number
    borderWidth: 2,//设置边框粗细程度
    borderColor: 'black',//设置边框颜色
    borderRadius: 30,//设置圆角大小，上面几个属性表示不同位置的圆角
    opacity: 0.5,//设置透明程度，1为完全不透明
    overflow: 'visible',//‘visible’,'hidden'当图片原始尺寸大于Image尺寸时，多余的部分是否可见
```  
![](http://upload-images.jianshu.io/upload_images/2781235-8b13f8245416db37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


###   ScrollView组件  

ScrollView必须有一个确定的高度才能正常使用，它实际上所做的就是将一系列不确定高度的子组件装进一个确定高度的容器,而这个容器就是ScrollView。    

contentContainerStyle StyleSheetPropType(ViewStylePropTypes) 
这些样式会应用到一个内层的内容容器上，所有的子视图都会包裹在内容容器内。  

	<ScrollView contentContainerStyle={styles.contentContainer}>
    </ScrollView>  
    
现在咱们来看一下它的常用属性和方法   
  
```
<ScrollView style={styles.scrollV}  
                    contentContainerStyle={styles.contentContainer}
                    horizontal={true}
                    keyboardDismissMode='none'
                    keyboardShouldPersistTaps={false}
                    onScroll={this._scroller}
                    >
          <Text>就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样就是这样</Text>
</ScrollView>
```  

上面的这个是横向滚动的    

horizontal:布尔值类型，当此属性为true的时候，所有的的子视图会在水平方向上排成一行，默认为false.   
 
keyboardDismissMode:用户拖拽滚动视图的时候，是否要隐藏软键盘，默认为不隐藏'none', "interactive", 'on-drag'    

keyboardShouldPersistTaps:当此属性为false的时候，在软键盘激活之后，点击焦点文本输入框以外的地方，键盘就会隐藏。如果为true，滚动视图不会响应点击.   
 
onContentSizeChange  function  该当滚动视图的内容尺寸大小发生变化的时候进行调用。    

onScroll  function  该方法在滚动的时候每frame(帧)调用一次。该方法事件调用的频率可以使用scrollEventThrottle属性进行设置。

```  
	_scroller(){
    console.log("横向滚动");
  }
```  

refreshControl   element 设置元素控件，该可以进行指定  

RefreshControl组件。这样可以为ScrollView添加下拉刷新的功能.这个咱们以后讲。    

showsHorizontalScrollIndicator:bool值是否显示一个水平方向的滚动条    

showsVerticalScrollIndicator :bool值是否显示一个竖直方向的滚动条    

以上是一些基础的属性，进阶的咱们后面再讲。   
 
下面是一些常用属性

```
scroller: {
    flex:1,
    margin:20,
    width: 300,
    backgroundColor :'white',
    borderWidth:2,
    borderColor:'black',
  },
  contentContainer: {
    shadowColor: 'red',//设置阴影颜色
    shadowOffset: {width:10,height:5},//设置阴影面积
    shadowOpacity: 1,//设置阴影的透明度
    shadowRadius: 20,//设置阴影的圆角
  },
```  

下周咱们接着说另外的控件。  
![](http://upload-images.jianshu.io/upload_images/2781235-c0bb3cb3d28e7ed2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


另外，本系列所有的源码都放在了我的github上：[https://github.com/Demon404/Honey](https://github.com/Demon404/Honey)
