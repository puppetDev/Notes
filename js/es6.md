### var let const
- var 声明变量提升机制  
- 块级声明 let const 禁止重命名
- TDZ临时性死区
- 循环中的块作用域绑定
- 循环中的函数

### 函数

- 形参默认值
- es5非严格模式，参数变化提现到arguments对象中，严格模式，arguments不再随之发生变化
- 默认参数的临时性死区
- 函数命名参数前...表示不定参数
- arguments包含所有传入函数的参数
- es6为所有函数增加了name属性
- 箭头函数的特点：


```bash
1.没有this、super、、arguments和new target绑定
2.不能用new关键字调用
3.没有原型
4.不可以改变this的绑定
5.不支持arguments对象

```
### 扩展对象
- 对象属性初始值的简写

```js
let a=1;
let o={a};
```

- 对象方法的简写

```js
let o={
    say(){
        //
    }
}
```

- 可计算属性名  

```js
let lastName="last name"
let person={
    [lastName]:'x'
}
```

- Object.is()
- Object.assign()
- Object.getOwnPropertyNames()
- Object.setPrototypeOf()改变对象的原型对象
- 简化原型访问的super引用

### Symbol  
- 字符串、数字、布尔、null、undefined、Symbol

### Set

- 有序列表，包含相互独立非重复值    

```js
let set=new Set();
set.add(3);
set.add('3');
set.size===2;//true
set.has(2);//true
set.delete(2);
set.clear();
//转为数组
let array=[...set]
let set1=new Set(array)
```

- 多次add方法传入相同值作为参数，后续的调用实际上会被忽略
- Set集合的forEach()方法的回调函数接受以下3个参数：Set结合中下一次索引的位置；与第一个参数一样的值；被遍历的Set集合本身
- Set的ForEach()第二个参数可以传入this引用，或者中箭头函数

### WeakSet
- WeakSet 弱引用set结合，不接受任何原始值（string，number---）
- 不支持foreach size

### Map
- 储存着许多键值对的有序列表
- 键名和对应的值支持所有的类型

```js
let map=new Map()
let obj={}
map.set('title','es6')
map.set(obj,'2017')
map.get('title')
map.has('title')
map.delete('title')
map.clear()
map.size==0
let map2=new Map(['name','x'],['age',23])
```
- map 的ForEach 类似数组

### 迭代器Iterator
- 迭代器是一种特殊对象，它具有一些专门为迭代过程设计的专有接口，所有的迭代器对象都有一个next()方法，每次调用都会返回一个对象。结果对象有两个属性：value，done，最后一个值返回后在调用next，done为true

### 生成器
- 返回迭代器的函数，
- 关键字yield  只可在生成器内部使用  

```js
function *createIterator(){
    for (let i = 0; i < 10; i++) {
        yield i
    }
}
let iterator=createIterator();
console.log(iterator.next());

```
- 不能用箭头函数来创建生成器  

### 类

- class关键字
- 私有属性是实例中的属性，不会出现在原型上，且只能在类的构造函数或方法中创建，
- 类声明仅仅是基于已有自定义类型声明的语法糖。typeof 一个类返回的是“function”
- 函数声明可以被提升，类声明与let声明类似，不可被提升
- 类声明中的所有代码都将自动运行在严格模式下
- 类中，所有的方法都是不可枚举的
- 使用关键字new意外的方式调用类的构造函数会导致程序抛出错误
- 再类中修改类名会导致程序报错
- 一等公民是指一个可以传入函数，可以从函数返回，并且赋值给变量的值
- 访问器属性  

```js
class ClassName {
    constructor() {

    }
    set name(val){
        this.xx=val;
    }
    get html(){
        return '';
    }
}
```

- 类方法和访问器属性也支持使用可计算名称
- 静态成员

```js
class Person(){
    constructor(name){
        this.name=name;
    }
    static say(){
        return new Person(name);
    }
}
``` 

- 继承  

```js
    function An(name){
        this.name=name
    }
    An.prototype.say=function(){
        alert(this.name)
    }
    function Pe(name,sex){
        An.call(this,name)
        this.sex=sex
    }
    Pe.prototype=Object.create(An.prototype,{
        constructor:{
            value:Pe,
            enumerable:true,
            writable:true,
            configurable:true
        }
    })
```

- extend 继承自其他类的类被称为派生类，如果再派生类中指定了构造函数则必须调用super(),如果不这样做程序就会报错。
- super  

```bash
只可在派生类的构造函数中使用super
在构造函数中访问this之前一定要调用super()
如果不想调用super()
```

- 派生类中的方法总会覆盖基类中的同名方法。
- 如果基类有静态成员，那么这些静态成员在派生类中也可用。
- 只要表达式被解析为一个函数并且具有[[construct]]属性和原型，那么可以用extends进行派生。
- 内建对象的继承

```js
class MyArray extends Array
```


### 数组

- Array.of() 要创建数组，只需传入你希望在数组中包含的值
- Array.from()  可以接受可迭代对象或类数组对象作为第一个参数，最后返回一个数组
- 映射转换

```js
function translate() {
    return Array.from(arguments,value=>value+1);
}
let numbers=translate(1,2,3);
console.log(numbers);
//2,3,4

```

- find() findIndex()
- fill()
