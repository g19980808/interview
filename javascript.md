## JavaScript面试题

### 知识点

#### 数据类型&堆栈

##### 数据类型有哪些

JavaScript共有八种数据类型，分别是 Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt。

- Symbol 代表创建后独一无二且不可变的数据类型，它主要是为了解决可能出现的全局变量冲突的问题

- BigInt 是一种数字类型的数据，它可以表示任意精度格式的整数，使用 BigInt 可以安全地存储和操作大整数，即使这个数已经超出了 Number 能够表示的安全整数范围。

数据可以分为原始数据类型和引用数据类型：

- 栈：原始数据类型（Undefined、Null、Boolean、Number、String）
- 堆：引用数据类型（对象、数组和函数）

##### 原始值和引用值的区别

两种类型的区别在于存储位置的不同：

- 原始数据类型直接存储在栈（stack）中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
- 引用数据类型存储在堆（heap）中的对象，占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体。

堆和栈的概念存在于数据结构和操作系统内存中，在数据结构中：

- 在数据结构中，栈中数据的存取方式为先进后出。
- 堆是一个优先队列，是按优先级来进行排序的，优先级可以按照大小来规定。

在操作系统中，内存被分为栈区和堆区：

- 栈区内存由编译器自动分配释放，存放函数的参数值，局部变量的值等。其操作方式类似于数据结构中的栈。
- 堆区内存一般由开发着分配释放，若开发者不释放，程序结束时可能由垃圾回收机制回收









#### 检测数据类型

##### 1.typeof

```javascript
console.log(typeof null);            // object
console.log(typeof []);              // object  
```

只能检测基本数据类型，其中数组，对象，null都会判断为object



##### 2.instanceof

instanceof 用来检测一个对象的原型链中是否存在一个构造函数的prototype属性

原理是构造函数的 prototype 属性是否出现在对象的原型链中的任何位置

```javascript
console.log(2 instanceof Number)  //false
console.log(function(){} instanceof Function);       // true
```

只能判断引用数据类型，不能判断基本数据类型

##### 3.constructor

作用 1.判断数据类型 2.对象实例通过constructor 对象访问它的构造函数

```javascript
console.log((2).constructor === Number); // true
console.log(({}).constructor === Object); // true
```

如果创建一个对象来改变它的原型，就不能用来判断数据类型了



#####  4.Object.prototype.toString.call()

能够准确判断数据类型

```javascript
var a = Object.prototype.toString;
 
console.log(a.call(2));     //Number
console.log(a.call(null));  //Null
```





#### 字符串

##### 1.声明字符串

1.构造函数形式

var str=new String(参数)

2.字面量形式

var str='aaa'

##### 2.常用方法

###### 1.charAt()

通过下标返回指定位置的字符

###### 2.concat()

连接字符串，返回新字符串

###### 3.replace()

在字符串中替换某些字符

###### 4.split()

通过某个字符分割成数组

###### 4.indexOf()

返回字符在字符串中首次出现的位置，不存在返回-1

###### 6.lastIndexOf()

返回字符在字符串中最后一次出现的位置，不存在返回-1

###### 7.match()

在字符串内检索指定的值或正则，不存在返回null,存在返回  数组

```javascript
var url="name=qwe&id=27"
var reg=/(^|&)id=([^&]*)(&|$)/
console.log( url.match(reg)) //["&id=27","&","27","",index:8,input:"name=qwe&id=27"]
```

###### 8.toLowerCase()

把字符串转小写

```javascript
console.log( str.toLowerCase() )
```

###### 9.toUpperCase()

字符串转大写

###### 10.substring(start,end)

start包含，end不包含   ，只传一个值，从当前开始直到结束

提取字符串中两个指定索引号之间的字符

```javascript
var str="123456789"
console.log( str.substring(0,4) )//1234

console.log( str.substring(4))  //56789
```



###### 11.slice(start,end)

提取字符串的某个部分，并以新的字符串返回被提取的部分

```javascript
var str="123456789"
console.log( str.slice(0,4) )//1234

```

###### 12.substr(start,length)

从start开始提取长度

```javascript
var str="123456789"
console.log( str.slice(0,4) )//1234
```







#### 日期

```javascript
//获取当前日期
let now = new Date()
```



##### 2.获取时间方法

###### getFullYear() 

```javascript
//获取年
let year=now.getFullYear() 
```

###### getMonth()

```javascript
//获取月
let month=now.getMonth()

```

###### getDate()

```javascript
//获取日
let date=now.getDate()
```

###### getHours()

```javascript
//获取小时
let hours=now.getHours()
```

###### getMintes()

```javascript
//获取分钟
let mintes=now.getMintes()
```

###### getSeconds()

```javascript
//获取秒
let seconds=now.getFullYear() 
```

###### 获取时间戳

```javascript
new Date().getTime()
//2
let time=Date.parse(new Date())
//3
let time=(new Date()).valueOf()
//4
let time=Date.now()

```



##### 3.设置时间方法

###### setFullYear()

```javascript
//设置年份

new Date().setFullYear(new Date().getFullYear()+5)  //加5年
```



###### setMonth()

```javascript
//设置月份
new Date().setMonth(new Date().getMonth()+2)
```



###### setDate()

```javascript
//设置天数
new Date().setDate()
```



###### setHours()

```javascript
//设置小时
new Date().setHours()
```



###### setMinutes()

```javascript
//设置分钟
new Date().setMinutes()
```

###### setSeconds()

```javascript
//设置秒
new Date().setSeconds()
```

###### setDay()

```javascript
//设置周(7天)
new Date().setDay()
```



###### setTime()

```javascript
//设置时间戳
new Date().setTime()
```







#### 数组

##### 常用方法

###### push() 

数组末尾添加数据 ，改变原数组

```javascript
let arr=[1,2,3]
arr.push(4)

console.log(arr)  // [1,2,3,4]


```



###### unshift()

数组首位添加数据，改变原数组

```javascript
let arr=[1,2,3]
arr.unshift(4)

console.log(arr)  // [4，1,2,3]
```



###### pop()

删除数组最后一项，改变原数组

```javascript
let arr=[1,2,3]
arr.pop()

console.log(arr)  // [1,2]
```



###### shift()

删除数组第一项，改变原数组

```javascript
let arr=[1,2,3]
arr.shift()

console.log(arr)  // [2,3]
```



###### join()

用指定分隔符把数组拼接成字符串，不改变原数组

```javascript
let arr=[1,2,3]
let str=arr.join('-')

console.log(str)  // 1-2-3
```



###### concat()

用于连接两个或多个数组，不改变原数组

```javascript
let arr=[1,2]
let arr2=[3,4]
let newArr=arr.concat(arr2)

console.log(newArr)  // [1,2,3,4]
```



###### indexOf(item，start)

检索在数组中第一次出现索引,返回   索引 /-1，不改变原数组

item:查找的数据

start:开始检索的位置

```javascript
let arr=[1,2,3,4]
let index=arr.indexOf(2)

console.log(index)  // 1
```



###### includes()

判断数组是否包含某个字符，返回 true/false ,不改变原数组



```javascript
let arr=[1,2,3,4]
let isTrue=arr.includes(5)

console.log(isTrue)  // false
```



###### slice(start,end) 

查找符合数据，不改变原数组

start:开始查找位置，包括start

end:结束查找的位置，不包括end

只有start，从start开始查找到最后一项

start,end可以为负数，从最后一项算起，-1为最后一项，-2为倒数第二项

```javascript
let arr=[1,2,3,4]
let arr2=arr.slice(1,3) //索引为  1-3，不包括3
console.log(arr2) //[2,3]
console.log(arr.slice(0))  //[1,2,3,4]  原样输出
```



###### splice( index,len,[item])  

对数组进行增删改,改变原数组

index:数组开始下标

len:替换/删除的长度

item:替换的值，删除操作item为空

```javascript
//增加

let arr=['a','b','c']
arr.splice(1,0,'zz') 
console.log(arr)  //['a','zz','b','c']
//删除

let arr=['a','b','c']
arr.splice(1,1)  //删除index为1 长度为1
console.log(arr)  //['a','c']


//修改

let arr=['a','b','c']
arr.splice(1,2,'zz') //zz占两个长度
console.log(arr)  //['a','zz']




```



###### sort()

数组排序  ，改变原数组

默认从小到大排序

```javascript
let arr=[7,9,2,0]
arr.sort((a,b)=>{
    return a-b
})
console.log(arr)  //[0,2,7,9]

arr.sort((a,b)=>{
    return b-a
})
console.log(arr)  //[9,7,2,0]



```



###### reverse() 

 数组翻转，改变原数组

```javascript
let arr=['a','b','c']
let neW=arr.reverse()
console.log(arr) // ['c','b','a']  
```





##### 遍历方法

######  forEach(item,index,ary)  

不改变原数组，无返回值

ary:原数组

```javascript
let arr=['a','b','c']
arr.forEach((item,index)=>{
    console.log(item)  //a->b->c
    console.log(index) //0->1->2
})
```



###### map() 

改变原数组，使用return

```javascript
let arr=['a','b','c']
let res=arr.map(item=>item=='b')
console.log(res) //[false,true,false]
```



###### filter()  

返回新数组

```javascript
let arr=[1,2,3]
let res=arr.filter(item=>item>=2)
console.log(res) //[2,3]
```



###### find()  

检测符合条件的项

```javascript
let arr=[1,2,3]
let res=arr.find(item=>item>=2)
console.log(res) // 2

let arr=[{id:1,name:'a'},{id:2,name:'b'}]
let res=arr.find(item=>item.id==2)
console.log(res) //{id:2,name:'b'}

```



###### some()

检测只要有一个元素符合条件就返回true,全部不符合返回false

```javascript
let arr=[1,2,3]
let res=arr.some(item=>item>2)
console.log(res) //true

let res=arr.some(item=>item>3)
console.log(res) //false

```



###### every()

判断元素是否全部符合条件，全部符合返回true，否则false

```javascript
let arr=[1,2,3]
let res=arr.every(item=>item>2)
console.log(res) //false

let res=arr.every(item=>item>0)
console.log(res) //true
```



###### reduce()

```javascript

```



###### for...of  

可以直接获取键值

```javascript
let arr = ['a', 'b', 'c'];

for (let a of arr) {
  console.log(a); // a b c 
}



```



###### for...in  

 直接获取键名，不能直接获取键值

```javascript
let arr = ['a', 'b', 'c'];

for (let a in arr) {
  console.log(a); // 0 1 2 
}
```

##### 去重

###### 1.for+indexOf

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2 = [];
for(let i=0;i<arr.length;i++){
   if(arr.indexOf(arr[i])==i){
      arr2.push(arr[i])
   }
}
console.log(arr2)
```

###### 2.filter高阶函数去重

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2= arr.filter((item,index,self)=>{
   return self.indexOf(item)===index
})
console.log(arr2)
```

###### 3. new Set去重

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2=[...new Set(arr)]
console.log(arr2)
```

###### 4.双重for循环 +splice[1]

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
for(let i=0;i<arr.length;i++) {
    for (let j=0; j<i; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(i, 1);
                 i--
        }
     }
  }
console.log(arr)
```

###### 5.双重for循环+splice[2]

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
for(let i=0;i<arr.length;i++) {
    for (let j=i+1; j<arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j, 1);
                 j--
        }
     }
  }
console.log(arr)
```

###### 6.reduce()去重

```
const arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2= arr.reduce((pre, cur) => {
    return pre.includes(cur) ? pre : pre.concat(cur);
}, []);
console.log(arr2)
```





##### 数组扁平化

###### 1.reduce（）

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
function flatten(arr) {  
    return arr.reduce((pre, cur)=> {
        return pre.concat(Array.isArray(cur) ? flatten(cur) : cur);
    }, []);
}
flatten(arr)
```

###### 2. flat()

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
var arr2=arr.flat(Infinity);
console.log(arr2)
```

###### 3.toString+split

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
function flatten(arr) {
    return arr.toString().split(',').map(function(item) {
        return Number(item);
    })
} 
flatten(arr)
```



