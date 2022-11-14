# DOM

## console.dir() 打印元素对象

## 一、获取元素

### 1. getElementById('id') 

返回一个元素对象

### 2. getElementsByTagName(‘标签名’)

返回一个对象集合，以伪数组的形式存储

遍历：

```javascript
for(var i = 0; i< lis.length; i++){
	console.log(lis[i])
}
```

如果页面中只有一个，返回的仍是伪数组形式

如果页面中没有这个元素，则返回空的伪数组

采用指定元素：

```javascript
// 指定一个id= ol
var ol = document.getrElementById('ol');
console.log(ol.getElementsByTagName('li'))
```

### 3. getElementsByClassName('类名')    //(HTML5新增)

### 4. querySelector('选择器')

返回指定选择器的第一个元素对象

```javascript
<div class = "box"><div/>
var firstBox = document.querySelector('.box');

<div id = "nav">
var nav = document.querySelector('#nav');

<li> aaa </li>
var li = document.querySelector('li');
```

### 5. querySelectorAll('选择器')

返回指定选择器的所有元素对象

```javascript
var allBox = document.querySelectorAll('.box');
```

### 6. 获取特殊元素

#### ① body: document.body

```javascript
var bodyEle = document.body;
```

#### ② html: document.documentElement

```javascript
var html = document.documentElement;
```

## 二、事件基础

### 1. 事件三要素

![image-20210708164508917](image/image-20210708164508917.png)

### 2. 执行事件步骤

![image-20210708164820700](image/image-20210708164820700.png)

### 3. 常见事件

#### ① 鼠标事件

![image-20210708164758969](image/image-20210708164758969.png)

### 4. 操作元素

![image-20210708165528434](image/image-20210708165528434.png)

#### ① innerText（不推荐）和InnerHTML

innerText不识别html标签

innerHTML可以识别HTML标签   保留空格和换行

![image-20210708165952772](image/image-20210708165952772.png)

#### ② 修改元素属性

 ![image-20210708170549743](image/image-20210708170549743.png)

#### ③ 表单属性设置

![image-20210708171545152](image/image-20210708171545152.png)

##### 案例：仿京东切换明暗文

![image-20210708172834724](image/image-20210708172834724.png)

#### ④ 修改元素样式

![image-20210709102905283](image/image-20210709102905283.png)

##### 案例：循环精灵图

```javascript
'0 -44px'
'0 -++indexpx'
'0 -' + index + 'px';
```

![image-20210709104305621](image/image-20210709104305621.png)

##### 案例：显示隐藏文本框内容

![image-20210709105244563](image/image-20210709105244563.png)

##### 技巧： 利用className修改元素样式

![image-20210709105959291](image/image-20210709105959291.png)

##### 案例：密码框验证

![image-20210709145744812](image/image-20210709145744812.png)

#### ⑤ 排他思想（算法）

![image-20210709150556177](image/image-20210709150556177.png)

##### 案例：百度换肤

![image-20210709151252543](image/image-20210709151252543.png)

##### 案例：表格隔行变色

![image-20210709151853911](image/image-20210709151853911.png)

##### 案例：表单全选取消案例

![image-20210709152500260](image/image-20210709152500260.png)

![image-20210709153031432](image/image-20210709153031432.png)

#### ⑥ 自定义属性操作

##### 1. 获取属性

![image-20210709153540340](image/image-20210709153540340.png)

![image-20210709153555522](image/image-20210709153555522.png)

##### 2. 设置属性

![image-20210709153756274](image/image-20210709153756274.png)

![image-20210709153825771](image/image-20210709153825771.png)

##### 重点案例：tab栏切换

![image-20210709155311169](image/image-20210709155311169.png)

![image-20210709155401279](image/image-20210709155401279.png)

#### ⑦ H5自定义属性

![image-20210709155719080](image/image-20210709155719080.png)

![image-20210709160218932](image/image-20210709160218932.png)

![image-20210709160205142](image/image-20210709160205142.png)

### 5. 节点操作

#### ① 节点概述

![image-20210709160823588](image/image-20210709160823588.png)

#### ② 节点操作

##### 1. 节点层级

###### 1.1 父级节点![image-20210709161256370](image/image-20210709161256370.png)

![image-20210709161309819](image/image-20210709161309819.png)

###### 1.2 子节点

子节点

![image-20210709161700740](image/image-20210709161700740.png)

![image-20210709161808747](image/image-20210709161808747.png)

![image-20210709161850506](image/image-20210709161850506.png)

首部/尾部节点

![image-20210709162122632](image/image-20210709162122632.png)

