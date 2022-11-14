# 一、基础类型

## 1. boolean

```typescript
let isDone: boolean = true
```



## 2. number

- number和js里一样是浮点数

```typescript
let decLiteral: number = 6; // 10进制
let hexLiteral: number = 0xf00d; // 16进制
let binaryLiteral: number = 0b1010; // 2进制
let octalLiteral: number = 0o744; // 8进制
```



## 3. string

```typescript
let message: string = 'hello'
```



## 4. Array

- 数组元素的类型必须一致

```typescript
// 表示一
let numbers: number[] = [1, 2, 3];
let messages: string[] = ['a','b', 'c'];

// 表示二
let numbers1: Array<number> = [1, 2, 3];
```



## 5. Tuple

- 表示已知元素数量和类型的数组

```typescript
let x: [string, number];
x = ['hello', 11];
```



## 6. enum

- 相当于给数组的数值分配名字

```typescript
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

- 默认情况下从0开始编号，也可以手动指定

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
let d: string = Color[1];
```



## 7. any

- 跳过编译的类型检测

```typescript
let notSure: any = 4;
notSure = 'maybe a string'
notSure = false
```

- 创建包含不同类型的数组

```typescript
let list: any = [1, 'a', false];
```



## 8. void

- 表示没有任何类型，用于函数没有返回值

```typescript
function sayHello(): void {
  console.log('hello');
}
```

- 可以给其赋值为null 或 undefined

```typescript
let test: void = undefined;
```



## 9. null 和 undefined

```typescript
// Not much else we can assign to these variables!
let u: undefined = undefined;
let n: null = null;
```

- 默认情况下`null`和`undefined`是所有类型的子类型。 就是说你可以把 `null`和`undefined`赋值给`number`类型的变量。
- 指定了`--strictNullChecks`标记，`null`和`undefined`只能赋值给`void`和它们各自。



## 10. Never

- 表示不可能存在的值

```typescript
// 返回never的函数必须存在无法达到的终点
function error(message: string): never {
    throw new Error(message);
}

// 推断的返回值类型为never
function fail() {
    return error("Something failed");
}

// 返回never的函数必须存在无法达到的终点
function infiniteLoop(): never {
    while (true) {
    }
}
```



## 11. Object

- 表示非原始类型，不能读取也不能修改

```typescript
let obj: object = {
  name: 'cw',
  age: 18
}
```



## 12. 类型断言

- 类似类型转换

```typescript
// 尖括号语法
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;

// as语法（在jsx中起效）
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```



# 二、接口

## 1. interface

- 传入的对象满足必要条件即可，无关顺序

```typescript
interface Person {
  name: string,
  age: number
}

function sayName(person: Person): void {
  console.log(person.name);
}

let cw = {
  name: 'cw',
  age: 18
}
sayName(cw) // cw
```

- 可选属性

```typescript
interface Person {
  name: string,
  age?: number
}
```

- 函数类型

```typescript
// 定义
interface SearchFunc {
  (source: string, subString: string): boolean;
}

// 创建
let mySearch: SearchFunc;
mySearch = function(source: string, subString: string) {
  let result = source.search(subString);
  return result > -1;
}
```

- 类的接口

```typescript
// 第一种
interface ClockInterface {
    currentTime: Date;
}

class Clock implements ClockInterface {
    currentTime: Date;
    constructor(h: number, m: number) { }
}

// 第二种
interface ClockInterface {
    currentTime: Date;
    setTime(d: Date);
}

class Clock implements ClockInterface {
    currentTime: Date;
    setTime(d: Date) {
        this.currentTime = d;
    }
    constructor(h: number, m: number) { }
}
```



## 2. readonly

- 给对象的属性只读，const是给变量只读

```typescript
// 定义
interface Point {
    readonly x: number;
    readonly y: number;
}

// 赋值后不能改变
let p1: Point = { x: 10, y: 20 };
p1.x = 5; // error!
```



## 3. 继承接口

- 和类一样，接口也可以相互继承。 这让我们能够从一个接口里复制成员到另一个接口里，可以更灵活地将接口分割到可重用的模块里。

```typescript
interface Shape {
    color: string;
}

interface PenStroke {
    penWidth: number;
}

interface Square extends Shape, PenStroke {
    sideLength: number;
}

let square = <Square>{};
square.color = "blue";
square.sideLength = 10;
square.penWidth = 5.0;
```



# 三、 类

## 1. 创建类

```typescript
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");
```



## 2. 继承

- 基础