##### 高阶函数

###### 1.定义：

​     是对其他函数操作的函数，他接收函数作为参数或将函数作为返回值输出

###### 2.使用

```javascript
1.
const array = [1, 2, 7, 4, 5]
function forEach (array, fn) {
    for (let index = 0; index < array.length; index++) {
        fn(array[index])
    }
}

forEach(array, function (item) {
    console.log(item)
})

2.
function add(a){
 function s(b){
    a =   a+b;
    return s;
 }
 s.toString = function(){return a;}
 return s;
}
console.log(add(1)(2)(3)(4));  //10



```

###### 3.数组高阶函数

1.map()

```javascript
let num =[1,2,3]
let obj={val:5};
let newNum=num.map(function(item,index,array){
    return item+index+array[index]+this.val;
},obj)
console.log(newNum)   //[7,10,13]
```

2.reduce()

3.filter()

```javascript
let arr =[1,2,3]
let arr2=arr.filter((item)=>item%2)
console.log(arr2)   //[7,10,13]
```



##### 数组扁平化并去重排序

###### 1

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
Array.from(new Set(arr.flat(Infinity))).sort((a,b)=>{ return a-b}) 

//[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

###### 2

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
function flatten(arr) {
    while (arr.some(item => Array.isArray(item))) {
        arr = [].concat(...arr);
    }
    return arr;
}
Array.from(new Set(flatten(arr))).sort((a, b) => {
 return a - b
})

// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```

###### 3

```javascript
var arr=[ [1, 2, 2], [3, 4, 5, 5], [6, 7, 8, 9, [11, 12, [12, 13, [14] ] ] ], 10];
Array.from(new Set(arr.toString().split(',').map((v)=>{return parseInt(v,10)}))).sort((a,b)=>{ return a-b})

// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
```



#### 对象

##### Object 构造函数的方法

- `Object.assign()`

  通过复制一个或多个对象来创建一个新的对象。

- `Object.create()`

  使用指定的原型对象和属性创建一个新对象。

- `Object.defineProperty()`

  给对象添加一个属性并指定该属性的配置。

- `Object.defineProperties()`

  给对象添加多个属性并分别指定它们的配置。

- `Object.entries()`

  返回给定对象自身可枚举属性的 `[key, value]` 数组。

- `Object.freeze()`

  冻结对象：其他代码不能删除或更改任何属性。

- `Object.getOwnPropertyDescriptor()`

  返回对象指定的属性配置。

- `Object.getOwnPropertyNames()`

  返回一个数组，它包含了指定对象所有的可枚举或不可枚举的属性名。

- `Object.getOwnPropertySymbols()`

  返回一个数组，它包含了指定对象自身所有的符号属性。

- `Object.getPrototypeOf()`

  返回指定对象的原型对象。

- `Object.is()`

  比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）。

- `Object.isExtensible()`

  判断对象是否可扩展。

- `Object.isFrozen()`

  判断对象是否已经冻结。

- `Object.isSealed()`

  判断对象是否已经密封。

- `Object.keys()`

  返回一个包含所有给定对象自身可枚举属性名称的数组。

- `Object.preventExtensions()`

  防止对象的任何扩展。

- `Object.seal()`

  防止其他代码删除对象的属性。

- `Object.setPrototypeOf()`

  设置对象的原型（即内部 `[[Prototype]]` 属性）。

- `Object.values()`

  返回给定对象自身可枚举值的数组。

#### 函数

#### 正则



##### 1.正则符号

？代表0次或一次

*代表0次或多次

+代表至少一次

{m}匹配确定的m次

{m,}匹配至少m次

{m，n}匹配至少m次且最多n次

\s或 \S： 匹配任何空白字符或任何非空白字符

\d或\D:   匹配数字字符或匹配非数字字符

##### 2.正则方法

- test()

  匹配到返回true，否则返回false

  ```javascript
  var reg=/^a/
  var str="abc123"
  reg.test(str)  //true
  ```

  

- exec()

  匹配到返回数组，否则返回null

  ```javascript
  var reg=/^a/
  var str="abc123"
  reg.exec(str)  //['a',index:0,input:'abc123',group:undefined]
  ```

  

- search()

##### 3.常用正则

- 数字价格千分位分割

  ```javascript
  '123456789'.replace(/(?!^)(?=(\d{3})+$)/g, ',') // 123,456,789
  ```

  

- 手机号3-4-4分割

  ```javascript
  let mobile = '18379836654' 
  let mobileReg = /(?=(\d{4})+$)/g 
  
  console.log(mobile.replace(mobileReg, '-')) // 183-7983-6654
  ```

  

- 去除空格法和非空格

  ```javascript
  const trim = (str) => {
    return str.replace(/^\s*|\s*$/g, '')    
  }
  
  const trim = (str) => {
    return str.replace(/^\s*(.*?)\s*$/g, '$1')    
  }
  ```

- 手机号

  ```javascript
   /(^[1][3,5,6,7,8,9][0-9]{9}$)|^(999|666|888|11111)$/
  ```

- 邮编

  ```javascript
  /^[0-9]{6}$/
  ```

- 姓名( 中文,英文和空格)

  ```javascript
  /^[\u4e00-\u9fa5A-Za-z\s]*$/
  ```

  

- email地址

  ```javascript
  
  var str = "111@qq.com";
  var reg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/g;
   
  console.log(reg.test(str));
  ```

  

- url

  ```javascript
  
  var str = "http://www.baidu.com";
  var reg = /^((ht|f)tps?):\/\/[\w\-]+(\.[\w\-]+)+([\w\-\.,@?^=%&:\/~\+#]*[\w\-\@?^=%&\/~\+#])?$/g;
   
   
  console.log(reg.test(str));
  ```

- 年-月-日

  ```javascript
  /^(d{2}|d{4})-((0([1-9]{1}))|(1[1|2]))-(([0-2]([1-9]{1}))|(3[0|1]))$/
  ```

  

- 月/日/年

  ```javascript
  /^((0([1-9]{1}))|(1[1|2]))/(([0-2]([1-9]{1}))|(3[0|1]))/(d{2}|d{4})$/
  ```

  

#### 构造函数，原型

##### 实现继承的方式

###### 1.原型链继承

核心：创建父类实体对象作为子类原型

优点：可以复用父类方法或属性

缺点：1.子实例不能传父类构造函数传参

​           2.实例1里(对象，数组)修改会影响实例2



```javascript
function Person(){
	this.name='MC'
    this.list=['苹果']
    this.sleep=function(){
		console.log('睡觉')
    }
}
Person.prototype.eat=function(){
	console.log('吃饭')
}

function Student(){}
//关键 ：把Student的原型指向Person的实例对象
Student.prototype=new Person()

//实例1

var s1=new Student()
s1.name='DK' 
console.log(s1.name)  //DK   
s1.eat()   // 吃饭
s1.sleep() // 睡觉
s1.list.push('香蕉')
console.log(s1.list)  //['苹果','香蕉']



//实例2
var s2=new Student()
console.log(s2.name)  //MC   原始类型name   s1修改，s2不共享
s2.eat()   // 吃饭
s2.sleep() // 睡觉
console.log(s2.list)  //['苹果','香蕉'],引用数据类型list  s1修改,s2共享



```



###### 2.构造函数继承

核心：在子构造函数中调用父构造函数(修改父类构造函数的this为子类的this)

优点：父类的方法不会被子类共享，不会互相影响

缺点：子类无法访问父类原型中的方法和属性



```javascript
//可以继承
function Person(name){
    this.name=name
    this.sleep=function(){
        alert('睡觉')
    }
}

//原型里的eat无法继承
Person.prototype.eat=function(){
    alert('吃饭')
}

function Student(age){
    Person.call(this) //使Person的this指向Student
}

var s1=new Student(18)
alert(s1.name) //alert 18x
s1.sleep()  // alert 睡觉
s1.eat()    //报错 s1.eat is not a function

```



###### 3.构造函数+原型链组合继承

核心：使用原型链实现对原型属性和方法的继承，通过构造函数实现对实例属性的继承

缺点：调用两次父类构造函数，会有两份一样的属性和方法，影响性能



```javascript
function Person(name){
    this.name=name
    this.sleep=function(){
        alert('睡觉')
    }
    
}
Person.prototype.eat=function(){
    alert('吃饭')
}

// 构造函数继承
function Student(age){
    Person.call(this)
}
// 原型链继承 
Student.prototype=new Person('张三')

var s1=new Student(18)
s1.sleep()  //alert 睡觉
s1.eat()    //alert 吃饭

```



###### 4.寄生组合式继承(最优)

核心：在组合继承的基础上，解决了父类构造函数调用两次的问题

优点：解决了组合继承中的构造函数调用两次，构造函数引用类型共享，以及原型对象上存在多余属性的问题



```javascript
function Person(name){
    this.name=name
}
Person.prototype.eat=function(){
    alert('吃饭')
}
function Student(){
    Person.call(this)
}
//Fn 作为中转
const Fn =function(){}
Fn.prototype=Person.prototype

Student.prototype=new Fn()
var s1=new Student()
s1.eat()
```



5.class类继承

```javascript
class Person {
    constructor(){
        this.name='ky'
        this.list=['苹果']
    }
}
```









#### 原型，原型链，构造函数理解

1.原型：在JavaScript中，每当定义一个普通函数或类时，都会天生自带一个prototype属性，这个属性指向函数的原型对象，并且这个属性是一个对象数据类型的值

2.原型链：每一个对象数据类型(普通的对象、实例、`prototype`......)也天生自带一个属性`__proto__`，属性值是当前实例所属类的原型(`prototype`)。原型对象中有一个属性`constructor`, 它指向函数对象

```javascript
function Person(name,age){
    this.name=name  //this指向实例对象person1
    this.age=age
    this.say:function(){
        alert(this.name)
    }
}

let person1=new Person('wang',18)
person1.contructor==Person  //true
```



#### js执行上下文理解

##### 1.执行上下文是什么

执行上下文就是当前JavaScript代码被解析和执行时存在的环境

##### 2.执行上下文的类型

- 全局执行上下文

  ​    1.不在函数内部的代码都位于全局执行上下文  

  ​    2.创建全局对象，window对象

  ​    3.使this指向这个全局对象

  ​    4.只有一个全局执行上下文

- 函数执行上下文：当函数被调用的时候会创建一个新的执行上下文,可以有无数个

- Eval函数执行上下文：运行eval函数中的代码时创建的执行上下文，少用且不建议使用

##### 3.执行上下文栈

在执行上下文创建好后，JavaScript引擎会将执行上下文压入到栈中，通常把这种用来管理执行上下文的栈称为执行上下文栈，又称调用栈

##### 4.执行上下文的生命周期：创建 -> 执行 -> 回收

######     1.创建阶段

- 创建变量对象：首先会初始化函数的参数arguments,提升函数声明和变量声明

- 创建作用域链：在执行上下文创建阶段，作用域链是在变量对象之后创建的，作用域链是在变量对象之后创建的，作用域链本身包含变量对象。作用域链用来解析变量

-  确定this的值

     1.在全局执行上下文时，this总是指向全局对象

     2.函数执行上下文中，this值取决于函数调用方式，被对象调用则指向对象，否则一般指向全局对象windows或undefined

   变量提升的主要原因：--创建阶段时var生命的变量赋值undefined值

 创建阶段对于var、let、const的赋值状态： let和const定义变量在创建阶段没有被赋值，var生命的变量在从创建阶段被赋值undefined。 

 原因：在创建阶段，代码处扫描变量和函数声明，然后将函数声明存储在环境中，单变量会被初始化成undefined（var声明时）和保持初始状态（let、const声明时）     

######     2. 执行阶段

- 执行变量赋值

- 代码执行

######     3. 回收阶段

- 执行上下文出栈

-  等待虚拟机回收上下文



#### this&箭头函数

##### this的指向



###### 1普通函数中，

