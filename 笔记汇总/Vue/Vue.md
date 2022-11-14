



一、Vue3基本指令

## 1. Mustache语法

```html
1. mustache的基本使用
<h2>
    {{message}}
</h2>
2. 表达式
<h2>
    {{counter + 10}}
    {{ message.split(" ").reverse() }}
</h2>
3. 调用函数/computed计算属性
<h2>
    {{getReverseMessage()}}
</h2>
4. 三元运算符
<h2>
    {{ isShow ? "hello" : ""}}
</h2>
```





## 2. v-once

```
只渲染一次，之后即使改变也不会更新
```

![image-20210811153530650](image/image-20210811153530650.png)





## 3. v-text

```html
与{{message}}效果一样 ，了解即可
<div v-text="message"></div>
```

![image-20210811153557343](image/image-20210811153557343.png)





## 4. v-html

```html
解析字符串中的html语言
<div v-html="message"></div>
```

![image-20210811153630721](image/image-20210811153630721.png)



## 5. v-pre

```html
不需要解析{{message}}时使用
```

![image-20210811153644631](image/image-20210811153644631.png)





## 6. v-cloak

```html
正式开发时一般不用，了解
```

![image-20210811153946258](image/image-20210811153946258.png)



# 二、Vue3基础语法

## 1. v-bind 绑定属性（:）

```html
动态绑定元素的某些属性
<template>
	<img v-bind:src="imgUrl">
    <a :href="link">百度一下</a>
</template>
```

![image-20210812133926012](image/image-20210812133926012.png)





### 1.1 基本使用

![image-20210812133952670](image/image-20210812133952670.png)





### 1.2 绑定class

![image-20210812135657264](image/image-20210812135657264.png)



#### ① 对象语法

```html
<div :class="{active: isActive, title:isTitle}">
    1111
</div>

<div :class="{classObj}">
    1111
</div>

data() {
	return {
		classObj: {
		active: true, 
		title: true	
		}
	}
}
```

![image-20210812135715226](image/image-20210812135715226.png)





#### ② 数组语法

```html
<div :class="['abc', title, {active: isActive}]">    1111</div>
```

![image-20210812135800993](image/image-20210812135800993.png)





### 1.3 绑定style

```html
<div :style="[style1Obj, style2Obj]">    hahaha</div>
```

![image-20210812142125082](image/image-20210812142125082.png)

![image-20210812143731674](image/image-20210812143731674.png)







### 1.4 动态绑定属性

```html
1. 属性名变成动态<div :[name]="value">    hhhh</div>data() {	return {		name: "aaaa",		value: "bbbb"	}}2. 直接绑定对象<div v-bind="info">    1111</div>data() {	return {		info: {			name: "cw",			age: 18		}	}}
```

![image-20210812143749351](image/image-20210812143749351.png)

![image-20210812143806480](../JavaScript/image-20210812143806480.png)





## 2. v-on  绑定事件

### 2.1  基本使用

```html
<button v-on:click="btn1Click" @mousemove="mouseMove">    按钮1</button>// 还绑定对象、绑定表达式，同v-bindmethods: {	btn1Click() {		console.log("button1点击");	}	mouseMove() {		console.log("move");	}}
```

![image-20210812151606691](image/image-20210812151606691.png)





### 2.2 参数传参

```

```

![image-20210812151618939](image/image-20210812151618939.png)





### 2.3 修饰符

![image-20210812152139308](image/image-20210812152139308.png)





## 3. v-if /v-show条件渲染

### 3.1 v-if

```html
<template>	<h2 v-if="score > 90">优秀</h2>    <h2 v-else-if="score > 60">及格</h2>    <h2 v-else>不及格</h2></template>
```

![image-20210812154157549](image/image-20210812154157549.png)





### 3.2 template配合使用

```html
<template id="my-app">	<template v-if="isShow">    	hhhh    </template>    <template v-else>    	ggg    </template></template>
```

![image-20210812155342213](image/image-20210812155342213.png)





### 3.3 v-show

```html
<template>	<h2 v-if="isShow">  // v-if 不会渲染        hhhh    </h2>    <h2 v-show="isShow"> // v-show 会渲染，只是被隐藏        ggg // 不支持 template 和 else    </h2></template>
```

![image-20210812155832958](image/image-20210812155832958.png)





## 4. v-for 列表渲染

### 4.1 基本使用

```vue
<template>	<ul>        // 遍历数组        <li v-for="item in movies">{{item}}</li>        <li v-for="(item, index) in movies">{{index+1}}.{{item}}</li>        // 遍历对象        <li v-for="item in videos">{{item}}</li>        <li v-for="(item, key) in videos">{{key}}-{{item}}</li>        // 遍历数字        <li v-for="num in 10">{{num}}</li>        <li v-for="(num, index) in 10">{{index}}-{{num}}</li>    </ul></template>data() {	return {		movies: [			"aaa",			"bbb",			"ccc"		],		videos: {			name: "aaa"		}	}}
```

![image-20210812161952719](image/image-20210812161952719.png)

![image-20210812162040287](image/image-20210812162040287.png)





### 4.2 template配合使用

```html

```

![image-20210812162054213](image/image-20210812162054213.png)





### 4.3 数组更新检测

![image-20210812162245282](image/image-20210812162245282.png)





### 4.4 绑定key

#### ① key的作用

![image-20210813135529644](image/image-20210813135529644.png)