```typescript
class Animal {
    move(distanceInMeters: number = 0) {
        console.log(`Animal moved ${distanceInMeters}m.`);
    }
}

class Dog extends Animal {
    bark() {
        console.log('Woof! Woof!');
    }
}

const dog = new Dog();
dog.bark();
dog.move(10);
dog.bark();
```

- 进阶

```typescript
class Animal {
    name: string;
    constructor(theName: string) { this.name = theName; }
    move(distanceInMeters: number = 0) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}

class Snake extends Animal {
    constructor(name: string) { super(name); }
    move(distanceInMeters = 5) {
        console.log("Slithering...");
        super.move(distanceInMeters);
    }
}

class Horse extends Animal {
    constructor(name: string) { super(name); }
    move(distanceInMeters = 45) {
        console.log("Galloping...");
        super.move(distanceInMeters);
    }
}

let sam = new Snake("Sammy the Python");
let tom: Animal = new Horse("Tommy the Palomino");

sam.move();
tom.move(34);
```



## 3. 公有、私有、受保护

### 3.1 public

- 类的成员默认为public

```typescript
class Animal {
    public name: string;
    public constructor(theName: string) { this.name = theName; }
    public move(distanceInMeters: number) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}
```



### 3.2 private

- 类外部不能访问

```typescript
class Animal {
    private name: string;
    constructor(theName: string) { this.name = theName; }
}

new Animal("Cat").name; // 错误: 'name' 是私有的.
```



### 3.3 protected

- 派生类可以访问

```typescript
class Person {
    protected name: string;
    constructor(name: string) { this.name = name; }
}

class Employee extends Person {
    private department: string;

    constructor(name: string, department: string) {
        super(name)
        this.department = department;
    }

    public getElevatorPitch() {
        return `Hello, my name is ${this.name} and I work in ${this.department}.`;
    }
}

let howard = new Employee("Howard", "Sales");
console.log(howard.getElevatorPitch());
console.log(howard.name); // 错误
```



### 3.4 相互兼容问题

- 如果其中一个类型里包含一个 `private`成员，那么只有当另外一个类型中也存在这样一个 `private`成员， 并且它们都是来自同一处声明时，我们才认为这两个类型是兼容的。

```typescript
class Animal {
    private name: string;
    constructor(theName: string) { this.name = theName; }
}

class Rhino extends Animal {
    constructor() { super("Rhino"); }
}

class Employee {
    private name: string;
    constructor(theName: string) { this.name = theName; }
}

let animal = new Animal("Goat");
let rhino = new Rhino();
let employee = new Employee("Bob");

animal = rhino;
animal = employee; // 错误: Animal 与 Employee 不兼容.
```



## 4. 抽象类

- 抽象类做为其它派生类的基类使用。 它们一般不会直接被实例化。 不同于接口，抽象类可以包含成员的实现细节。 `abstract`关键字是用于定义抽象类和在抽象类内部定义抽象方法。

```typescript
abstract class Animal {
    abstract makeSound(): void;
    move(): void {
        console.log('roaming the earch...');
    }
}
```

- 抽象类中的抽象方法不包含具体实现并且必须在派生类中实现。

```typescript
abstract class Department {

    constructor(public name: string) {
    }

    printName(): void {
        console.log('Department name: ' + this.name);
    }

    abstract printMeeting(): void; // 必须在派生类中实现
}

class AccountingDepartment extends Department {

    constructor() {
        super('Accounting and Auditing'); // 在派生类的构造函数中必须调用 super()
    }

    printMeeting(): void {
        console.log('The Accounting Department meets each Monday at 10am.');
    }

    generateReports(): void {
        console.log('Generating accounting reports...');
    }
}

let department: Department; // 允许创建一个对抽象类型的引用
department = new Department(); // 错误: 不能创建一个抽象类的实例
department = new AccountingDepartment(); // 允许对一个抽象子类进行实例化和赋值
department.printName();
department.printMeeting();
department.generateReports(); // 错误: 方法在声明的抽象类中不存在
```



# 四、函数

## 1. 定义

```typescript
function add(x: number, y: number): number {
    return x + y;
}

let myAdd = function(x: number, y: number): number { return x + y; };
```



## 2. 函数参数

### 2.1 可选参数

```typescript
function buildName(firstName: string, lastName?: string) {
    if (lastName)
        return firstName + " " + lastName;
    else
        return firstName;
}

let result1 = buildName("Bob");  // works correctly now
let result2 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result3 = buildName("Bob", "Adams");  // ah, just right
```



### 2.2 默认参数