​      this指向全局对象window

###### 2.作为对象的方法调用

​       this指向调用这个函数的对象

###### 3.作为事件的处理函数时，

​       this指向触发事件的元素

###### 4.构造函数中

​       this指向new出来的新对象

###### 5.定时器中

​       this指向window

###### 6.箭头函数中

​       this指向父级中的this

###### 7.严格模式中

​       this指向undefined

##### 改变this指向

###### 1.call 方法

语法：函数名.call(调用者, 参数1, …)
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
    console.log(this)
}
fn()  // this  => window
const obj = {}
fn.call(obj, '李四', 100)  //this => obj


```



###### 2.**apply方法**

语法：函数名.apply(调用者, [参数, …])
作用：函数被借用时，会立即执行，并且函数体内的this会指向借用者或调用者

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
}
const obj = {}

fn.apply(obj, ['李四', 100])

```



###### 3.bind方法

语法：函数名.bind(调用者, 参数, …)
作用：函数被借用时，不会立即执行，而是返回一个新的函数。需要自己手动调用新的函数来改变this指向

```javascript
function fn(name, age) {
    this.name = name;
    this.age = age;
}
const obj = {}
fn.bind(obj, '李四', 100)()
```



###### 4.总结：

相同点： 三者都可以把一个函数应用到其他对象身上，注意不是自身对象
不同点：
      call，apply是直接执行函数调用。bind是绑定，执行需要再次调用
      call，bind接收逗号分隔的无限个参数列表；apply接收数组作为参数



##### 箭头函数

###### 1.箭头函数与普通函数

**（1）箭头函数比普通函数更加简洁**

- 如果没有参数，就直接写一个空括号即可
- 如果只有一个参数，可以省去参数的括号
- 如果有多个参数，用逗号分割
- 如果函数体的返回值只有一句，可以省略大括号
- 如果函数体不需要返回值，且只有一句话，可以给这个语句前面加一个void关键字。最常见的就是调用一个函数：

**（2）箭头函数没有自己的this**

箭头函数不会创建自己的this， 所以它没有自己的this，它只会在自己作用域的上一层继承this。所以箭头函数中this的指向在它在定义时已经确定了，之后不会改变。

**（3）箭头函数继承来的this指向永远不会改变**

**（4）call()、apply()、bind()等方法不能改变箭头函数中this的指向**

**（5）箭头函数不能作为构造函数使用**

构造函数在new的步骤在上面已经说过了，实际上第二步就是将函数中的this指向该对象。 但是由于箭头函数时没有自己的this的，且this指向外层的执行环境，且不能改变指向，所以不能当做构造函数使用。

**（6）箭头函数没有自己的arguments**

箭头函数没有自己的arguments对象。在箭头函数中访问arguments实际上获得的是它外层函数的arguments值。

**（7）箭头函数没有prototype**

**（8）箭头函数不能用作Generator函数，不能使用yeild关键字**



######  2.箭头函数的**this**指向

箭头函数并没有属于⾃⼰的this，它所谓的this是捕获其所在上下⽂的 this 值，作为⾃⼰的 this 值，并且由于没有属于⾃⼰的this，所以是不会被new调⽤的，这个所谓的this也不会被改变。



###### 3.new一个箭头函数的会怎样

箭头函数没有prototype，也没有自己的this指向，更不可以使用arguments参数，所以不能New一个箭头函数

###### 4.new操作符实现步骤

1. 创建一个新的对象obj
2. 将对象与构建函数通过原型链连接起来
3. 将构建函数中的this绑定到新建的对象obj上
4. 根据构建函数返回类型作判断，如果是原始值则被忽略，如果是返回对象，需要正常处理

上面的第二、三步，箭头函数都是没有办法执行的。





#### 异步编程

##### 对异步编程的理解

##### 怎么实现异步编程

###### 回调函数

解决了同步的问题，但回调地狱，每个任务只能指定一个回调函数,不能 return

###### 事件监听

###### Promise

###### Generator

######  async/await











js的==和===区别

#### 浅拷贝和深拷贝

##### 浅拷贝定义

 只是将数据中所有的数据引用下来，依旧指向同一个存放地址，拷贝之后的数据修改之后，也会影响到原数据的中的对象数据

##### 浅拷贝方式

###### 1.Object.assign(目标对象，[来源对象1,目标对象2])

```javascript
let obj1 = { name: '张三', action: { say: 'hi'};
let obj2 = Object.assign({}, obj1);
obj2.name = '李四';
obj2.action.say = 'hello'
console.log('obj1',obj1) // { name: '张三', action: { say: 'hello'}
console.log('obj2',obj2) // { name: '李四', action: { say: 'hello'}
```

###### 2....运算符

```javascript
//修改obj

let obj1={
    name:'df'
}
let obj2={...obj1}
obj2.name="zb"
console.log(obj1)  //{name:'df'}
console.log(obj2) //{name:'zb'}



//修改source

let source={
    name:'df'
}
let obj={...source}
source.name="zb"
console.log(obj)  //{name:"df"}
console.log(source) //{name:"zb"}

```

###### 3.Array.prototype.concat

```javascript
const arr = [1, 2, {name: 'aa'}];
const newArr = arr.concat();
newArr[2].name = 'wy';
console.log(arr); 
console.log(newArr);
```

###### 4.Array.prototype.slice

```javascript
const arr = [1, 2, {name: 'nordon'}];
const newArr = arr.slice();
newArr[2].name = 'wy';
```

##### 深拷贝定义

将数据中所有的数据拷贝下来，对拷贝之后的数据进行修改不会影响到原数据

##### 深拷贝方式

###### 1.递归

```javascript
function deepClone(obj){
    let objClone = Array.isArray(obj)?[]:{};
    if(obj && typeof obj==="object"){
        for(key in obj){
            if(obj.hasOwnProperty(key)){
                //判断obj子元素是否为对象，如果是，递归复制
                if(obj[key]&&typeof obj[key] ==="object"){
                    objClone[key] = deepClone(obj[key]);
                }else{
                    //如果不是，简单复制
                    objClone[key] = obj[key];
                }
            }
        }
    }
    return objClone;
}    
let a=[1,2,3,4],
    b=deepClone(a);
a[0]=2;
console.log(a,b);
```

###### 2.JSON.parse(JSON.stringify())

```javascript
var obj = {
  a: {
    c: 2,
    d: [9, 8, 7]
  },
  b: 4
}
var jsontext = JSON.stringify(obj)
var obj1 =JSON.parse(jsontext) 
console.log(obj);
console.log(obj1);

obj.a.d[0] = 666

console.log(obj);
console.log(obj1);
```



js怎么实现继承

#### 闭包

##### 什么是闭包

一个内层函数可以访问外层函数中变量的函数称为闭包

##### 闭包的应用场景

##### 闭包怎么形成的

##### 闭包解决了什么问题

避免全局变量的污染；避免命名冲突；解决循环绑定引发的索引问题；可以使函数内的变量不被垃圾回收机制回收

##### 闭包会导致什么问题

因为当一段内存在内存空间一直存在，不被销毁，就会出现内存占用，当占用过多时，导致内存溢出，结果就容易造成内存泄漏。

##### 怎么解决内存泄漏

闭包不在使用时，要及时释放，将引用内层函数对象的变量赋值为null







### Dom对象

#### dom创建

1.document.createElement('img') / document.createTextNode('a')   创建元素节点 / 文本节点

2.domA.appendChild(domB)  domA的末尾创建 domB元素

3.parentDom.insertBefore(domA,domB)  在父节点中domA插入domB前

4.dom.cloneNode(deep)   复制节点  deep:true  深复制  deep:false 浅复制



#### dom获取

##### 读取html元素

1.document.getElementById(’id‘)通过ID获取

2.document.getElementByTagName(’div‘)通过标签名获取

3.document.getElementByName()通过name属性获取

4.document.getElementByClassName('class')通过标类名获取，

5.document.querySelector('p')  所有的匹配第一个p

5.document.querySelectorAll('p')  匹配所有p



##### element 属性

1.dom.firstElementChild / dom.lastElementChild 第一个元素节点 /最后一个元素节点

2.dom.nextElementSibling  / dom.previousElementSibling  下一个元素节点 / 上一个元素节点



##### 节点属性

1.dom.parentNode   父节点

2.dom.childNodes / dom.children   所有子节点

3.dom.firstChild / dom.lastChild    第一个子节点 / 最后一个子节点

4.dom.nextSibling /dom.previousSibling   下一个子节点 / 上一个子节点

5.dom.getAttributeNode('class') 获取所有节点属性



##### 节点信息

1.dom.nodeName 节点名称

2.dom.nodeValue 节点的值

3.dom.nodeType  节点类型



##### 节点类型

element 元素节点  / text文本节点 / document文档节点 / attr属性节点 / comments注释节点



#### dom修改

###### 1.修改内容

dom.innerHTML

dom.innerText



#### dom替换

1.parentDom.replaceChild(newDom,oldDom)  在父节点中newDom替换oldDom

#### dom删除

1.dom.remove() 删除dom

2.parentDom.removeChild(dom)  在父节点中删除子节点



#### 属性操作

1.读取属性(4种)

　　　　dom.attributes[下标].value

　　　　dom.attributes['属性名']

　　　　dom.getAttributeNode('属性名').value

　　　　dom.getAttribute("属性名")

2.修改属性(2种)

　　       dom.setAttribute(name, value);//IE8不支持 只能：element.attributes['属性名']=value

　　　　dom.setAttributeNode(attrNode);//属性可以是属性节点

3.移除属性(2种)

　　　　dom.removeAttribute('属性名');

　　　　dom.removeAttributeNode(attrNode);

4.判断元素是否包含属性(2种)　

　　　　dom.hasAttribute('属性名') //true或false

　　　　dom.hasAttributes( );



#### 样式操作

设置样式

​       1.style

​               dom.style.color='red'

​        2.className

​                dom.className='样式名称'

读取样式

​        1.value=dom.style.color

​        2.getComputedStyle('样式名')

​        3.dom.currentStyle.样式名



### Bom对象

#### 定义：

Browser Object Model(浏览器对象模型) 提供了独立于内容与浏览器窗口进行交互的对象

#### 1.window对象 浏览器窗口

##### 属性：

   ie,chorome,fixfox,opera

window.innerHeight 浏览器窗口的内高度(不包括工具条，滚动条)

window.innerWidth 浏览器窗口的内宽度(像素)

   ie8,7,6,5

document.documentElement.clientHeight

document.documentElement.clientWidth

  所有浏览器

document.body.clientHeight

document.body.clientWidth



##### 方法：

- window.open( a，b  )打开新窗口

​         a ：  url打开的页面路径

​         b ： _self(自身窗口)/_blank(新的窗口)

- window.close();关闭当前窗口

- window.move( 100,100) 移动当前窗口

- window.resize(100,100) 调整当前窗口大小

  

#### 2.screen对象 屏幕对象

##### 属性：

获取屏幕信息

screen.width屏幕宽度

screen.height 屏幕高度

screen.availWidth 可用屏幕宽度

screen.availHeight 可用屏幕高度



#### 3.navigator 对象  浏览器信息

##### 属性：

navigator.appName 浏览器名称

navigator.appVersion 浏览器版本

navigator.language 浏览器设置的语言

navigator.platform 操作系统类型

navigator.userAgent 用户信息



#### 4.location对象

##### 属性：

location.protocol   url协议

location.host       主机，包括hostname和port

location.hostname      主机名

location.port       端口号

location.path   包括pathname和search

location.pathname 路径名称

location.search  参数 从’？‘开始的url部分

location.hash   从’#‘开始url部分

location.href   完整的url

##### 方法：

location.assign();   加载新页面，获取新的URL地址

location.reload();  重新加载当前页面

#### 5.history 历史对象

##### 属性：

length 返回浏览器历史列表中url数量

##### 方法：

history.back() ; 历史列表中前一个url

history.forward() ; 历史列表中后一个url

history.go(0 );具体某个url