#### ② VNode

![image-20210813140456695](image/image-20210813140456695.png)

![image-20210813140507725](image/image-20210813140507725.png)

#### ③ 没有Key的diff算法

![image-20210813154504047](image/image-20210813154504047.png)

#### ④ 有Key的diff算法

![image-20210813154619488](image/image-20210813154619488.png)

![image-20210813154627120](image/image-20210813154627120.png)

![image-20210813154656087](image/image-20210813154656087.png)









## 5. computed计算属性

### 5.1 概念

![image-20210814112842162](image/image-20210814112842162.png)





### 5.2  使用案例

![image-20210814112929278](image/image-20210814112929278.png)





### 5.2 computed 对比 methods

![image-20210814113837128](image/image-20210814113837128.png)

![image-20210814115617633](image/image-20210814115617633.png)

![image-20210814115631414](image/image-20210814115631414.png)

![image-20210814123746195](image/image-20210814123746195.png)

## 





## 6. 侦听器watch

### 6.1 基本使用

![image-20210814125440912](image/image-20210814125440912.png)

![image-20210815100307757](image/image-20210815100307757.png)





### 6.2 侦听器的配置选项

![image-20210815102528581](image/image-20210815102528581.png)

![image-20210815102543480](image/image-20210815102543480.png)





### 6.3 其他方法

![image-20210815103403196](image/image-20210815103403196.png)

![image-20210815103414576](image/image-20210815103414576.png)





## 7. v-model 双向数据绑定

### 7.1 基本使用

![image-20210815155838512](image/image-20210815155838512.png)





### 7.2 原理

![image-20210815160424972](image/image-20210815160424972.png)





### 7.3 绑定各类元素

#### ① textarea

![image-20210815161339182](image/image-20210815161339182.png)





#### ② checkbox

![image-20210815161400917](image/image-20210815161400917.png)





#### ③ radio

![image-20210815161450440](image/image-20210815161450440.png)





#### ④ select

![image-20210815161509261](image/image-20210815161509261.png)





### 7.4 值绑定

![image-20210815161548159](image/image-20210815161548159.png)





### 7.5 修饰符

#### ① lazy

![image-20210815164728994](image/image-20210815164728994.png)





#### ② number

![image-20210815164805382](image/image-20210815164805382.png)





#### ③ trim

![image-20210815164856296](image/image-20210815164856296.png)







# 三、组件化开发

## 1. 注册组件

### 1.1 全局组件

![image-20210817145501862](image/image-20210817145501862.png)



### 1.2 局部组件

![image-20210817152029295](image/image-20210817152029295.png)

![image-20210817152041196](image/image-20210817152041196.png)





### 1.3 组件名称

![image-20210817151016916](image/image-20210817151016916.png)





## 2. Vue的开发模式

![image-20210817152940047](image/image-20210817152940047.png)

![image-20210817153014489](image/image-20210817153014489.png)

![image-20210817153025245](image/image-20210817153025245.png)



## 3. 组件的拆分和嵌套

### 3.1 组件的嵌套

![image-20210824172108059](image/image-20210824172108059.png)

### 3.2 组件的拆分

![image-20210824172345273](image/image-20210824172345273.png)





## 4. 组件的CSS作用域

```vue
<template>	<div class= "any">        套一个div给一个class    </div></template>
```



## 5. 组件的通信

### 5.1 父子组件的通信

#### ① 父 => 子 （ props）

![image-20210825143812447](image/image-20210825143812447.png)

##### （1）数组用法

![image-20210825145106628](image/image-20210825145106628.png)

##### （2）对象用法

![image-20210825145122632](image/image-20210825145122632.png)

![image-20210825145954200](image/image-20210825145954200.png)

<img src="image/image-20210825150005114.png" alt="image-20210825150005114" style="zoom:25%;" />

![image-20210825150737319](image/image-20210825150737319.png)

##### （3）非props的attribute

![image-20210825151313642](image/image-20210825151313642.png)

![image-20210825151326114](image/image-20210825151326114.png)





#### ② 子 => 父（emits）

![image-20210825152909005](image/image-20210825152909005.png)

![image-20210825155018662](image/image-20210825155018662.png)



### 5.2  非父子组件的通信

#### ① Provide/Inject

##### （1）基本用法

![image-20210826160815676](image/image-20210826160815676.png)

![image-20210826161134340](image/image-20210826161134340.png)

##### （2）函数写法（this）

![image-20210826161237871](image/image-20210826161237871.png)

##### （3）处理响应式数据

![image-20210827105921971](image/image-20210827105921971.png)

![image-20210827100731928](image/image-20210827100731928.png)





#### ② Mitt全局事件总线

![image-20210827150316165](image/image-20210827150316165.png)

![image-20210827150823597](image/image-20210827150823597.png)

![image-20210827152619601](image/image-20210827152619601.png)





#### ③ slot插槽

##### （1）具名插槽和动态插槽

![image-20210827152712074](image/image-20210827152712074.png)

![image-20210827152804095](image/image-20210827152804095.png)

![image-20210827152819022](image/image-20210827152819022.png)

![image-20210827153454597](image/image-20210827153454597.png)

![image-20210827153703554](image/image-20210827153703554.png)

![image-20210827153728218](image/image-20210827153728218.png)

![image-20210827153832808](image/image-20210827153832808.png)

