## JavaScript零基础 day5

[TOC]

##### arguments的使用

> 只有函数才有**`arguments`**对象，代表着函数所有传递过来的**实参**

```javascript
let fn = function() {
	for(let i = 0; i < arguments.length - 1; i++)
        console.log(arguments[i]);
}
fn(1, true, 3, 4, 18, 'frash apples!');
// 输出的是一个伪数组，没有数组的一些方法，如: pop(), push()
```

##### 作用域

> JavaScript 有全局作用域和局部作用域，但没有块级作用域

```javascript
if( 5 > 4)
	let num = 23;
console.log(num) // 23, 没有块级作用域
```

###### ==tips==:

> :bell: 全局变量声明方式有两种，一种在全局声明，一种在局部作用域内赋值(:exclamation: 局部作用域要先被执行)

```javascript
let num = 17; //第一种声明方法
let len = function(){
	extent = "Linear Measure";	// 第二种声明方法
}
len();
console.log(num, extent);
```

##### 作用域链

> 采用就近原则

```javascript
let num = 13;
let len = function(){
	let num = 17; 		//一级作用域链
	let extent = function(){
		console.log(num);	//二级作用域链
	};
    extent();
};
len(); // 17
```

##### 预解析

> js引擎分为两步： **预解析** + **代码执行**
>
> 预解析分为两种： **变量提升** 和 **函数提升**

```javascript
console.log(num);	//undefined, 变量提升=> let num; -> console.log(num); ....
let num = 17;

sum(5, 6);		// error, 变量提升=> let sum; -> sum(5, 6)...
let sum = (a, b) => console.log(a + b);

reduce(7, 3);	//4, 函数提升=> function reduce(a, b) {...} -> reduce(7, 3) ...
function reduce(a, b) {
    console.log(a,b);
}
```

##### 对象

> 

```javascript
// 创建对象
let obj_1 = {};
let obj_2 = new Object();

let family = {
	atmosphere: "harmony", // 对象属性
	father: function() {	// 对象方法
		console.log("father");	
	},
	mother: function() {
		console.log("mother");	
    },
}

console.log(family.atmosphere);
family.father();
```

##### 构造函数

> 创建对象时，为了提高复用性，用函数的方法把一些相同的属性和方法抽象出来，这叫做**==“构造函数”==**.

`// 语法：`

`function 构造的函数名(参数){
	this.属性 = 属性;
	this.方法:function(){
		....
	};		
};
new 构造函数名;`

```javascript
function Fun(name, age){
	this.name = name;
    this.age = age;
}
let star = new Fun('john', 19);
console.log(star.name, star.age);
```

###### ==tips==:

* new() 的执行过程：

> 1. new 创建一个空对象({})
>
> 2. this 指向刚才创建的空对象
>
> 3. 执行构造函数里的代码 给这个空对象添加属性和方法
> 4. 返回这个对象

* 遍历对象(for...in)

```javascript
let family = {
	father_age: 34,
    mother_age: 31,
    oneself: 5,
}
for(let key in family)
    console.log(key+":"+family[key]);
```