### 手写



##### 节流防抖

1.防抖定义：在触发n秒后执行回调，n秒内再次触发则重新计时，避免多次点击导致触发多次请求

防抖函数：

```javascript
// 防抖
function debounce(fn, delay = 300) {
  //默认300毫秒
  let timer;
  return function () {
    const args = arguments;
    //还存在计时器，重新计时
    if (timer) {
      clearTimeout(timer);
        timer = null;
    }
      
    // n秒后的回调，设定时器计时  
    timer = setTimeout(() => {
      fn.apply(this, args); // 改变this指向为调用debounce所指的对象
    }, delay);
  };
}

window.addEventListener(
  "scroll",
  debounce(() => {
    console.log(111);
  }, 1000)
);

```

使用场景：**防抖**经常用在我们搜索框输入搜索，点击提交，防止等



2.节流定义：在一个时间单位内，只执行一次回调函数，如果在同一个单位时间内某事件被触发多次，只有一次能生效。节流可以使用在 scroll 函数的事件监听上，通过事件节流来降低事件调用的频率。

节流函数：

```javascript
function throttle(fn, delay) {
  let flag = true;
  return () => {
      
    //定时器在计时flag为true  
    if (!flag) return;
    flag = false;
      
     // 一段时间内执行一次函数flag为true可以执行回调函数
    timer = setTimeout(() => {
      fn();
      flag = true;  
    }, delay);
  };
}

window.addEventListener(
  "scroll",
  throttle(() => {
    console.log(111);
  }, 1000)
);

```

使用场景：节流一般在onresize、mousemove、滚动事件等事件中使用，防止过多的请求造成服务器压力



##### new操作符

```javascript
function myNew(fn, ...args) {
  let obj = Object.create(fn.prototype);
  let res = fn.call(obj, ...args);
  if (res && (typeof res === "object" || typeof res === "function")) {
    return res;
  }
  return obj;
}
//用法如下：
 function Person(name, age) {
   this.name = name;
   this.age = age;
 }
 Person.prototype.say = function() {
   console.log(this.age);
 };
 let p1 = myNew(Person, "lihua", 18);
 console.log(p1.name);
 console.log(p1);
 p1.say();

```





### HTTP

#### 是什么