![image-20210827153849031](image/image-20210827153849031.png)



##### （2）作用域插槽

![image-20210827162109166](image/image-20210827162109166.png)

![image-20210827162120967](image/image-20210827162120967.png)

![image-20210827162138988](image/image-20210827162138988.png)

![image-20210827162152533](image/image-20210827162152533.png)

![image-20210827162641601](image/image-20210827162641601.png)

![image-20210827162706926](image/image-20210827162706926.png)





## 6. 动态组件

### 6.1 动态组件的实现

![image-20210830105931814](image/image-20210830105931814.png)



### 6.2 动态组件的传参

![image-20210830105950249](image/image-20210830105950249.png)



## 7. keep-alive

### 7.1 认识

![image-20210830110052334](image/image-20210830110052334.png)



### 7.2 属性

![image-20210830110123972](image/image-20210830110123972.png)



### 7.3 缓存组件的生命周期

![image-20210830110218242](image/image-20210830110218242.png)



## 8. webpack的代码分包

![image-20210830110324135](image/image-20210830110324135.png)



## 9. Vue中实现异步组件

### 9.1 写法一

![image-20210830112711842](image/image-20210830112711842.png)



### 9.2 写法二

![image-20210830112735819](image/image-20210830112735819.png)



### 9.3 异步组件和Suspense

![image-20210830113008537](image/image-20210830113008537.png)



## 10. Vue生命周期

### 10.1 图示

![实例的生命周期](image/lifecycle.png)



### 10.2 认识

![image-20210830155440002](../JavaScript/image-20210830155440002.png)





### 10.3 缓存组件的生命周期

![image-20210830155636443](image/image-20210830155636443.png)



## 11. 组件的v-model

### 11.1 基本使用

![image-20210830160033067](image/image-20210830160033067.png)

![image-20210830160908621](image/image-20210830160908621.png)



### 11.2 computed实现

![image-20210830161332019](image/image-20210830161332019.png)

### 11.3 绑定多个属性

![image-20210830161536000](image/image-20210830161536000.png)





## # 其他知识点

###  1. $refs

![image-20210830114349630](image/image-20210830114349630.png)





### 2. $parent 和 $root

![image-20210830114435058](image/image-20210830114435058.png)









# 四、 Webpack

## 1. 概念

![image-20210817163623647](image/image-20210817163623647.png)





## 2. 基础

![image-20210818093437716](image/image-20210818093437716.png)

![image-20210818095750377](image/image-20210818095750377.png)

![image-20210818095811197](image/image-20210818095811197.png)

![image-20210818095831183](image/image-20210818095831183.png)





## 3. webpack-css

### 3.1 webpack依赖图

![image-20210818101956709](image/image-20210818101956709.png)

### 3.2 css-loader的使用

![image-20210818144353689](image/image-20210818144353689.png)



#### ① 内联式

![image-20210818145431377](image/image-20210818145431377.png)



#### ② CLI方式

![image-20210818145451833](image/image-20210818145451833.png)



#### ③ 配置方式

![image-20210818145521169](image/image-20210818145521169.png)

![image-20210818150303970](image/image-20210818150303970.png)

### 3.3 style-loader使用

![image-20210818150625059](image/image-20210818150625059.png)

![image-20210818150639785](image/image-20210818150639785.png)

### 3.4 less文件的处理

![image-20210818150715212](image/image-20210818150715212.png)

![image-20210818150727343](image/image-20210818150727343.png)

![image-20210818150751547](image/image-20210818150751547.png)

### 3.5 PostCSS工具

![image-20210818152641591](image/image-20210818152641591.png)

![image-20210818152653317](image/image-20210818152653317.png)

![image-20210818152704055](image/image-20210818152704055.png)

![image-20210818152713240](image/image-20210818152713240.png)

![image-20210818152725331](image/image-20210818152725331.png)

![image-20210818152740704](image/image-20210818152740704.png)



## 4. webpack打包其他资源

### 4.1 打包图片 

#### ① file-loader

![image-20210823150352260](image/image-20210823150352260.png)

![image-20210823150424447](image/image-20210823150424447.png)

![image-20210823153440621](image/image-20210823153440621.png)

![image-20210823153450867](image/image-20210823153450867.png)

#### ② url-loarder

![image-20210823154120295](image/image-20210823154120295.png)

![image-20210823154131909](image/image-20210823154131909.png)





### 4.2 asset module type 

#### ① 认识与使用

![image-20210823154202274](image/image-20210823154202274.png)

![image-20210823154315053](image/image-20210823154315053.png)

![image-20210823154324771](image/image-20210823154324771.png)

#### ② 字体

![image-20210823154439446](image/image-20210823154439446.png)





### 4.3 Plugin

#### ① 认识与使用

![image-20210823154545364](image/image-20210823154545364.png)

![image-20210823154949317](image/image-20210823154949317.png)

![image-20210823155003408](image/image-20210823155003408.png)

![image-20210823155011679](image/image-20210823155011679.png)

![image-20210823155021904](image/image-20210823155021904.png)

![image-20210823155030037](image/image-20210823155030037.png)

![image-20210823155036954](image/image-20210823155036954.png)

![image-20210823155045107](image/image-20210823155045107.png)

![image-20210823155057347](image/image-20210823155057347.png)

![image-20210823155110813](image/image-20210823155110813.png)







## 5. babel

### 5.1 介绍