![image-20210709162224944](image/image-20210709162224944.png)

![image-20210709162429912](image/image-20210709162429912.png)

###### 1.3  兄弟节点

![image-20210709163234109](image/image-20210709163234109.png)

![image-20210709163438087](image/image-20210709163438087.png)



##### 案例：下拉菜单

![image-20210709163025664](image/image-20210709163025664.png)

##### 2. 添加/创建节点

![image-20210709164045445](image/image-20210709164045445.png)

###### 2.1 创建节点

![image-20210709164111289](image/image-20210709164111289.png)

###### 2.2 添加节点

![image-20210709164017640](image/image-20210709164017640.png)

##### 案例：简单 发布留言

![image-20210709164704990](image/image-20210709164704990.png)

##### 3. 删除节点

![image-20210711141337148](image/image-20210711141337148.png)

![image-20210711141357912](image/image-20210711141357912.png)

##### 案例： 删除留言

![image-20210711142527749](image/image-20210711142527749.png)

##### 4. 克隆节点

![image-20210711143639035](image/image-20210711143639035.png)

![image-20210711143658241](image/image-20210711143658241.png)

##### 案例：动态生成表格

![image-20210711145128336](image/image-20210711145128336.png)

![image-20210711145054666](image/image-20210711145054666.png)

![image-20210711145752647](image/image-20210711145752647.png)

##### 5. 三种创建元素方式区别

###### 5.1 document.write()

![image-20210711150231342](image/image-20210711150231342.png)

![image-20210711150247221](image/image-20210711150247221.png)

###### 5.2 innerHTML

拼接多个字符串效率低 改用数组拼接

![image-20210711150813403](image/image-20210711150813403.png)

![image-20210711150903748](image/image-20210711150903748.png)

###### 5.3 document.createElement()

## 三、事件高级

### ① 注册事件（绑定事件）

##### 1. 传统方式

![image-20210711151423914](image/image-20210711151423914.png)

##### 2. 方法监听

![image-20210711151520742](image/image-20210711151520742.png)

![image-20210711151618082](image/image-20210711151618082.png)

![image-20210711151821592](image/image-20210711151821592.png)

### ② 删除事件

##### 1. 传统方式

![image-20210711152228575](image/image-20210711152228575.png)

##### 2. 方法监听

![image-20210711152642728](image/image-20210711152642728.png)

##### 3. 兼容性解决

![image-20210711152709750](image/image-20210711152709750.png)

### ③ DOM事件流

##### 1. 三个阶段

![image-20210711162117376](image/image-20210711162117376.png)

![image-20210711163024078](image/image-20210711163024078.png)

###### 1.1. 捕获阶段

![image-20210711163118402](image/image-20210711163118402.png)

###### 1.2. 当前目标阶段

###### 1.3. 冒泡阶段

![image-20210711163046351](image/image-20210711163046351.png)

##### 2. 事件对象

![image-20210711163809914](image/image-20210711163809914.png)

![image-20210711163529434](image/image-20210711163529434.png)

###### 2.1 常见事件对象属性和方法

![image-20210711164513151](image/image-20210711164513151.png)

1. e.target

![image-20210711164421423](image/image-20210711164421423.png)

2. e. preventDefault()

   ![image-20210711164756078](image/image-20210711164756078.png)

###### 2.2 阻止事件冒泡

![image-20210711165247997](image/image-20210711165247997.png)

###### 2.3 禁止选中文字和右键菜单

![image-20210712133156389](image/image-20210712133156389.png)

###### 2.4 获得鼠标坐标

![image-20210712133538830](image/image-20210712133538830.png)

![image-20210712134141587](image/image-20210712134141587.png)

###### 2.5 常用的键盘事件

![image-20210712135546034](image/image-20210712135546034.png)

![image-20210712135605113](image/image-20210712135605113.png)

###### 2.6 键盘事件对象

![image-20210712140213975](image/image-20210712140213975.png)

![image-20210712140257016](image/image-20210712140257016.png)

###### 案例：跟随鼠标的天使

![image-20210712134924571](image/image-20210712134924571.png)

###### 案例：按键后搜索框获得焦点

![image-20210712140850989](image/image-20210712140850989.png)

###### 案例：输入时在旁边显示放大的文本框

![image-20210712141708812](image/image-20210712141708812.png)

![image-20210712141502405](image/image-20210712141502405.png)

![image-20210712145952890](image/image-20210712145952890.png)

##### 3. 事件委托

![image-20210712132504410](image/image-20210712132504410.png)

###### 

![image-20210712132847200](image/image-20210712132847200.png)

