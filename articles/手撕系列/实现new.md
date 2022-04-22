# 思路
首先我们要明确new这个关键字做了什么，它的功能是创建一个内置对象或者构造函数的实例。
明确以下几点：
1. 传入参数：myNew(Person, ....)
2. 返回的值: 一个对象，该对象拥有构造函数中定义的属性，并且__proto__指向构造函数的prototype

```js
// 定义自己的new
function myNew() {
    // 创建一个obj作为要返回的新对象
    let obj = new Object();
  
    // 从参数中取出构造函数
    let constructor = [].shift.call(arguments);
  
    // 将obj的原型对象指向构造函数的原型对象
    obj.__proto__ = constructor.prototype;
  
    // 调用构造函数，并存放返回结果，如果结果是一个新对象，则返回这个新对象，否则返回obj
    let res = constructor.call(obj, ...arguments);
    if (typeof res !== 'object') {
      return obj;
    } else {
      return res;
    }
  }

// 定义构造函数
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// 定义原型上的方法
Person.prototype.getName = function() {
  return this.name;
}

// 调用
let person1 = myNew(Person, 'Tom', 18);
console.log(person1); // Person { name: 'Tom', age: 18 }
console.log(person1.getName()); // 'Tom'
```