![image-20210823155700180](image/image-20210823155700180.png)

### 5.2 认识与使用

![image-20210823155854010](image/image-20210823155854010.png)

![image-20210823155906299](image/image-20210823155906299.png)

![image-20210823155916028](image/image-20210823155916028.png)

![image-20210823155932813](image/image-20210823155932813.png)

![image-20210823155953285](image/image-20210823155953285.png)

![image-20210823160052676](image/image-20210823160052676.png)

![image-20210823160059622](image/image-20210823160059622.png)

![image-20210823160111465](image/image-20210823160111465.png)

![image-20210823160126185](image/image-20210823160126185.png)







### 5.3 Vue源码的打包

![image-20210823160204682](image/image-20210823160204682.png)

![image-20210823160221638](image/image-20210823160221638.png)

![image-20210823160235360](image/image-20210823160235360.png)

![image-20210823160242544](image/image-20210823160242544.png)

![image-20210823160251966](image/image-20210823160251966.png)

![image-20210823160410107](image/image-20210823160410107.png)

![image-20210823160417884](image/image-20210823160417884.png)

![image-20210823160425078](image/image-20210823160425078.png)





### 5.4 搭建本地服务器

![image-20210823160443304](image/image-20210823160443304.png)

![image-20210823160452490](image/image-20210823160452490.png)

![image-20210823160501576](image/image-20210823160501576.png)

![image-20210823160553541](image/image-20210823160553541.png)

![image-20210823160602607](image/image-20210823160602607.png)

![image-20210823160614870](image/image-20210823160614870.png)

![image-20210823160622509](image/image-20210823160622509.png)

![image-20210823160647950](image/image-20210823160647950.png)

![image-20210823160655463](image/image-20210823160655463.png)

![image-20210823160706727](image/image-20210823160706727.png)

![image-20210823160715741](image/image-20210823160715741.png)

![image-20210823160724183](image/image-20210823160724183.png)

![image-20210823160731866](image/image-20210823160731866.png)

![image-20210823160742072](image/image-20210823160742072.png)

![image-20210823160816883](image/image-20210823160816883.png)

![image-20210823160833623](image/image-20210823160833623.png)

![image-20210823161209812](image/image-20210823161209812.png)

![image-20210823161215661](image/image-20210823161215661.png)

![image-20210823161222762](image/image-20210823161222762.png)









# 五、Vue CLI

## 1. 概念

![image-20210824153954474](image/image-20210824153954474.png)



## 2. 安装和使用

![image-20210824154020689](image/image-20210824154020689.png)

![image-20210824155523026](image/image-20210824155523026.png)

![image-20210824155916108](image/image-20210824155916108.png)





## 3. 运行原理

![image-20210824161442537](image/image-20210824161442537.png)







# 六、Vue3实现动画

## 1. 认识动画

![image-20210901142525937](image/image-20210901142525937.png)



## 2. transition动画

![image-20210901143006384](image/image-20210901143006384.png)



### 2.1. 原理

![image-20210901144215778](image/image-20210901144215778.png)



### 2.2. 过渡动画的class

![image-20210901144534538](image/image-20210901144534538.png)

![image-20210901144950745](image/image-20210901144950745.png)



### 2.3  animation帧动画

![image-20210901145516368](image/image-20210901145516368.png)

### 2.4 同时设置过渡和动画

#### ① type

![image-20210901150520180](image/image-20210901150520180.png)

#### ② duration

（以下较少使用）

![image-20210901153948662](image/image-20210901153948662.png)



### 2.5 过渡的模式mode

![image-20210901154135299](image/image-20210901154135299.png)



### 2.6 动态组件的切换

![image-20210901154255196](image/image-20210901154255196.png)

### 2.7 appear初次渲染

![image-20210901154330930](image/image-20210901154330930.png)



## 3. animate.css库

### 3.1 认识

![image-20210901155728176](image/image-20210901155728176.png)

### 3.2 自定义过渡class

![image-20210901155815224](image/image-20210901155815224.png)



### 3.3 使用

![image-20210901155830776](image/image-20210901155830776.png)



## 4. gasp库

### 4.1 认识

![image-20210901162357720](image/image-20210901162357720.png)



### 4.2 JavaScript钩子

![image-20210901162420795](image/image-20210901162420795.png)



### 4.3 使用

![image-20210901162451984](image/image-20210901162451984.png)





### 4.4 实现数字变化

![image-20210901162509057](image/image-20210901162509057.png)



## 5. 列表的过渡

### 5.1 认识

![image-20210903141514834](image/image-20210903141514834.png)



### 5.2 基本使用

![image-20210903143440828](image/image-20210903143440828.png)

![image-20210903143452355](image/image-20210903143452355.png)

![image-20210903143507708](image/image-20210903143507708.png)





# 七、Composition API

## 1. Mixin（vue2使用）

### 1.1 认识

![image-20210903150010996](image/image-20210903150010996.png)





### 1.2 基本使用

![image-20210903150846863](image/image-20210903150846863.png)



### 1.3 合并规则

![image-20210903151302342](image/image-20210903151302342.png)





### 1.4 全局混入

![image-20210903151626538](image/image-20210903151626538.png)





### 1.5 extends（不常用）

![image-20210903152134916](image/image-20210903152134916.png)



## 2. Options API弊端（vue2）

![image-20210903162934526](image/image-20210903162934526.png)