```typescript
function buildName(firstName: string, lastName = "Smith") {
    return firstName + " " + lastName;
}

let result1 = buildName("Bob");                  // works correctly now, returns "Bob Smith"
let result2 = buildName("Bob", undefined);       // still works, also returns "Bob Smith"
let result3 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result4 = buildName("Bob", "Adams");         // ah, just right
```



### 2.3 剩余参数

```typescript
function buildName(firstName: string, ...restOfName: string[]) {
  return firstName + " " + restOfName.join(" ");
}

let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```



# 五、泛型

## 1. 定义

```typescript
// 定义
function identity<T>(arg: T): T {
    return arg;
}
// 利用类型推论
let output = identity("myString");  // type of output will be 'string'
```

## 2. 使用泛型变量

- 数组泛型

```typescript
function loggingIdentity<T>(arg: T[]): T[] {
    console.log(arg.length);  // Array has a .length, so no more error
    return arg;
}
```

- 函数泛型

```typescript
function identity<T>(arg: T): T {
    return arg;
}

let myIdentity: <T>(arg: T) => T = identity;
```

- 泛型类

```typescript
class GenericNumber<T> {
    zeroValue: T;
    add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; };
```



# 六、类型推论

## 1. 基本推论

```typescript
let x = 3; // 推断为number
```



## 2. 最佳通用类型

```typescript
let x = [0, 1, null]; // 推断为number或null

let zoo = [new Rhino(), new Elephant(), new Snake()]; // 不能推断
let zoo: Animal[] = [new Rhino(), new Elephant(), new Snake()]; // 正确写法：补全类型
```



## 3. 上下文类型

- 这个例子会得到一个类型错误，TypeScript类型检查器使用`Window.onmousedown`函数的类型来推断右边函数表达式的类型。 因此，就能推断出 `mouseEvent`参数的类型了。 如果函数表达式不是在上下文类型的位置， `mouseEvent`参数的类型需要指定为`any`，这样也不会报错了。

```typescript
window.onmousedown = function(mouseEvent) {
    console.log(mouseEvent.button);  //<- Error
};
```

- 如果上下文类型表达式包含了明确的类型信息，上下文的类型被忽略。 重写上面的例子：

```typescript
window.onmousedown = function(mouseEvent: any) {
    console.log(mouseEvent.button);  //<- Now, no error is given
};
```



# 七、类型兼容性

## 1. 基本规则

- 如果`x`要兼容`y`，那么`y`至少具有与`x`相同的属性。

```typescript
interface Named {
    name: string;
}

let x: Named;
// y's inferred type is { name: string; location: string; }
let y = { name: 'Alice', location: 'Seattle' };
x = y;
```



## 2. 比较两个函数

- 要查看`x`是否能赋值给`y`，首先看它们的参数列表。 `x`的每个参数必须能在`y`里找到对应类型的参数。 注意的是参数的名字相同与否无所谓，只看它们的类型。

```typescript
let x = (a: number) => 0;
let y = (b: number, s: string) => 0;

y = x; // OK
x = y; // Error
```

- 类型系统强制源函数的返回值类型必须是目标函数返回值类型的子类型。

```typescript
let x = () => ({name: 'Alice'});
let y = () => ({name: 'Alice', location: 'Seattle'});

x = y; // OK
y = x; // Error, because x() lacks a location property
```



# 八、模块

## 1. 导出

```typescript
class ZipCodeValidator implements StringValidator {
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
}
export { ZipCodeValidator };
export { ZipCodeValidator as mainValidator };
```



## 2. 导入

```typescript
import { ZipCodeValidator as ZCV } from "./ZipCodeValidator";
let myValidator = new ZCV();
```



## 3. 默认导出

```typescript
// 文件a
export default class ZipCodeValidator {
    static numberRegexp = /^[0-9]+$/;
    isAcceptable(s: string) {
        return s.length === 5 && ZipCodeValidator.numberRegexp.test(s);
    }
}

// 文件b
import validator from "./ZipCodeValidator";

let myValidator = new validator();

```



## 4. export =

```typescript
// 文件a
let numberRegexp = /^[0-9]+$/;
class ZipCodeValidator {
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
}
export = ZipCodeValidator;


// 文件b
import zip = require("./ZipCodeValidator");

// Some samples to try
let strings = ["Hello", "98052", "101"];

// Validators to use
let validator = new zip();

// Show whether each string passed each validator
strings.forEach(s => {
  console.log(`"${ s }" - ${ validator.isAcceptable(s) ? "matches" : "does not match" }`);
});
```



# 九、命名空间

```typescript
namespace Say {
  export function sayHello(): void {
    console.log('hello');
  }
}
let sayHello = say['sayHello'];
sayHello();
```





