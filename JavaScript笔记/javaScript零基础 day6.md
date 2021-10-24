# javaScript零基础 day6

[TOC]

#### 查阅MDN文档

网站：[MDN文档](https://developer.mozilla.org/zh-CN/)

#### Math对象

> max(),min()，abs(),floor(), ceil(), round(), random()

```javascript
// 最大最小值
console.log(Math.max(1, 5, 7.9, 5.6));
console.log(Math.min(1, 5, 7.9, 5.6));
// 返回绝对值
console.log(Math.abs(-1), Math.abs('-99'), Math.abs(99));
// floor 向下取整， ceil 向上取整, round 四舍五入
console.log(Math.floor(9.8),Math.floor(-9.8));
console.log(Math.ceil(9.8), Math.ceil(-9.8));
console.log(Math.round(9.8), Math.round(9.2));
// 随机数
console.log(Math.random()); //返回一个 大于等于0小于1的随机小数

```

#### Date日期对象

> Date是个构造函数，使用必须要构造函数
> 方法：getFullYear(),getMonth(),getDate(),getDay(),getHours(),getMinutes(),getSecond()
>
> 获得毫秒数方法: valueOf(),getTime(); H5新增now()

```javascript
let date1 = new Date();
//传参的两种方式
let date2 = new Date(2021, 10, 22);
let date3 = new Date("2021-10-22");
console.log(date1.getFullYear(),date1.getMonth(),date1.getDate(),date1.getDay(),date1.getHours(),date1.getMinutes(),date1.getSeconds()); //年，月，日，星期X,时，分，秒
// 获取当前毫秒数(距1970-1-1)
console.log(date1.valueOf(),date1.getTime(),Date.now());
// 简单的方法
let date4 = +new Date();
console.log(date4);
```

#### 数组

* 创建数组

> 创建数组的两种方式：字面量，new

```javascript
let arr1 = []; //字面量
let arr2 = new Array(3); //创建3个空数组
let arr3 = new Array(12, "45"); //创建两个数组元素
```

* 检测数组

> 检测数组：instanceof 运算符，Array.isArray(参数)

```javascript
let arr = [1, "hello", 3, 6];
let obj = {};
console.log(arr instanceof Array, obj instanceof Object); // true, true
console.log(Array.isArray(arr), Array.isArray(obj)); // true, false
```

* 添加/删除数组方法

> 添加删除数组方法
>
> 添加： push(), unshift() ; 删除： pop(), shift() ;

```javascript
let arr1 = [1, 2, 3], arr2 = [1, 2, 3];
console.log(arr1.push("red", "green", "blue")); // 向后添加数组元素，可添加一个或多个, 返回新数组的长度
console.log(arr2.unshift("red", "green")); // 向前添加数组元素，可添加一个或多个, 返回新数组的长度
console.log(arr1, arr2); //都会更改原数组
```

* 数组排序

> 数组排序
>
> 翻转数组： reverse(); 升降序数组：sort();

```javascript
let arr1 = [ "red", "green", "blue"];
let arr2 = [1, 2, 32, 17, 9, 81, 53];
console.log(arr1.reverse(), arr1);
console.log(arr2.sort()); //高位数字从低到高排序
//正确的排序
console.log(arr2.sort(function(a,b){
	return a - b;
})); //升序
console.log(arr2.sort(function(a,b){
    return b -a;
})); //降序
```

* 获取数组元素的索引方法

> 获取数组元素的索引方法: indexOf(数组元素)，lastIndexOf(数组元素)

```javascript
let arr1 = ["red", "green", "blue", "red", "green", "blue"];
console.log(arr1.indexOf("green")); //从头查找，返回索引号
console.log(arr1.lastIndexOf("green")); // 从后查找，返回索引号
```

* 数组转化为字符串

> 方法：toString(), join(分隔符)

```javascript
let arr = ["red", "green", "blue"];
console.log(arr.toString());
console.log(arr.join(), arr.join("-"), arr.join("&")); //join()可替换分割符
```

#### 字符串

* 属性

> 基本包装类型：字符串也可以有方法
> 字符串的不可变性：每个变量被赋值为字符串都会申请一块内存，变量被替换为另一字符串，修改都会浪费内存，这就是字符串的不可变性

```javascript
let str = "andy";
console.log(str.length);
// 基本包装类型
let temp = new String("andy");
str = temp; // 把临时变量的值赋给str
temp = null; // 销毁
```

* 字符串操作方法

  * 根据字符返回位置

  ```javascript
  let str = "改革春风吹满地，新中国的春天就要来了";
  console.log(str.indexOf("春"));
  console.log(str.indexOf("春", 3));
  ```

  * 根据位置返回字符

  > 根据位置返回字符
  >
  > charAt(index)根据索引号返回字符， charCodeAt(index)根据索引号返回字符的ASCII值

  ```javascript
  let str = "hello world!";
  console.log(str.charAt(2), str.charCodeAt(2));
  ```

  * 其它操作方法

  > 拼接： concat(); 截取：substr();
  >
  > 替换：replace(); 将字符串转化伪数组:  split(分隔符)

  ```javascript
  let str = "red";
  let str1 = "red, green, blue";
  let str2 = "a&b&c";
  console.log(str.concat("green"), str); // redgreen red,不改变原字符串
  console.log(str.substr(1,2)); //ed,第一个字符是索引号，第二个字符是截取的长度
  console.log(str.replace('e','o'), str); //rod red,不改变原字符串
  console.log(str1.split(","), str2.split("&")); // 伪数组，其实是对象
  ```

#### 数据传参

* 简单数据传参

> 简单数据类型： 值,值类型: Number,String,Array,boolean,null,undefined,symbol类型(七种原始类型) 

```javascript
// 简单数据类型
let a = 11;
function fc(i){
    i++;
    console.log(i);
}
console.log(a);
```

* 复杂数据传参

> 复杂数据类型: 引用类型,object

```javascript
// 复杂数据类型
 // 构造函数
function Person(name, age){
    this.name = name;
    this.age = age;
}

let fn = function(obj){
    console.log(`${obj.name}: ${obj.age}`);
    obj.name = "蜘蛛侠";
    obj.age = 18;
    console.log(`${obj.name}: ${obj.age}`);
}

let reson = new Person("钢铁侠", 34);
console.log(`${reson.name}: ${reson.age}`);
fn(reson);
console.log(reson.name, reson.age);
```