![image-20210903163435030](image/image-20210903163435030.png)



## 3. 认识Composition API

![image-20210903163853829](image/image-20210903163853829.png)



## 4. setup函数

### 4.1 参数

![image-20210904143239738](image/image-20210904143239738.png)



### 4.2 返回值

![image-20210904154030695](image/image-20210904154030695.png)



### 4.3 不能用 this

![image-20210906153730959](image/image-20210906153730959.png)



### 4.4 响应式数据 reactive

#### ① 认识

![image-20210906155812940](image/image-20210906155812940.png)



#### ② 判断API

![image-20210906165027938](image/image-20210906165027938.png)





### 4.5 ref API

#### ① 使用

![image-20210906160805681](image/image-20210906160805681.png)



#### ② 自动解包

![image-20210906161302432](image/image-20210906161302432.png)



#### ③ toRefs

![image-20210906172842662](image/image-20210906172842662.png)



#### ④ toRef

![image-20210906172901705](image/image-20210906172901705.png)



#### ⑤ Ref的其他API

![image-20210906172919299](image/image-20210906172919299.png)



#### ⑥ customRef

![image-20210906172947930](image/image-20210906172947930.png)

![image-20210909092528517](image/image-20210909092528517.png)

### 4.6 只读 readonly

#### ① 认识

![image-20210906161622064](image/image-20210906161622064.png)





#### ② 使用

![image-20210906161642583](image/image-20210906161642583.png)



#### ③ 应用

![image-20210906161700452](image/image-20210906161700452.png)





### 4.7. computed 计算属性

![image-20210909105049213](image/image-20210909105049213.png)





### 4.8 侦听数据的变化

![image-20210909142707518](image/image-20210909142707518.png)



#### ① watchEffect

##### · 使用

![image-20210909142744116](image/image-20210909142744116.png)

##### · 停止侦听

![image-20210909143428308](image/image-20210909143428308.png)

##### · 清除副作用

![image-20210909143508642](image/image-20210909143508642.png)

##### · setup中使用ref

![image-20210909152525692](image/image-20210909152525692.png)

##### · watchEffect执行时机

![image-20210909152722447](image/image-20210909152722447.png)

![image-20210909154533191](image/image-20210909154533191.png)





#### ② Watch

##### · 使用

![image-20210909154602183](image/image-20210909154602183.png)



##### · 侦听单个数据源

![image-20210909154819392](image/image-20210909154819392.png)



##### · 侦听多个数据源

![image-20210909154840255](image/image-20210909154840255.png)



##### · 侦听响应式对象

![image-20210909154855040](image/image-20210909154855040.png)



##### · watch的选项

![image-20210909154928838](image/image-20210909154928838.png)



### 4.9 生命周期钩子

![image-20210909161556307](image/image-20210909161556307.png)



### 4.10 Provide、Inject

![image-20210909162706499](image/image-20210909162706499.png)

![image-20210909162720913](image/image-20210909162720913.png)

![image-20210909162851485](image/image-20210909162851485.png)

![image-20210909162904196](image/image-20210909162904196.png)

### 



### 4.11 封装hook案例

#### ① useCounter

![image-20210909170503489](image/image-20210909170503489.png)

#### ② useTitle

![image-20210909170511736](image/image-20210909170511736.png)

#### ③ useScrollPosition

![image-20210909170625355](image/image-20210909170625355.png)

#### ④ useMousePosition

![image-20210909170647135](image/image-20210909170647135.png)

#### ⑤ useLocalStorage

![image-20210909170706113](image/image-20210909170706113.png)



## 5. h函数

### 5.1 认识

![image-20210910145633824](image/image-20210910145633824.png)



### 5.2 使用

#### ① 基本使用

![image-20210910145958986](image/image-20210910145958986.png)

![image-20210910150830034](image/image-20210910150830034.png)

![image-20210910150845238](image/image-20210910150845238.png)



#### ② 组件和插槽的使用

![image-20210910152347527](image/image-20210910152347527.png)



## 6. jsx

### 6.1 配置

![image-20210910152850767](image/image-20210910152850767.png)



### 6.2 使用

![image-20210910152929271](image/image-20210910152929271.png)



### 6.3 组件的使用

![image-20210910153008291](image/image-20210910153008291.png)



## 7. 自定义指令

### 7.1 认识

![image-20210910154252923](image/image-20210910154252923.png)



### 7.2 实现方式

#### ① 默认实现

![image-20210910154808887](image/image-20210910154808887.png)



#### ② 局部自定义指令

![image-20210910155113777](image/image-20210910155113777.png)



#### ③ 自定义全局指令

![image-20210910155818790](image/image-20210910155818790.png)



### 7.3 指令的生命周期

![image-20210910155858057](image/image-20210910155858057.png)



### 7.4 指令的参数和修饰符

![image-20210910160701367](image/image-20210910160701367.png)



### 7.5 时间戳案例

![image-20210910162657714](image/image-20210910162657714.png)

![image-20210910162708015](image/image-20210910162708015.png)



## 8. Teleport

### 8.1 认识

![image-20210911142338437](image/image-20210911142338437.png)



### 8.2 使用

![image-20210911143113707](image/image-20210911143113707.png)

![image-20210911143124960](image/image-20210911143124960.png)

![image-20210911143133273](image/image-20210911143133273.png)



## 9. 认识Vue插件