HTTP(（HyperText Transfer Protocol）即超文本传输协议。是一个简单的请求-响应协议，它通常运行在TCP之上。运行于应用层。明文传输(无加密),它指定了客户端可能发送给服务器什么样的消息以及得到什么样的响应。请求和响应消息的头以ASCII码形式给出；而消息内容则具有一个类似MIME的格式。



#### 主要特点

1.简单快速：客户向服务器请求服务时，只需要传送请求方法和路径。请求方法规定了客户与服务器联系的类型不同。由于http服务器的程序规模小，因而通信速度很快。

2.灵活：http允许传输任意类型的数据对象。正在传输的类型由Content-Type加以标记。

3.无连接：限制每一次连接只处理一个请求。服务器处理完客户的请求，并受到客户的应答后，即断开连接，可以节省传输时间

4.无状态：协议对于事务处理没有记忆能力，如果后续需要处理前面的信息，必须重传，可能导致每次连接传送的数据量增大。

5.支持B/S及C/S模式。

#### HTTP工作原理

HTTP协议定义Web客户端如何从Web服务器请求Web页面，以及服务器如何把Web页面传送给客户端。HTTP协议采用了请求/响应模型。客户端向服务器发送一个请求报文，请求报文包含请求的方法、URL、协议版本、请求头部和请求数据。服务器以一个状态行作为响应，响应的内容包括协议的版本、成功或者错误代码、服务器信息、响应头部和响应数据。

##### HTTP 请求/响应的步骤

1.客户端连接到Web服务器
一个HTTP客户端，通常是浏览器，与Web服务器的HTTP端口（默认为80）建立一个TCP套接字连接。例如，http://www.luffycity.com。

2.发送HTTP请求
通过TCP套接字，客户端向Web服务器发送一个文本的请求报文，一个请求报文由请求行、请求头部、空行和请求数据4部分组成。

3.服务器接受请求并返回HTTP响应
Web服务器解析请求，定位请求资源。服务器将资源复本写到TCP套接字，由客户端读取。一个响应由状态行、响应头部、空行和响应数据4部分组成。

4.释放连接TCP连接
若connection 模式为close，则服务器主动关闭TCP连接，客户端被动关闭连接，释放TCP连接;若connection 模式为keepalive，则该连接会保持一段时间，在该时间内可以继续接收请求;

5.客户端浏览器解析HTML内容
客户端浏览器首先解析状态行，查看表明请求是否成功的状态代码。然后解析每一个响应头，响应头告知以下为若干字节的HTML文档和文档的字符集。客户端浏览器读取响应数据HTML，根据HTML的语法对其进行格式化，并在浏览器窗口中显示。

##### 浏览器地址栏键入URL，按下回车之后流程：

```
1. 浏览器向 DNS 服务器请求解析该 URL 中的域名所对应的 IP 地址;`
2. 解析出 IP 地址后，根据该 IP 地址和默认端口 80，和服务器建立TCP连接;`
3. 浏览器发出读取文件(URL 中域名后面部分对应的文件)的HTTP 请求，该请求报文作为 TCP 三次握手的第三个报文的数据发送给服务器;`
4. 服务器对浏览器请求作出响应，并把对应的 html 文本发送给浏览器;`
5. 释放 TCP连接;`
6. 浏览器将该 html 文本并显示内容;
```

#### HTTP请求

##### HTTP请求方法

get：请求指定的页面信息,并返回实体主体。
head：类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头
post：向指定资源提交数据进行处理请求〔例如提交表单或者上传文件)。数据被包含在请求体中。POST请求可能会导致新的资源的建立和或已有资源的修改。

put：从客户端向服务器传送的数据取代指定的文档的内容。
delete：请求服务器删除指定的页面。
connect：HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。

options：允许客户端查看服务器的性能。
trace：回显服务器收到的请求，主要用于测试或诊断。

##### HTTP请求消息

分为4个部分

1.请求行：用来说明请求类型，以一个方法符号开头，以空格分开，后面跟着请求的url和协议的版本。

2.请求头部：用来说明服务器要使用的附加信息。

3.空行：请求头部后面的空行是必须的。

4.请求数据：可以是任意类型。

##### HTTP请求状态码

#### HTTP响应

分为4个部分：

1.状态行：由http协议版本号，状态码，状态消息组成。

2.消息报头：用来说明客户端要使用的一些附加信息。

3.空行：消息报头后面的空行是必须的。

4.响应正文：服务器返回给客户端的文本信息。



##### HTTP响应状态码

1xx消息——请求已被服务器接收，继续处理
2xx成功——请求已成功被服务器接收、理解、并接受
3xx重定向——需要后续操作才能完成这一请求
4xx请求错误——请求含有词法错误或者无法被执行
5xx服务器错误——服务器在处理某个正确请求时发生错误

200：请求成功。

400：客户端请求有语法错误，不能被服务器理解。

401：请求未经授权，这个状态码必须和WWW-Authenticate报头域一起使用。

403：服务器收到请求，但拒绝提供服务。

404：请求资源不存在。

500：服务器发生不可预期的错误。

503：服务器当前不能处理客户端的请求，一段时间后可能恢复正常。

#### HTTP版本

截止到现在，IETF已经发布了5个HTTP协议了，包括HTTP0.9、HTTP1.0、HTTP1.1、HTTP2、HTTP3.

##### HTTP0.9

1991年发布， 没有header，功能非常简单，只支持GET。

##### HTTP1.0

1996年发布，明文传输安全性差，header特别大。它相对0.9有以下增强：

- 增加了header(使用元数据与数据解耦)
- 增加了status code，用于声明请求的结果。
- content-type可以传输其它文件。
- 请求头增加了http/1.0版本号。

缺点：每请求一次资源就新建一次tcp连接

##### HTTP1.1

1997发布，是现在使用最广泛的版本。它相对1.0有以下增强：

- 可以设置keepalive让http重用tcp连接(请求必需串行发送)
- 支持pipeline传输，请求发出后可以继续发送请求
- 增加了HOST头，让服务端知道用户请求的是哪个域名
- 增加了type、language、encoding等header

2014年更新了内容：

- 增加了TLS支持,即https传输
- 支持四种模型：短连接，可重用tcp的长链接，服务端push模型(服务端主动将数据推送到客户端cache中)，websocket模型

缺点：还是文本协议，客户端服务端都需要利用cpu解压缩

##### HTTP2

2015年发布，主要是提升安全性与性能。它相对1.1的增强有：

- 头部压缩(合并同时发出请求的相同部分)
- 二进制分帧传输，更方便头部只传输差异部分
- 流多路复用，同一服务下只需要用一个连接，节省了连接
- 服务器推送，一次客户端请求服务端可以多次响应。
- 可以在一个tcp连接中并发发送请求

缺点：基于tcp传输，会有队头阻塞问题(丢包停止窗口滑动)，tcp会丢包重传。tcp握手延时长，协议僵化问题。

##### HTTP3

2018年发布，基于谷歌的QUIC，底层使用udp代码tcp协议，

这样解决了队头阻塞问题，同样无需握手,性能大大地提升，默认使用tls加密。

### TCP

https://www.zhihu.com/tardis/sogou/art/267520757

https://blog.csdn.net/weixin_45393094/article/details/104965561?utm_medium=distribute.wap_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1.wap_blog_relevant_default&spm=1001.2101.3001.4242.2&utm_relevant_index=4

#### 是什么

1、TCP（Transmission Control Protocol，传输控制协议）是一种面向连接的、可靠的、基于字节流的通信协议，数据在传输前要建立连接，传输完毕后还要断开连接。
2、客户端在收发数据前要使用 connect() 函数和服务器建立连接。建立连接的目的是保证IP地址、端口、物理链路等正确无误，为数据的传输开辟通道。
3、TCP建立连接时要传输三个数据包，俗称三次握手（Three-way Handshaking）

①序号：Seq（Sequence Number）序号占32位，用来标识从计算机A发送到计算机B的数据包的序号，计算机发送数据时对此进行标记。
②确认号：Ack（Acknowledge Number）确认号占32位，客户端和服务器端都可以发送，Ack = Seq + 1。
③标志位：每个标志位占用1Bit，共有6个，分别为 URG、ACK、PSH、RST、SYN、FIN，



```
URG：紧急指针（urgent pointer）有效。
ACK：确认序号有效。
PSH：接收方应该尽快将这个报文交给应用层。
RST：重置连接。
SYN：建立一个新连接。
FIN：断开一个连接。
```

#### TCP三次握手

##### 过程

①客户端请求建立连接(SYN)，并且发送出序号。
②服务端接受到信号，即有确认号（ACK）,此时并同样返回请求序号Seq
③客户端接受到信号，即有确认号（ACK），连接已经建立。



![image-20220426135006301](C:\Users\unite001\AppData\Roaming\Typora\typora-user-images\image-20220426135006301.png)

小结：三次握手的关键是要确认对方收到了自己的数据包，这个目标就是通过“确认号（Ack）”字段实现的。计算机会记录下自己发送的数据包序号Seq，待收到对方的数据包后，检测“确认号（Ack）”字段，看Ack = Seq + 1是否成立，如果成立说明对方正确收到了自己的数据包

##### 为什么要三次握手

为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误。

比如：client发出的第一个连接请求报文段并没有丢失，而是在某个网络结点长时间的滞留了，以致延误到连接释放以后的某个时间才到达server。本来这是一个早已失效的报文段，但是server收到此失效的连接请求报文段后，就误认为是client再次发出的一个新的连接请求，于是就向client发出确认报文段，同意建立连接。

假设不采用“三次握手”，那么只要server发出确认，新的连接就建立了，由于client并没有发出建立连接的请求，因此不会理睬server的确认，也不会向server发送数据，但server却以为新的运输连接已经建立，并一直等待client发来数据。所以没有采用“三次握手”，这种情况下server的很多资源就白白浪费掉了。

描述：

```
1、在第一次通信过程中，A向B发送信息之后，B收到信息后可以确认自己的收信能力和A的发信能力没有问题。

2、在第二次通信中，B向A发送信息之后，A可以确认自己的发信能力和B的收信能力没有问题，但是B不知道自己的发信能力到底如何，所以就需要第三次通信。

3、在第三次通信中，A向B发送信息之后，B就可以确认自己的发信能力没有问题。

4、 小结：3次握手完成两个重要的功能，既要双方做好发送数据的准备工作(双方都知道彼此已准备好)，也要允许双方就初始序列号进行协商，这个序列号在握手过程中被发送和确认。
```



#### TCP的四次挥手

建立连接非常重要，它是数据正确传输的前提；断开连接同样重要，它让计算机释放不再使用的资源。如果连接不能正常断开，不仅会造成数据传输错误，还会导致套接字不能关闭，持续占用资源，如果并发量高，服务器压力堪忧。

##### 过程：

第一次挥手：Clien发送一个FIN，用来关闭Client到Server的数据传送，Client进入FIN_WAIT_1状态。

第二次挥手：Server收到FIN后，发送一个ACK给Client,Server进入CLOSE_WAIT状态。

第三次挥手： Server发送一个FIN，用来关闭Server到Client的数据传送，Server进入LAST_ACK状态。

第四次挥手：Client收到FIN后，Client进入TIME_WAIT状态，发送ACK给Server，Server进入CLOSED状态，完成四次握手。

```
A：“任务处理完毕，我希望断开连接。”
B：“哦，是吗？请稍等，我准备一下。”
等待片刻后……
B：“我准备好了，可以断开连接了。”
A：“好的，谢谢合作。”
```

![image-20220426140613366](C:\Users\unite001\AppData\Roaming\Typora\typora-user-images\image-20220426140613366.png)

##### 为什么连接的时候是三次握手，关闭的时候却是四次握手？

①因为当Server端收到Client端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。
②但是关闭连接时，当Server端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉Client端，“你发的FIN报文我收到了”。
③只有等到我Server端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送。故需要四步握手。

##### TCP的三次握手一定能保证传输可靠吗？不能

1.三次握手比两次更可靠，但也不是完全可靠，而追加更多次握手也不能使连接更可靠了。因此选择了三次握手。

2.世界上不存在完全可靠的通信协议。从通信时间成本空间成本以及可靠度来讲，选择了“三次握手”作为点对点通信的一般规则

#### HTTP与TCP的区别

TCP是传输层协议，主要解决数据如何在网络中传输，而HTTP是应用层协议，主要解决如何包装数据。

TCP/IP和HTTP协议的关系，从本质上来说，二者没有可比性，在传输数据时，可以只使用（传输层）TCP/IP协议，但是那样的话，如果没有应用层，便无法识别数据内容，如果想要使传输的数据有意义，则必须使用到应用层协议，应用层协议有很多，比如HTTP、FTP、TELNET 等，也可以自己定义应用层协议。WEB使用HTTP协议作应用层协议，以封装HTTP 文本信息，然后使用TCP/IP做传输层协议将它发到网络上。

##### 短连接：

客户端和服务端建立连接，发送完数据后立马断开连接。下次要取数据，需要再次建立连接。

短连接的操作步骤是：建立连接——数据传输——关闭连接…建立连接——数据传输——关闭连接

##### 多路复用：

通过单一的HTTP/2连接请求发起多重的请求-响应消息，多个请求stream共享一个TCP连接，实现多留并行而不是依赖建立多个TCP连接。

##### 长连接：

客户端和服务端建立连接后不进行断开，之后客户端再次访问这个服务器上的内容时，继续使用这一条连接通道。

##### Http长连接和TCP长连接的区别

Http长连接 和 TCP长连接的区别在于: TCP 的长连接需要自己去维护一套心跳策略。，而Http只需要在请求头加入keep-alive:true即可实现长连接。

#### 

### HTTPS

#### 是什么

以安全为目标的 HTTP 通道，简单讲是 HTTP 的安全版。即 HTTP 下加入 SSL 层，HTTPS 的安全基础是 SSL，因此加密的详细内容就需要 SSL。

#### 与 HTTPS 的区别

1.HTTP 是明文传输，HTTPS 通过 SSLTLS 进行了加密

2.HTTP 的端口号是 80，HTTPS 是 443

3.HTTPS 需要到 CA 申请证书，一般免费证书很少，需要交费

4.HTTPS 的连接很简单，是无状态的；HTTPS 协议是由 SSL+HTTP 协议构建的可进行加密传输、身份认证的网络协议，比 HTTP 协议安全。

#### HTTP 通信有什么问题

1.通信使用明文(不加密)，内容可能被窃听

2.不验证通信方的身份，因此有可能遭遇伪装

3.无法证明报文的完整性，所以可能遭篡改

#### HTTPS 如何解决上述三个问题

##### 1.解决内容可能被窃听的问题——加密

- 对称加密(加密和解密同用一个密钥)
- 非对称加密(公开密钥加密使用一对非对称的密钥)
- 对称加密+非对称加密

##### 2.解决报文可能遭篡改问题——数字签名

- 能确定消息确实是由发送方签名并发出来的，因为别人假冒不了发送方的签名。
- 数字签名能确定消息的完整性,证明数据是否未被篡改过。

##### 3.解决通信方身份可能被伪装的问题——认证

使用由数字证书认证机构(CA，Certificate Authority)和其相关机关颁发的公开密钥证书。

#### 为什么不一直使用 HTTPS

- 因为与纯文本通信相比，加密通信会消耗更多的 CPU 及内存资源。如果每次通信都加密，会消耗相当多的资源，所以只有在包含个人信息等敏感数据时，才利用 HTTPS 加密通信
- 节约购买证书的开销

### Ajax

#### 是什么

全称为“Asynchronous JavaScript and XML”（异步JavaScript和XML），是一种创建交互式网页应用的技术。Ajax是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。传统的网页(不使用Ajax)如果需要更新内容，需要重载整个网页。

#### 工作原理

Ajax的工作原理相当于在用户和服务器之间加了一个中间层(Ajax引擎)，使用户操作与服务器响应异步化。并不是所有用户请求都提交服务器。像一些数据验证和数据处理等都交给Ajax引擎自己来做，只有确定需要从服务器读取新数据时再由Ajax引擎代为向服务器提交请求。

#### 执行流程

- 创建XMLHttpRequest对象,也就是创建一个异步调用对象

- 创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息

- 设置响应HTTP请求状态变化的函数(打开链接open())

- 发送HTTP请求(发送send())

- 数据接收完成，判断http响应状态(status) 200~300之间或304(缓存)执行回调函数

- 使用JavaScript和DOM实现局部刷新

#### 优点

- 局部刷新页面，减少用户心理和实际的等待时间，带来更好的用户体验
- 按需取数据，减轻服务器的负担，最大程度减少冗余请求
- 异步方式与服务器通信，不需要打断用户的操作，具有更加迅速地响应能力
- 基于xml标准化，并被广泛支持，不需要安装插件等，进一步促进页面和数据的分离

#### 缺点

- 本身是针对MVC编程，不符合前端MVVM的浪潮
- 基于原生XHR开发，XHR本身的架构不清晰
- 不符合关注分离（Separation of Concerns）的原则
- 配置和调用方式非常混乱，而且基于事件的异步模型不友好。

#### 适用场景

- 表单驱动的交互
- 深层次的树的导航

- 快速的用户与用户间的交流响应
- 类似投票，yes/no等无关痛痒的场景

- 对数据进行过滤和操纵相关数据的场景

- 普通的文本输入提示和自动完成的场景

#### 不适用场景

- 部分简单的表单

- 搜索
- 基本的导航

- 替换大量的文本

- 对呈现的操纵

### Axios

#### 定义

可以理解为ajax i/o system，这不是一种新技术，本质上还是对原生XMLHttpRequest的封装，可用于浏览器和nodejs的HTTP客户端，只不过它是基于Promise的，符合最新的ES规范

#### 特点

- 浏览器端发起XMLHtppRequests请求
- node端发起http请求
- 支持PromiseAPI
- 监听请求和返回
- 对请求和返回进行转化
- 取消请求
- 自动转换json数据
- 客户端支持抵御XSRF攻击

#### 请求方式

- axios(config)
- axios.request(config)
- axios.get(url [,config])
- axios.post(url [,data [,config]])
- axios.put(url [,data [,config]])
- axios.delete(url [,config])
- axios.patch(url [,data [,config]])
- axios.head(url [,config])





### Fetch

#### 定义

在es6中基于promise设计，不是ajax的进一步封装，而是原生js,没有使用XMLHttpRequest对象

#### 优点

- 语法简洁，更加语义化
- 基于标准Promise实现，支持async/await
- 更加底层，提供的API丰富
- 脱离了XHR,是ES规范里新的实现方式

#### 缺点

- fetch只对网络请求报错，对400，500都当作成功的请求，返回400，500时不会rejecte，只有网络错误这些导致请求不能完成，fetch才会被reject

- fetch默认不带cookie
- fetch不支持abort,不支持超时控制，使用setTimeout及promise.reject的实现的超时控制并不能阻止请求过程继续在后台运行，造成了流量的浪费
- fetch没有办法原生检测请求的进度，而XHR可以

### 浏览器

1.浏览器的缓存机制是什么

2.session、cookie和token区别及应用场景

3.meta viewport的作用

4.跨域





什么是跨域

跨域怎么解决

jsonp实现跨域的原理

5.浏览器的渲染机制





## ES6面试题

### promise

#### 定义

Promise是异步编程的一种解决方案，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果

#### 特点

1. 对象的状态不受外界影响

   promise有三种状态：pending、fulfilled和rejected,只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态

2. 一旦状态改变，就不会再变，任何时候都可以得到这个结果

   Promise对象的状态改变，只有两种可能：从pending变为fulfilled和从pending变为rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果

#### 作用

ES6 规定，Promise对象是一个构造函数，用来生成Promise实例。

###### resolve函数作用

将Promise对象的状态从“未完成”变为“成功”（即从 `pending` 变为 `resolved`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去

###### reject函数作用

将`Promise`对象的状态从“未完成”变为“失败”（即从 `pending` 变为`rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去

#### 缺点

- promise一旦执行无法取消

- 如果不设置回调函数promise内部抛出的错误，不会反映到外部

- 当处于pending（进行中）的状态时，无法得知进行到那一阶段（刚开始或者即将完成）

  #### 

#### promise三种状态

- Pending:promise对象刚被创建后的初始化状态(执行中)
- Fulfilled:成功时时会调用 onFulfilled
- Rejected:失败时此时会调用 onRejected

#### promise的方法

###### then()

执行状态改变时的成功回调或失败回调

```javascript

let p = new Promise(function(reslove,reject){
    reslove('成功')  //状态由等待变为成功，传的参数作为then函数中成功函数的实参
    reject('失败')  //状态由等待变为失败，传的参数作为then函数中失败函数的实参
})
```



###### catch()

可以实现错误的捕获

```javascript
let p = new Promise(function(resolve,reject){
    reject('失败')
});

p.then((res)=>{},(err)=>{
    throw Error('错误')    //有err执行err,没有err执行catch
}).catch(e=>{
    console.log(e+'公共的err')   //执行catch
})
```



###### finally()

用于指定不管 Promise 对象最后状态如何，都会执行的操作

###### all()

返回的依旧是promise, all两个全成功才表示成功

```javascript
function read(content) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            resolve(content)
        }, 1000)
    })
}

let result = Promise.all([read(1), read(2)]);
result.then((data) => {
    console.log(data) //[ 1, 2 ]
})
```



###### race()

如果先成功了那就成功了, 如果先失败了那就失败了

```javascript
function read(content) {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            if(content>4){
                resolve(content)
            }else{
                reject(content)
            }
        }, 1000*content)
    })
}

let result = Promise.all([read(5), read(2)]);
result.then((data) => {
    console.log('成功'+data)
},(err)=>{
    console.log('失败'+err) //失败2
})
```



###### any()

有一个成功就算成功，全部失败才算失败



#### race、all和any的区别

all所有Promise的结果都返回resolve才会执行then，返回结果为一个存放所有结果的数组里，如果有任何一个返回reject，则执行catch，如果第一个Promise是有延迟执行的 则会等待执行完才继续

可实现发送多个请求，参数不一定是数组，只要有iterable接口就行，函数返回的是一个数组



race的方法执行结果取决于第一个Promise的返回结果，reject则执行catch，resolve则执行then，不会等待定时器的执行，会将定时器时间执行时间短的结果返回











### async,await

ES7提出的基于promise的解决异步的最终方案

#### async

async是一个加在函数前的修饰符，被async定义的函数会默认返回一个Promise对象resolve的值。因此对async函数可以直接then，返回值就是then方法传入的函数。

#### await

await 也是一个修饰符，只能放在async定义的函数内。可以理解为等待,修饰的如果是Promise对象：可以获取Promise中返回的内容,且取到值后语句才会往下执行；如果不是Promise对象：把这个非promise的东西当做await表达式的结果。



#### 使用场景

多个请求中，后面请求参数需要前面请求返回数据



```javascript
async submit(type) {
     var res = await salesCheck(this.form)
}
```







## 	VUE面试题

### 虚拟dom原理

#### 虚拟dom为什么能提高性能

#### 1.定义

虚拟dom其实就是用一个原生的js对象去描述一个dom节点，是对真实dom的抽象。状态变更时，记录新树和旧树的差异 最后把差异更新到真正的dom中，相当于在js和真实dom之间做了一个缓存，利用patch(diff算法)对比新旧虚拟dom记录到一个对象中按需更新，最后创建真实的dom

#### 2.原生DOM慢的原因

浏览器收到一个DOM操作，就会走一遍完整的渲染流程，像计算元素坐标的操作就会浪费掉，因为下次DOM操作可能会改变之前计算的坐标

#### 3.虚拟dom渲染方式

利用batching把所有的DOM操作收集起来，一次性提交给真实的DOM，diff算法通过对比新旧虚拟DOM,记录之间的差异

中心思想：在一个不在render tree的元素统一统计所有操作，再把节点加到render tree上，这样复杂的DOM操作最后就只进行一次layout



#### 4.虚拟DOM优点

 真实的DOM创建、更新、插⼊等操作会带来⼤量的性能损耗，从⽽极⼤的降低渲染效率

- 减少DOM的操作

​          减少DOM的操作的次数：虚拟DOM可以将多次操作合并为一次操作，比如添加1000个节点，却是一个一个操作的，虚拟DOM则是往数组中添加一千个文本，虚拟DOM可以合并为一次
​         减少DOM操作的范围：虚拟DOM借助DOM diff可以把多余的操作省掉，如果页面中990个节点，现在需要添加10个，虚拟DOM通过diff算法对比节点，只操作需要更新的10个节点就好了，而js是无法判断的，会对所有的DOM进行操作

- 跨平台

    虚拟DOM本质上是JavaScript对象,而DOM与平台强相关,相比之下虚拟DOM可以进行更方便地跨平台操作,例如服务器渲染、移动端开发等等

#### 5.虚拟DOM缺点

​    需要额外的创建函数，如createElement，但是可以用JSX来简化成XML写法，严重依赖打包工具，需要添加额外的构建过程

#### 6.虚拟DOM基本步骤

- 用 JavaScript 对象模拟真实 DOM 树，对真实 DOM 进行抽象；

- `diff 算法` — 比较两棵虚拟 DOM 树的差异；

- `patch 算法` — 将两个虚拟 DOM 对象的差异应用到真正的 DOM 树

  1.首先在 `oldVnode`（老 VNode 节点）不存在的时候，相当于新的 VNode 替代原本没有的节点，所以直接用 `addVnodes` 将这些节点批量添加到 `parentElm` 上。------创建新增的节点

  2.然后同理，在 `vnode`（新 VNode 节点）不存在的时候，相当于要把老的节点删除，所以直接使用 `removeVnodes` 进行批量的节点删除即可。-----删除已经废弃的节点

  3.最后一种情况，当 `oldVNode` 与 `vnode` 都存在的时候，需要判断它们是否属于 `sameVnode`（相同的节点）。如果是则进行patchVnode（比对 VNode ）操作，否则删除老节点，增加新节点。--修改需要更新的节点



#### 7.虚拟dom如何转换真实dom

在⼀个组件实例⾸次被渲染时，它先⽣成虚拟dom树，然后根据虚拟dom树创建真实dom，并把真实dom挂载到页⾯中合适的位置，
此时，每个虚拟dom便会对应⼀个真实的dom。
如果⼀个组件受响应式数据变化的影响，需要重新渲染时，它仍然会重新调⽤render函数，创建出⼀个新的虚拟dom树，⽤新树和旧
树对⽐，通过对⽐，vue会找到最⼩更新量，然后更新必要的真实dom节点

这样⼀来，就保证了对真实dom达到最⼩的改动。



#### 8.diff算法

##### (1)diff算法的[时间复杂度

两个树的完全的 diff 算法是一个时间复杂度为 O(n3) , Vue 进行了优化·O(n3) 复杂度的问题转换成 O(n) 复杂度的问题(只比较同级不考虑跨级问题)，因为在前端操作dom的时候了，不会把当前元素作为上一级元素或下一级元素，很少会跨越层级地移动Dom元素，常见的都是同级的比较。 所 以 Virtual Dom只会对同一个层级的元素进行对比。

##### (2)vue中diff算法的原理

在数据发生变化，vue是先根据真实DOM生成一颗 virtual DOM ，当 virtual DOM 某个节点的数据改变后会生成一个新的 Vnode ，然后 Vnode 和 oldVnode 作对比，发现有不一样的地方就直接修改在真实的DOM上，然后使 oldVnode 的值为 Vnode ，来实现更新节点。

对比过程：

- 判断`Vnode`和`oldVnode`是否相同，如果是，那么直接return；
- 如果他们都有文本节点并且不相等，那么将更新为`Vnode`的文本节点。
- 如果`oldVnode`有子节点而`Vnode`没有，则删除el的子节点
- 如果`oldVnode`没有子节点而`Vnode`有，则将`Vnode`的子节点真实化之后添加到el
- 如果两者都有子节点，则执行`updateChildren`函数比较子节点，而这个函数也是diff逻辑最多的一步



#### 9.不使用index作为for循环key值

主要是因为虚拟DOM的diff算法，当遍历一个数组的时候使用了index作为key值，如果这个数组中的数据进行打乱，因为diff算法是根据key值去进行新旧对比的，如果发现key所对应的数据不一致的情况下，就会进行重新渲染，删除原来的旧元素，重新生成新的元素。

而如果不是使用index作为key值，使用的是唯一data数据唯一标识的话，diff算法会根据key去对比发现原来的DOM元素只是调换了位置，就不会去删除旧元素而去生成新的元素了。

不使用index作为key值其实是方便了diff算法，使其更加高效，









### vue权限管理

#### 1.菜单权限管理(不同用户菜单权限不同)

​     根据用户登录返回菜单权限 ,使用vuex+本地存储数据，只使用vuex刷新页面数据丢失

​     退出登录需要清除sessionStoryage和vuex数据

​     sessionStorage.clear()    清除本地存取

​     window.location.reload()    刷新清除vuex

```javascript
  //store.js

   state:{
      rightList: JSON.parse( sessionStorage.getItem('rightList') ||  '[]')   
    }

   mutations:{
      setRightList(state.data){
	       state.rightList=data
	       sessionStorage.setItem('rightList',JSON.stringify(data))
      }
    }

  // login.vue
      login().then(res=>{
         let {data}=res 
            this.$store.commit('setRightList',data.rightList)
      })

  // home.vue
    //一级菜单
    <div v-for="(item,index) in menuList" :key="index">      
         {{ item}}
       //二级菜单
      <div v-for="(item2,index2) in item" :key="index2">{{item2}}</div>
    <div>
          
    import {mapState} form 'vuex'
     created(){
         this.menuList=this.rightList
     }
     computed:{
        ...mapState(['rightList'])
     }
```





#### 2.界面权限管理

#####   1.路由导航钩子，防止用户跳过登录进入其他页面



```javascript
   router.js
   
   router.beforeEach((to,from,next)=>{
        if(to.path=="/login"){
	        next()
         }else {
	        const token=sessionStorage.getItem('token')
	        if(!token){
	             next('/login')
	         }else {
	             next()
             }
         }
     })
```







#####      2.根据登录动态添加路由规则



```javascript
    // router.js
    import store form 'store.js'
    const userRule={path:'/user' ,component:User}
    const rolesRule={path:'/user' ,component:roles}
    const goodsRule={path:'/user' ,component:goods}
    const ruleMap={
       'use' :userRule,
       'roles':  rolesRule,
       'goods': goodsRule
     }
    export function addRouter(){
        // 根据二级路由权限，对路由规则进行动态添加
         const currentRoutes=router.options.routes
         const rightList= store.state.rightList
         rightList.forEach(item=>{
	          item.children.forEach(its=>{
	              const temp =ruleMap[item.path]
	              temp.meta=item.rights    添加路由元数据
                  currentRoutes[2].children.push(temp)
	           })
          })
          router.addRoutes(currentRoutes)               
      }



   // login.vue
     import { addRouter } form 'router'

     login(){
       addRouter ()    //登录动态添加二级路由
     }

     //登录完成刷新会丢失动态添加的路由
     // 在 APP.vue中
      import {addRouter } form 'router.js'
       created(){
           addRouter ()
      }



```





#### **3.按钮权限管理**

```javascript
   //通过自定义指令  自定义： action 删除   effect  禁用
   // permission.js
     import Vue form 'vue'
     import router form 'router.js'

      Vue.directive('permission',{
          inserted(el,binding){
             const action= binding.value.action   
	         const effect=binding.value.effect
              // 通过 添加路由元数据判断按钮权限

             if(router.currentRoute.meta.indexOf(action)==-1){
                   if(effect=='disabled'){  
                        el.disabled=true
	                    el.classList.add('is-disabled')
	                }else {
	                   el.parentNode.removeChild(el)
	                }
              }
          }

      })



    // main.js
     import 'permission.js'

    // user.vue
     <button v-permission="{action:'add',effect:'disabled'}">添加</button>
```





#### 4.请求和响应权限管理

#####    1.请求拦截

```javascript
   const actionMap={
       'get':'view',    
       'post':'add',
       'put':'edit',
       'delete':'delete'
   }

    axios.interceptors.request.use((request)=>{
        if(request.url!=='login'){
           // 1.除了登录请求都添加token
	         request.header.Authorization=sessionStorage.getItem('token')
	       //2.判断非权限范围内的请求   例如 非权限按钮删除
	         const action =actionMap[request.method]
	         const currentRight=router.currentRoute.meta
	         if( currentRight&&currentRight.indexOf(action)===-1){
	             aler('无权限')
	            return Promise.reject(new Error('无权限'))
	         }
         }
       return request
    })
```





#####     2.响应拦截

```javascript
   axios.interceptors.response.use(res=>{
       if(res.data.code===401){
	       router.push('/login')
	       sessionStorage.clear()
	       window.location.reload()
        }
        return res
    })
```







### 知识点

#### vue的优点和缺点

##### 优点：

1.vue作为一款轻量级框架，门槛低，上手快，简单易学。

2.vue可以进行组件化开发，数据与结构相分离，使代码量减少，从而提升开发效率，易于理解

3.vue最突出的优势在于对数据进行双向绑定，使用虚拟DOM

4.相较于传统页面通过超链接实现页面跳转，vue会使用路由跳转不会刷新页面

5.vue是单页面应用，页面局部刷新，不用每次跳转都请求数据，加快了访问速度，提升了用户体验

##### 缺点：

1.初次加载时耗时多



#### 生命周期

##### vue生命周期定义

Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。

##### 生命周期有哪些

beforeCreate, created, beforeMount, mounted

##### 生命周期的作用

它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。

##### 第一次页面加载会触发哪几个钩子

beforeCreate, created, beforeMount, mounted

##### 在哪个阶段有$el,$data

beforeCreate   el无   data无

created             el无    data有

beforeMount   el无    data有

mounted           el有   data有



##### 每个周期具体适合哪些场景

beforecreate : 可以在这加个loading事件，在加载实例时触发

created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用

mounted : 挂载元素，获取到DOM节点

updated : 如果对数据统一处理，在这里写上相应函数

beforeDestroy : 可以做一个确认停止事件的确认框 nextTick : 更新数据后立即操作dom

##### 如果加入keep-alive 会增加两个生命周期

activated : keep-alive 组件激活时调用

deactivated:keep-alive 组件停用时调用

##### 8.如果加入keep-alive ，第一次会执行哪些生命周期

beforeCreate, 

created, 

beforeMount, 

mounted

activated 

##### 9.如果加入keep-alive ，第二次或第N次会执行哪些生命周期

只执行一个生命周期  activated 

##### 对 keep-alive 的了解

1.vue系统自带的组件，一般结合路由和动态组件一起使用，用于缓存组件来提高性能；

2.提供 include 和 exclude 属性，两者都支持字符串或正则表达式， include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的组件都不会被缓存 ，其中 exclude 的优先级比 include 高；

3.对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated。



#### 怎样理解 Vue 的单向数据流

#### computed,watch

##### computed

计算属性，依赖其它属性值，并且 computed 的值有缓存，只有它依赖的属性值发生改变，下一次获取 computed 的值时才会重新计算 computed 的值

场景:当我们需要进行数值计算，并且依赖于其它数据时，应该使用 computed，因为可以利用 computed 的缓存特性，避免每次获取值时，都要重新计算

##### watch

 更多的是「观察」的作用，类似于某些数据的监听回调 ，每当监听的数据变化时都会执行回调进行后续操作；

场景:当我们需要在数据变化时执行异步或开销较大的操作时，应该使用 watch，使用 watch 选项允许我们执行异步操作 ( 访问一个 API )，限制我们执行该操作的频率，并在我们得到最终结果前，设置中间状态。这些都是计算属性无法做到



#### vue组件间通信方式

1.props / $emit 适用 父子组件通信

2.ref 与 parent /children 适用 父子组件通信

-   ref：如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例
-   parent /children：访问父 / 子实例

3.EventBus (emit/on） 适用于 父子、隔代、兄弟组件通信

4.attrs/listeners 适用于 隔代组件通信

5.provide / inject 适用于 隔代组件通信

​     祖先组件中通过 provider 来提供变量，然后在子孙组件中通过 inject 来注入变量。provide / inject API 主要解决了跨级组件间的通信问题，不过它的使用场景，主要是子组件获取上级组件的状态，跨级组件间建立了一种主动提供与依赖注入的关系

6.Vuex 适用于 父子、隔代、兄弟组件通信



#### 数组项赋值,vue能检测到变化吗

#### 组件中data为什么是一个函数

因为组件是用来复用的，且 JS 里对象是引用关系，如果组件中 data 是一个对象，那么这样作用域没有隔离，子组件中的 data 属性值会相互影响，如果组件中 data 选项是一个函数，那么每个实例可以维护一份被返回对象的独立的拷贝，组件实例之间的 data 属性值不会互相影响；而 new Vue 的实例，是不会被复用的，因此不存在引用对象的问题

#### slot

##### 定义

##### 作用

##### 原理

#### 什么是 MVVM

#### Vue 是如何实现数据双向绑定的

#### Vue 框架怎么实现对象和数组的监听



#### 虚拟 DOM 的优缺点

#### 虚拟 DOM 实现原理

#### Vue 中的 key 有什么作用









v-if,v-show 区别

vue双向绑定原理

实现双向绑定的思路

#### vue优化

优化的方式

优化使用的工具

#### vue-router

##### 路由模式

###### hash

使用 URL hash 值来作路由。支持所有浏览器，包括不支持 HTML5 History Api 的浏览器；

###### history 

依赖 HTML5 History API 和服务器配置。具体可以查看 HTML5 History 模式；

###### abstract 

支持所有 JavaScript 运行环境，如 Node.js 服务器端。如果发现没有浏览器的 API，路由会自动强制进入这个模式.

##### 路由模式实现原理

hash实现原理

history 实现原理

##### 路由传参

###### 方法 一：

```
 this.$router.push({
          path: `/describe/${id}`,
   })
// 路由配置         
  {
     path: '/describe/:id',
     name: 'Describe',
     component: Describe
   }
 //获取参数
 this.$route.params.id
```

###### 方法二：

```
this.$router.push({
          name: 'Describe',
          params: {
            id: id
          }
    })
 // 获取参数
this.$route.params.id
```

###### 方法三：(url拼接)

```
this.$router.push({
          path: '/describe',
          query: {
            id: id
       }
 })
 // 获取参数
 this.$route.query.id
```





#### vuex

state

mutation

action   

getter    :不会修改state中的数据，只是读取操作

```javascript
store.js

export defalut new Vuex.Store({
  state:{
     count:0
  },
//同步操作,使用commit
  mutations:{
    add(state,step){
      state.count+=step
   },
    sub(state,step){
      state.count-=step
    }
 },
//异步操作 1秒后修改使用dispatch
  actions:{
    subAsync(context,step){
      setTimout(()=>{
         context.commit('sub',step)
      },1000)
    }
 },
//读取操作
 getters:{
    showNum(state){
      return '最新数据'+state.count
    }
  }
})

```



```javascript
//组件内
//使用state
<div>{{$store.state.count}}</div>
<div>{{count}}</div>
//使用mutation
<button @click="handle">+4</button>
<button @click="add(3)">+4</button>
//使用actions
<button @click="handle2">+4</button>
<button @click="subAsync(3)">+4</button>
//使用getter



使用state中值方式

1.   this.$store.state.count

2.   import  { mapState }  from 'vuex'

       computed:{

       ...mapState (['count'])

      }
使用mutation中值方式
1. methods:{
        handle(){
            this.$store.commit('add',4)
        }
   }
2. import  { mapMutations }  from 'vuex'
   methods:{
       ...mapMutations(['add'])
   }
使用action中的方式
1. methods:{
        handle2(){
            this.$store.dispatch('subAsync',4)
        }
   }
2. import  { mapActions }  from 'vuex'
   methods:{
       ...mapActions(['subAsync'])
   }
使用getter中值方式
1. this.$store.getters.showNum
2. import  { mapActions }  from 'vuex'
   computed:{
       ...mapGetters(['showNum'])
   }
```



## VUE3面试题

#### 获取dom

##### 1.获取单个dom

```js
<div ref="myRef">  vue3</div>
import {ref,onMounted} form 'vue'
setup(){
    const myRef=ref(null);
    onMounted(()=>{
        console.log(myRef.value)
    });
    return {
        myRef
    };
    
}

<h1 ref="color">color</h1>
import {ref,onMounted} form 'vue'
setup(){
    const color=ref(null);
    onMounted(()=>{
        color.value.style.color="red"
    })
}

```



##### 2.获取多个dom

```js
<ul> 
    <li v-for="(item,index) in arr" :key="index" :ref="setRef">{{item}}</li>
</ul>
import {ref,nextTick} form 'vue'
setup(){
    const arr=ref([1,2,3]);
    const myRef=([]);
    const setRef=(el)=>{
        myRef.value.push(el)
    };
    nextTick(()=>{
        console.log(myRef.value)
    })
    return {
        arr,
        setRef,
    }
```

#### 父子传参

##### 1.父传子

```js
父组件
<Son :father="father"></Son>
import {ref} from 'vue'
setup(){
    const father=ref="父组件传过的值"
    return {
        father
    }
}

```

```js
子组件
<div>{{father}<div>
    props:[
        "father"
    ],
    setup(props,context){
        console.log(props)
    }

```



##### 2.子传父

```js
子组件

<button @click="handle">点击</button>
import {ref} form 'vue'
setup(props,{emit}){
    handle=()=>{
        emit('add',{title:'子传父'})
    };
    return {
        handle
    }
}


```

```js
父组件

<Son @add="receive"></Son>
setup(){
    cosnt receive=(e:any)=>{
        console.log(e)
    };
    return {
        receive
    }
}

```

#### 生命周期钩子函数







#### props  ,context

##### 1.props

props 是响应式的。但不可以解构，否则会失去响应性

```js
setup(props,context){
    console.log(this)    //获取不到this  undefined
	console.log(props)   //获取父组件传过来的值
    console.log(context)  //上下文对象
}
```

##### 2.context

```
非响应式，可直接解构： setup(props, { attrs, slots, emit })
```

context可以访问的属性

root

parent

refs

attrs

listeners

isServer

ssrContext

emit





#### 怎么使用watch

watch有两个参数，1：要监听的值，2：回调函数，此回调有两个参数(newVal,oldVal)

##### 1.name为ref定义的变量时，第一个参数直接使用

```js
import {ref,reactive ,watch} form 'vue'
setup(){
    const name=ref('');
    watch(name,(newVal,oldVal)=>{
        console.log(newVal，oldVal)
    })
}

```

##### 2.data为reactive定义的变量需要没在监听时使用函数返回值的形式才能监听到

```js
import {ref,reactive ,watch} form 'vue'
setup(){
    const data=reactive({
        aa:['a','b'],
        bb:''
    })
    
    watch(()=>data.bb,(newVal,oldVal)=>{
        console.log(newVal，oldVal)
    })
}
```

##### 3.深度监听

```js
vm.$watch('data',callback,{
    deep:true
})
vm.data.cc=123
```

##### 4.监听多个变量

参数需要写成数组的形式，同时返回的参数也是数组

```js
setup(){
    const data=reactive({
        girls:['a','b','c'],
        selectGirl:'',
        selectGirlFun:(index)=>{
            data.selectGirl=data.girls[index]
        }
    });
    watch([()=>data.girls,()=>data.selectGirl],(newVal,oldVal)=>{
        console.log(newVal[1],oldVal[1])
    })
}
```



#### 怎么使用computed

##### 1.函数式写法

```js
import {ref,computed} form 'vue'

setup(){
    const num1=ref(1);
    const num2=ref(2);
    let sum=computed(()=>{
        return num1.value+num2.value
    });
    return {
        num1,
        num2,
        sum,
    }
}
```



##### 2.options写法

```js
import {ref,computed} form 'vue'

setup(){
    const num1=ref(1);
    const num2=ref(2);
    let mul=computed({
        get:()=>{
            return num1.value*10
        },
        set:(value)=>{
            return num1.value=value/10
        }
    })
    return {
        num1,
        num2,
        mul,
    }
}

```

##### 3.computed传参

```js
<div v-for="(item,index) in arr" :key="index" @click="handle(index)">
    {{item}}
</div>

import {ref,reactive,computed} form 'vue'
setup(){
    const arr=reactive([
        '哈哈','嘿嘿'
    ])
    const handle=computed(()=>{
        return function(index){
            console.log(index)
        }
    });
    return {
        arr,
        handle,
    }
}
```

#### 响应式api

##### 1.ref

  ref接收参数并将其包裹在一个带有 `value` property 的对象中返回，然后可以使用该 property 访问或更改响应式变量的值

```
const name=ref('')
return {
	name,
}
```

##### 2.reactive  

reactive  如果将对象分配为 ref 值，则通过 [reactive](https://v3.cn.vuejs.org/api/basic-reactivity.html#reactive) 方法使该对象具有高度的响应式

```js
 setup() {
     let name = ref('')
     let age = ref(0)
     let obj = reactive({
         name: name.value,
         age: age.value
      })
      return toRefs(obj)
  }
```

##### 3.toRef

  为 reactive 对象的属性创建一个 ref,这个 ref 可以被传递并且能够保持响应性

```js
setup(){
    const user=reactive({age:1});
    const age=toRef(user,'age');
    age.value++;
    console.log(user.age)  //2
    user.age++;
    console.log(age.value) //3
}

```

##### 4.toRefs

解构响应式对象数据

```js
<div>{{username}}<div>
<div>{{age}}<div>

import {reactive,toRefs} form 'vue'
setup(){
    const user=reactive({
        username:'hai',
        age:100
    })
    return {
        ...toRefs(user)
    }
}

```

##### 5.isRef、isProxy、isReactive、isReadonly

检查一个值/对象是否为一个 ref / proxy / reactive / readonly 对象



##### 6.readonly只读函数

被修改时会发出警告，但不会改变值

```js
import {readonly} from 'vue'
setup(){
    const info=readonly('只读');
    setTimeout(()=>{
        info='更新'     //只读，不会更改
    }，2000)
}
```



#### 组合式api

##### 1.setup  :在组件被创建之前，`props` 被解析之后执行。它是组合式 API 的入口

##### 2.生命周期钩子

created     ==>setup()

mounted   ==>onMounted,

updated     ==>onUpdated,

destroyed  ==>onUnmounted,

##### 3.provide,inject

provide 函数接收两个参数  provide (name,value)

​     name:定义提供property的name

​     value:property的值

inject函数有两个参数 inject(name,default)

​		name:接收provide提供的属性名

​		default:设置默认值，可选参数

使用ref,reactive添加响应式，在父组件或子组件都会修改 `info `的值

```js
//父组件
import {ref,provide} from 'vue'

setup(){
    let info=ref('aaa');
    setTimeout(()=>{
        info.value='bbb'
    },2000)
	provide('info',info);
    return {
        info
    }
}
```



```js
//子组件
<div>{{info}}</div>
import {inject} form 'vue'
setup(){
	const info=inject('info')
    setTimeout(()=>{
        info='ccc'
    },2000)
	return {
		info
	}
}
```

##### 4.h渲染函数

```js
import {h,ref,reactive} from 'vue'
setup(){
	const count=ref(0);
	const object=reactive({foo:'bar'});
	return ()=>h('div',[count.value,object.foo])
}
```

##### 5.getCurrentInstance 获取当前组价实例

```
import {getCurrentInstance } form 'vue'

setup(){
	const { proxy }=getCurrentInstance ()
	proxy.$attrs
	proxy.$data
	proxy.$emit
	proxy.$data
}
```





## CSS面试题

怎么实现响应式布局

怎么水平垂直居中一个元素

怎么兼容不同浏览器

web性能优化策略



#### 1.自适应布局/响应式布局

自适应布局：同一张网页自动适应不同大小的屏幕，根据屏幕宽度，自动调整网页内容大小。

响应式布局：可以自动识别屏幕宽度、并做出相应调整的网页设计，布局和展示的内容可能会有所变动。

区别：如果网页内容过多，整体会显得拥挤。所以响应式布局是自适应布局的改进，布局和展示的内容可能会有所变动。

响应式：

- 允许网页宽度自动调整

  ```
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  // viewport是网页默认的宽度和高度
  // 网页宽度默认等于屏幕宽度（width=device-width），原始缩放比例（initial-scale=1）为1.0 
  // 即网页初始大小占屏幕面积的100%
  ```

- 尽量少使用绝对宽度：使用百分比进行布局

- 相对大小的字体：字体也不能使用绝对大小（px），而只能使用相对大小（em）或者高清方案（rem）,rem不局限于字体大小，前面的宽度width也可以使用，代替百分比

- 流动布局（fluid grid）：各个区块的位置都是浮动的，不是固定不变的

- 选择加载CSS：

  ```
  <link rel="stylesheet" type="text/css" media="screen and (max-device-width: 400px)"
  　　href="tinyScreen.css" />
      或者：
      @import  url("tinyScreen.css") screen and (max-device-width: 400px);
  ```

  

- CSS的@media规则（媒体查询） 

  ```
  @media  screen and (max-device-width: 400px) {
  　　　　.column {
  　　　　　　float: none;
  　　　　　　width:auto;
  　　　　}
  
  　　　　#sidebar {
  　　　　　　display:none;    
  　　　　}
  
  　　}
  ```

  

- 图片的自适应（fluid image）

  ```
  img { max-width: 100%;}
  
  ```

  



#### 2.对BFC规范的理解

BFC 全称“块级格式化上下文”(Block Formatting Context)，对应的还有 IFC。BFC 类似一个“结界”，如果一个 DOM 元素具有 BFC，那么它内部的子元素不会影响外面的元素；外面的元素也不会影响到其内部元素。

应用场景：

-   解决浮动子元素导致父元素，高度坍塌的问题
-   解决文字环绕在float 四周的情况
-   解决边距重叠问题 （父子，兄弟，空元素等）

特性：

-   计算BFC的高度时，浮动子元素也参与计算
-   BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然
-   BFC的区域不会与float的元素区域重叠

形成条件:

- html 根元素

- float的值不是none

- position 的值不是static或者relative

- display的值是inline-block,table-cell,table-caption,flex,inline-flex

- overflow的值不是visible

  

#### link和@import的区别

link属于XHTML标签，而@import是CSS提供的。

（2）页面被加载时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载。

（3）import只在IE 5以上才能识别，而link是XHTML标签，无兼容问题。

（4）link方式的样式权重高于@import的权重。

（5）使用dom控制样式时的差别。当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。


#### 介绍一下 Sass 和 Less 是什么？它们有何区别？

Sass (Syntactically Awesome Stylesheets)是一种动态样式语言，语法跟css一样(但多了些功能)，比css好写，而且更容易阅读。Sass语法类似与Haml，属于缩排语法（makeup），用意就是为了快速写Html和Css。

Less一种动态样式语言. 将CSS赋予了动态语言的特性，如变量，继承，运算， 函数. LESS 既可以在客户端上运行 (支持IE 6+, Webkit, Firefox)，也可一在服务端运行 (借助 Node.js)。

区别：

(1)Sass是基于Ruby的，是在服务端处理的，而Less是需要引入less.js来处理Less代码输出Css到浏览器，也可以在开发环节使用Less，然后编译成Css文件，直接放到项目中，也有Less.app、SimpleLess、CodeKit.app这样的工具，也有在线编译地址。

(2)变量符不一样，less是@，而Scss是$，而且变量的作用域也不一样，后面会讲到。

(3)输出设置，Less没有输出设置，Sass提供4中输出选项：nested, compact, compressed 和 expanded。

(4)Sass支持条件语句，可以使用if{}else{},for{}循环等等。而Less不支持。



#### css中常见长度单位

1.px像素：

   相对长度单位,像素px是相对于显示器屏幕分辨率而言的。

2.em与rem（相对长度单位）：

​    em  : 继承父级元素的字体大小

​    rem ：1,其值不是固定的

​                2,相对于HTML根元素的字体大小（font-size）来计算的长度单位,如果你没有设置html的字体大小，就会以浏览器默认字体大小，一般是16px

3.vw,vh

​     vw是相对视口（viewport）的宽度而定的，长度等于视口宽度的`1/100`假如浏览器的宽度为200px，那么1vw就等于2px（200px/100）

​     vh是相对视口（viewport）的高度而定的，长度等于视口高度的`1/100`假如浏览器的高度为500px，那么1vh就等于5px（500px/100）

4. %

   一般来说就是相对于父元素

   1、对于普通定位元素就是我们理解的父元素

   2、对于position: absolute;的元素是相对于已定位的父元素

   3、对于position: fixed;的元素是相对于ViewPort（可视窗口）

####  居中布局

-   水平居中

1.  行内元素: `text-align:center`
2.  块级元素: `margin:0 auto`
3.  绝对定位和移动: `absolute + transform`
4.  绝对定位和负边距: `absolute + margin`
5.  flex布局: `flex + justify-content:center`

- 垂直居中

  1.子元素为单行文本: `line-height:height`

  2.`absolute + transform`

  3.`flex + align-items:center`

  4.table: `display:table-cell; vertical-align: middle`

  5.利用position和top和负margin

- 水平垂直居中

​         1已知元素宽高:绝对定位+margin:auto:

```
 div{
      width: 200px;
      height: 200px;
      background: green;
 
      position:absolute;
      left:0;
      top: 0;
      bottom: 0;
      right: 0;
      margin: auto;
  }
```



​         2 已知元素宽高:  绝对定位+负margin

```
 div{
      width: 200px;
      height: 200px;
      background: green;
 
      position:absolute;
      left:0;
      top: 0;
      bottom: 0;
      right: 0;
      margin: auto;
   }
```

​         3 absolute+transform

```
 div{
     width: 200px;
     height: 200px;
     background: green;
 
     position:absolute;
     left:50%;    /* 定位父级的50% */
     top:50%;
     transform: translate(-50%,-50%); /*自己的50% */
   }
```

​         4 flex + justify-content + align-items

```
.box{
   height:600px;
 
   display:flex;
   justify-content:center;  //子元素水平居中
   align-items:center;      //子元素垂直居中
     /* aa只要三句话就可以实现不定宽高水平垂直居中。*/
    }
  .box>div{
    background: green;
    width: 200px;
    height: 200px;
   }
```

怎么实现两栏布局

```
.right{
    width:100px;
    height:100px;  
    border:1px solid #000;
}
.left{
    height:100px;
    border:1px solid #000;
}
```

  1absolute + margin-left方案

```
.left{
    margin-right:100px;
}
.right{
    position:absolute;
    right:0;
}

```

  2 flex方案

```
.wrapper{
    display:flex;
    align-items:flex-start;
}
.left{
    flex:1;
}
```

  3  float + margin-left方案

```
.wrapper{
    overflow:hidden;
}
.left{
   margin-right:100px;
}
.right{
    float:right;
}

```

#### flex布局 

flex弹性布局，可以简便、完整、响应式地实现各种页面布局, 容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）

（1）flex-direction：决定主轴的方向

​			row（默认值）：主轴为水平方向，起点在左端。

​			row-reverse：主轴为水平方向，起点在右端。

​			column：主轴为垂直方向，起点在上沿。

​			column-reverse：主轴为垂直方向，起点在下沿。

（2）flex-wrap：换行

​			nowrap（默认）：不换行。

​			wrap：换行，第一行在上方。

​			wrap-reverse：换行，第一行在下方。

（3）flex-flow：flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

（4）justify-content：主轴对齐方式

​			flex-start（默认值）：左对齐

​			flex-end：右对齐

​			center： 居中

​			space-between：两端对齐，项目之间的间隔都相等。

​			space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

​	5）align-items：侧轴对齐方式

​			flex-start：交叉轴的起点对齐。

​			flex-end：交叉轴的终点对齐。

​			center：交叉轴的中点对齐。

​			baseline: 项目的第一行文字的基线对齐。

​			stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。









## HTML面试题

## NODE面试题

nodejs使用场景

使用npm的好处

同步与异步怎么理解

fork是什么

nodejs能否充分利用多核处理器

## 谈谈对前后端分离的理解

调试代码使用什么方式

es6   对Promise的理解、Promise常用的方法、 对async/await 的理解、Set/Map

jquery

js     箭头函数/普通函数、http请求及响应过程、 数组的遍历方法，节流、防抖、cookie/localStorage/sessionStorage、深拷贝/浅拷贝区别及实现方法、堆内存/栈内存、

​         js   时间执行机制、异步执行顺序、实现call/apply 及 bind 函数、forEach/map区别

vue     组件的通讯方式、子组件怎么修改父组件数据、keep-live怎么理解 、路由导航钩子？起到哪些作用、 new操作符具体做了什么、vue中data为什么是函数、 

​         图片懒加载、双向数据流/单项数据流，双向绑定原理， vue中key的作用    、$nextTick原理及作用、vuex，编程式路由/声明式路由传参方式

怎么优化项目