![image-20210911143346851](image/image-20210911143346851.png)

![image-20210911143357443](image/image-20210911143357443.png)





# 八、Vue3源码学习

## 1. DOM渲染对比

### 1.1 真实的DOM渲染

![image-20210911145759641](image/image-20210911145759641.png)



### 1.2 虚拟DOM渲染

#### ① 优势

![image-20210911151004716](image/image-20210911151004716.png)



#### ② 渲染过程

![image-20210911151024833](image/image-20210911151024833.png)





## 2. 三大核心系统

### 2.1 认识

![image-20210911151311847](image/image-20210911151311847.png)



### 2.2 协同工作

![image-20210911153409834](image/image-20210911153409834.png)



## 3. 实现Mini-Vue

![image-20210911154817674](image/image-20210911154817674.png)

### 3.1 渲染系统实现

![image-20210911154808677](image/image-20210911154808677.png)



#### ① h函数

![image-20210911161115087](image/image-20210911161115087.png)

#### ② Mount函数

![image-20210911161123988](image/image-20210911161123988.png)



#### ③ patch函数

![image-20210913100332205](image/image-20210913100332205.png)

![image-20210913100342177](image/image-20210913100342177.png)



### 3.2 响应式系统实现

#### ① 依赖收集系统

![image-20210916102657093](image/image-20210916102657093.png)



#### ② Vue2实现响应式

![image-20210916102719617](image/image-20210916102719617.png)



#### ③ Vue3实现响应式

![image-20210916102739807](image/image-20210916102739807.png)

![image-20210916102849630](image/image-20210916102849630.png)



### 3.3 框架外层API设计

#### ① createApp

![image-20210917143638694](image/image-20210917143638694.png)



## （未完待续）



# 九、VueRouter

## 1. 认识路由

### 1.1 前端路由

![image-20210917150659187](image/image-20210917150659187.png)



### 1.2 后端路由

![image-20210917150720511](image/image-20210917150720511.png)



### 1.3 前后端分离

![image-20210917151623091](image/image-20210917151623091.png)



### 1.4 SPA（Single Page Application）



## 2. URL的hash

![image-20210917153645074](image/image-20210917153645074.png)



## 3. History （H5）

![image-20210918162016684](image/image-20210918162016684.png)



![image-20210918162030866](image/image-20210918162030866.png)



## 4. 认识 vue-router

![image-20210927195058648](image/image-20210927195058648.png)



## 5. 路由的使用

### 5.1 使用步骤

![image-20210927202826504](image/image-20210927202826504.png)



### 5.2 基本使用流程

![image-20210927203451950](image/image-20210927203451950.png)



### 5.3 路由的默认路径

![image-20210927204023002](image/image-20210927204023002.png)



### 5.4 路由的history模式

![image-20210927204125565](image/image-20210927204125565.png)



### 5.5 router-link

![image-20210927205032587](image/image-20210927205032587.png)



### 5.6 路由懒加载

![image-20210927205737596](image/image-20210927205737596.png)

自定义打包名：

![image-20210927213717228](image/image-20210927213717228.png)



### 5.7 路由的其他属性

![image-20210927233237744](image/image-20210927233237744.png)



### 5.8 动态路由匹配

![image-20210927233259784](image/image-20210927233259784.png)

![image-20210927234356896](image/image-20210927234356896.png)

![image-20210927234405634](image/image-20210927234405634.png)



### 5.9 Not Found

![image-20210928232936912](image/image-20210928232936912.png)

![image-20210928234239421](image/image-20210928234239421.png)





## 6. 路由的嵌套

### 6.1 认识

![image-20210928234253716](image/image-20210928234253716.png)



### 6.2 配置

![image-20210928234333454](image/image-20210928234333454.png)



### 6.3 代码的页面跳转（编程式）

![image-20210928234400489](image/image-20210928234400489.png)

### 

### 6.4 query传参

![image-20210929000213809](image/image-20210929000213809.png)



### 6.5 页面的其他操作

![image-20210929001654113](image/image-20210929001654113.png)

![image-20210929001724062](image/image-20210929001724062.png)





## 7. router-link的v-slot

![image-20210929001754058](image/image-20210929001754058.png)

![image-20210929003928487](image/image-20210929003928487.png)



## 8. 动态添加路由

![image-20211002150304058](image/image-20211002150304058.png)



## 9. 动态删除路由

![image-20211002153141866](image/image-20211002153141866.png)



## 10. 路由导航守卫

![image-20211002153731661](image/image-20211002153731661.png)

![image-20211002155433912](image/image-20211002155433912.png)



## 11. 其他导航守卫

![image-20211002155454253](image/image-20211002155454253.png)







# 十、Vuex

## 1. 认识

### 1.1 状态管理

![image-20211011191907483](image/image-20211011191907483.png)

![image-20211011192107656](image/image-20211011192107656.png)



### 1.2  Vuex的状态管理

![image-20211011193401061](image/image-20211011193401061.png)

![image-20211011193411237](image/image-20211011193411237.png)



## 2. Vue devtool

![image-20211011194138212](image/image-20211011194138212.png)

![image-20211011194149625](image/image-20211011194149625.png)



## 3. Vuex的使用

### 3.1 安装

![image-20211011205021036](image/image-20211011205021036.png)

![image-20211011205238637](image/image-20211011205238637.png)

![image-20211011205544652](image/image-20211011205544652.png)

![image-20211011205837464](image/image-20211011205837464.png)

### 3.2  创建store

![image-20211011220319723](image/image-20211011220319723.png)

![image-20211011220335602](image/image-20211011220335602.png)



### 3.3 单一状态树

![image-20211011221026531](image/image-20211011221026531.png)



### 3.4 组件获取状态

![image-20211011221607829](image/image-20211011221607829.png)



### 3.5 使用mapState

#### ① 在computed中使用

![image-20211011222908077](image/image-20211011222908077.png)



#### ② 在setup中使用

![image-20211011222312275](image/image-20211011222312275.png)

####  ③ 封装为单独文件

![image-20211015151942159](image/image-20211015151942159.png)

### 3.6 getters

#### ① 基本使用

![image-20211015155521301](image/image-20211015155521301.png)



#### ② 第二个参数

![image-20211015155539118](image/image-20211015155539118.png)



#### ③ 返回函数

![image-20211015160949600](image/image-20211015160949600.png)



#### ④ mapGetters辅助函数

![image-20211018135124396](image/image-20211018135124396.png)



### 3.7  Mutation

#### ① 基本使用

![image-20211018135853099](image/image-20211018135853099.png)



#### ② 携带数据

![image-20211018135911001](image/image-20211018135911001.png)



#### ③ 常量类型

![image-20211018140855111](image/image-20211018140855111.png)



#### ④ mapMutation辅助函数

![image-20211018141143713](image/image-20211018141143713.png)



#### ⑤ 重要原则

![image-20211018141728462](image/image-20211018141728462.png)





### 3.8 actions

#### ① 基本使用

![image-20211018141807672](image/image-20211018141807672.png)

#### 

#### ② 分发操作

![image-20211018153612976](image/image-20211018153612976.png)

#### ③ 辅助函数

![image-20211105164203732](image/image-20211105164203732.png)



#### ④ 异步操作

![image-20211105164238013](image/image-20211105164238013.png)



### 3.9 module的基本使用

![image-20211105164604129](image/image-20211105164604129.png)



#### ① 局部状态

![image-20211105164745718](image/image-20211105164745718.png)



#### ② 命名空间

![image-20211105165404908](image/image-20211105165404908.png)



#### ③ 修改或派发根组件

![image-20211105165459583](image/image-20211105165459583.png)



#### ④ 辅助函数

![image-20211105165538140](image/image-20211105165538140.png)

![image-20211105165716576](image/image-20211105165716576.png)



# 十一、Typescript

## 1. 安装

![image-20211105171129429](image/image-20211105171129429.png)

![image-20211105171148334](image/image-20211105171148334.png)

![image-20211105171430088](image/image-20211105171430088.png)



## 2. 变量

### 2.1 变量的声明

![image-20211105171837555](image/image-20211105171837555.png)



### 2.2 声明变量的关键字

![image-20211105172312936](image/image-20211105172312936.png)



### 2.3 变量的类型推导

![image-20211105172356089](image/image-20211105172356089.png)

### 2.4 各种类型

#### ① number

![image-20211105172540302](image/image-20211105172540302.png)



#### ② boolean

![image-20211105172628520](image/image-20211105172628520.png)



#### ③ string

![image-20211105172711319](image/image-20211105172711319.png)



#### ④ Array

![image-20211105172934563](image/image-20211105172934563.png)



#### ⑤ object

![image-20211105173143807](image/image-20211105173143807.png)



#### ⑥ Symbol

![image-20211105173449705](image/image-20211105173449705.png)



#### ⑦ null和undefined

![image-20211105173734229](image/image-20211105173734229.png)



#### ⑧ any

![image-20211105173801884](image/image-20211105173801884.png)



#### ⑨ unknown

![image-20211106142758763](image/image-20211106142758763.png)



#### ⑩ void

![image-20211106143021642](image/image-20211106143021642.png)



#### 11 never

![image-20211106143316616](image/image-20211106143316616.png)



#### 12 tuple

![image-20211106143408509](image/image-20211106143408509.png)

![image-20211106143740224](image/image-20211106143740224.png)



## 3. 函数

### 3.1 类型

#### ① 参数类型

![image-20211106144204408](image/image-20211106144204408.png)



#### ② 返回值类型

![image-20211106144442503](image/image-20211106144442503.png)



#### ③ 匿名函数的参数

![image-20211106145147165](image/image-20211106145147165.png)



#### ④ 对象类型

![image-20211106145224098](image/image-20211106145224098.png)



#### ⑤ 可选类型

![image-20211106145608387](image/image-20211106145608387.png)

![image-20211107131854098](image/image-20211107131854098.png)

#### ⑥ 联合类型

![image-20211107131732998](image/image-20211107131732998.png)

![image-20211107131811652](image/image-20211107131811652.png)



### 3.2 类型别名 type

![image-20211107132319241](image/image-20211107132319241.png)



### 3.3 类型断言 as ...

![image-20211107132404521](image/image-20211107132404521.png)

![image-20211107132500982](image/image-20211107132500982.png)



### 3.4 可选链 ？

![image-20211107133452232](image/image-20211107133452232.png)



### 3.5  符号 ？？和 ！！

![image-20211107133553701](image/image-20211107133553701.png)



### 3.6 字面量类型

![image-20211107133756266](image/image-20211107133756266.png)



### 3.7 字面量推理

![image-20211107134340926](image/image-20211107134340926.png)



### 3.8 类型缩小

#### ① 认识

![image-20211107134819202](image/image-20211107134819202.png)



#### ② typeof

![image-20211107135533797](image/image-20211107135533797.png)



#### ③ 平等缩小

![image-20211107135613838](image/image-20211107135613838.png)



#### ④ instanceof

![image-20211107135709648](image/image-20211107135709648.png)



#### ⑤ in

![image-20211107135905462](image/image-20211107135905462.png)



### 3.9 TS函数类型

![image-20211107140259974](image/image-20211107140259974.png)

![image-20211107140450871](image/image-20211107140450871.png)



### 3.10 参数

#### ① 参数的可选类型

![image-20211107140638045](image/image-20211107140638045.png)



#### ② 默认参数

![image-20211107141947558](image/image-20211107141947558.png)



#### ③ 剩余参数

![image-20211107142008453](image/image-20211107142008453.png)



### 3.11 this类型

#### ① 可推导的this类型

![image-20211107142137543](image/image-20211107142137543.png)



#### ② 不确定的this类型

![image-20211107142717928](image/image-20211107142717928.png)



#### ③ 指定this的类型

![image-20211107142814011](image/image-20211107142814011.png)



### 3.12 函数重载

#### ① 认识

![image-20211107142849953](image/image-20211107142849953.png)



#### ② sum函数例子

![image-20211107143019963](image/image-20211107143019963.png)



#### ③ 联合类型和重载

![image-20211107143056904](image/image-20211107143056904.png)









## 4. 类 class

### 4.1 认识类

![image-20211107143256684](image/image-20211107143256684.png)



### 4.2 类的定义

![image-20211107143319139](image/image-20211107143319139.png)



### 4.3 类的继承

![image-20211107143814152](image/image-20211107143814152.png)



### 4.4 成员修饰符

![image-20211107144126802](image/image-20211107144126802.png)



### 4.5 只读属性readonly

![image-20211107144508171](image/image-20211107144508171.png)



### 4.6 getters  /  setters 存取器

![image-20211107144802826](image/image-20211107144802826.png)



### 4.7 静态成员

![image-20211107145107132](image/image-20211107145107132.png)



### 4.8 抽象类 abstract

![image-20211107145232366](image/image-20211107145232366.png)



### 4.9 类的类型

![image-20211107150442733](image/image-20211107150442733.png)



## 5. 接口 interface

### 5.1 声明

![image-20211107150713583](image/image-20211107150713583.png)



### 5.2 可选属性

![image-20211107150856458](image/image-20211107150856458.png)



### 5.3 只读属性

![image-20211107151137126](image/image-20211107151137126.png)



### 5.4 索引类型

![image-20211107151517184](image/image-20211107151517184.png)



### 5.5 函数类型 （少）

![image-20211107151826381](image/image-20211107151826381.png)



### 5.6 接口继承

![image-20211107151915878](image/image-20211107151915878.png)



### 5.7 接口的实现

![image-20211107152014820](image/image-20211107152014820.png)



### 5.8 interface 与 type 区别

![image-20211107152532654](image/image-20211107152532654.png)





### 5.9 交叉类型

![image-20211107152320985](image/image-20211107152320985.png)

![image-20211107152342725](image/image-20211107152342725.png)



### 5.10 字面量赋值

![image-20211107153027890](image/image-20211107153027890.png)









## 6. TS 枚举类型

### 6.1 认识

![image-20211107153740609](image/image-20211107153740609.png)



### 6.2 枚举类型的值

![image-20211107153912238](image/image-20211107153912238.png)



## 7. 泛型

### 7.1 认识

![image-20211108214325375](image/image-20211108214325375.png)



### 7.2 类型参数化

![image-20211108215440783](image/image-20211108215440783.png)

![image-20211108215722201](image/image-20211108215722201.png)



### 7.3 泛型接口

![image-20211108220244298](image/image-20211108220244298.png)



### 7.4 泛型类

![image-20211108220259569](image/image-20211108220259569.png)



### 7.5 泛型约束

![image-20211108220432383](image/image-20211108220432383.png)



## 8. 模块化开发

### 8.1 模块化

![image-20211108220700550](image/image-20211108220700550.png)



### 8.2 命名空间

![image-20211108220800201](image/image-20211108220800201.png)



## 9. 补充

### 9.1 类型的查找

![image-20211108221151701](image/image-20211108221151701.png)

#### ① 内置类型声明

![image-20211108221605310](image/image-20211108221605310.png)



#### ② 外部类型声明

![image-20211108221627239](image/image-20211108221627239.png)

#### ③ 自定义声明 declare

![image-20211108221759707](image/image-20211108221759707.png)

![image-20211108221831900](image/image-20211108221831900.png)

![image-20211108221842466](image/image-20211108221842466.png)

![image-20211108222005877](image/image-20211108222005877.png)



### 9.2 tsconfig.json文件

![image-20211108222047302](image/image-20211108222047302.png)

![image-20211108222123499](image/image-20211108222123499.png)



# 十二、项目搭建

## 1.axios相关

![image-20211114140013171](image/image-20211114140013171.png)

![image-20211114140027253](image/image-20211114140027253.png)

![image-20211114140036221](image/image-20211114140036221.png)



## 2. 区分不同环境

![image-20211114141241017](image/image-20211114141241017.png)



v
