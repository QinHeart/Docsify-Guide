# JavaScript

## 第一章 基础知识

### 变量

```
let name = 'zs';
```

命名规则：

`驼峰命名法`：首个单词字母小写，后续单词首字母大写

`蛇形命名法`：单词全部小写，用下划线_隔开

### 常量

```
const COUNT  =10;
```

只读，不能二次赋值

命名规则：建议全部大写，多个单词用下划线_隔开

### 数据类型

1. `typeof`
2. `instanceof` 可判断对象类型
3. `isArray()` 判断是否为数组

#### Number

- 进制

​	`0b` 开头表示二进制

​	`0o` 开头表示八进制

​	`0x` 开头表示十六进制

- 特殊数字

  `isNaN`，true 代表非数字，false 代表数字

#### String

- 转义字符

- 模板字符串

  访问变量或表达式的值，可以使用`${}`把其中的变量值或表达式转换成字符串

  ```
  let a = 5;
  `a + 5 = ${a + 5}`
  ```

#### Null 与 Undefined

根据现行 ECMASCript 规范，使用 typeof 获取 null 类型会返回 Object

- `null` 代表已经定义的，只不过值是空值

  > 当收集用户信息时，如果用户没有输入信息，就应该使用 null

  ```
  const inputValue  = null;
  ```

  

- `undefined` 表示未定义的，不存在

#### Object

`无效字符`:属性名中包含中划线、空格等

```
let someObj = {
	"some prop":"value"
}
```

`访问含无效字符的属性`要使用方括号访问

```
someObj["some prop"]
```

修改对象属性的值，可以使用 `=` 赋予新值

```
someObj["some prop"] = "other value"
```

可以把属性的值放到变量中，使用变量的值作为对象的属性名

```
let prop = "some prop"
someObj[prop] = "other value"
```

：如果指定了对象中不存在的属性，就会将一个新的属性添加到对象中

#### Symbol

#### Array

> 建议数组中存放统一的类型

```
let nums = [1,2,3];
nums[0] = 1;
nums[0] = 5;
```

### 数据类型转换

- 隐式类型 ==> 自动转换

  1. 数字类型与字符串类型相`加`，转化为`字符串`

  2. 数字类型与字符串类型相`减`，转化为`数字`
  3. 数字类型与布尔值计算，布尔值转化为数字 `false => 0`

- 显示类型转换

  1. Nmber（）调用这个方法会转换成数字类型

     ```
     Number('123')  //123
     Number('123a')  //NaN
     Number('undefined') //NaN
     Number(false)    // 0
     Number(true)     //1
     Number(null) //0
     ```

  2. parseInt()转换成整数并取整直接舍去小数

     ```
     parseInt(123.12) //123
     parseInt(true)   //NaN
     parseInt('123a') //123
     //如果parseInt（number，n)中有两个参数代表number是以n为进制转换成十进制
     parseInt(12,8) //12
     ```

  3. String ()转换成字符串

     ```
     String(123) //123
     ```

  4. toString()

     ```
     var a
     a.toString() //报错
     var a = 123'
     a.toString() //'123'
     var c = null
     c.toString() //报错
     当toString（N)用参数时表示一个十进制的数转换成n进制的数
     var d = 10
     d.toString(2) //'1010
     ```

## 第二章 运算符

- `%`取模
- `3 ** 2` 幂运算，左边为底数，右边为指数
- `= = =`是严格的比较方式，不会发生类型转换，建议使用

#### Nullish Coalescing

`空值合并`，ES2020规范中定义，用`??`表示，只有当左侧操作数为 null 或 undefinded 时候，才会使用右侧的值，负责返回左侧的值

```
"" ?? 10; // ""
false ?? "no"; // false
null ?? 100; // 100
undefinded ?? "empty"; // "empty"
```

> 使用场景：把"",false,0等当作正常值，只有遇到 null 或 undefined 时，才设置默认值

## 第三章 流程控制

1. `if else`

2. `if,else if,else`

3. `switch case`

4. `while`

5. `do while`

6. `for`

7. `break`

   退出整个循环

8. `continue`

   跳过本次循环，继续下一次

9. `label`(不常用)



## 第四章 函数

`定义函数` 

```
function sayHello(name){
    console.log("Hello " + name); || return "Hello " + name;
}
sayHello("kqn") || console.log(sayHello(kqn))
```

### 箭头函数

`简单使用`

```
let sum = (x,y)=>{
    return x + y;
}
console.log(sum(1,2));
```

### 可变长度参数

#### arguments

> 除了`箭头函数`以外的普通函数中，都有一个隐式的 arguments 变量，存放所有传递过来的值
>
> 不是数组，`没有数组内置的方法`

```
function sum(){
    let outcome = 0;
    for(let i = 0;i<arguments.length;i++){
        outcome += arguments[i]
    }
    return outcome
}
console.log(sum(1,2,3));
```

#### 剩余参数

> `rest`运算符，使用`...`表示，使用`rest`定义的参数是一个真正的数组
>
> `箭头函数`可用，将一个不定数量的参数表示为一个数组
>
> 是数组，`有数组内置的方法`

```
let sum = (...theArgs) => {
	let total = 0;
	for (let arg of theArgs) {
		total += arg;
	}
	return total;
};
console.log(sum(1, 2));
```

#### 临时隔离区

使用`let`关键字定义的变量不能在初始化之前访问，因为它的声明被放到临时隔离区

#### 闭包

> 只调用一次函数，就可以完成所有的业务逻辑

#### 递归

> 对于一个复杂问题，把它分解为子问题，再对子问题继续划分，直到子问题可以求出答案

## 第五章 数组

### 创建数组

1. let arr = [1,2,3]

2. let arr_1 = new Array(5)

   let arr_2 = new Array("a","b","c")

   let arr_3 = Array.of(5) ==> `传给它的参数都将作为数组的原始元素`

3. let arr = Array.from([3,4,5]) ==> `将其他数组元素复制到新数组`

   `浅复制`

### 删除元素

#### delete

删除数组元素，但对应元素索引会保留下来，数组长度不会发生变化

```
let arr = [1,2,3]
delete arr[1] ==> [1,empty,3]
```

要判断索引元素是否在数组中，可以使用`in`

```
1 in arr;
arr[1] ==> undefined
```

这里要注意，arr[1]返回`undefined`是因为使用`delete`删除元素导致它不存在，但如果元素设置为`undefined`，那它还会存在于数组中，值为`undefined`

#### splice

删除数组并让数组向前移动

````
splice(开始索引，结束索引，添加元素)
````

#### length

修改数组长度来删除末尾数组

### 栈和队列

#### push() | unshift()

元素添加到数组末尾

```
let arr = [1,2]
arr.push(3,4,5) ==> [1,2,3,4,5]
```

#### pop() | shift()

从数组末尾删除一个元素，不需要参数

```
arr.push() ==> [1,2,3,4]
```

### 数组遍历

1. 传统

```
for (let i = 0; i < arr.length; i++) {
	console.log(arr[i]);
}
```

2. ES6

```
let arr = [0,1,2,3]
for(let item of arr){
	console.log(item)
}
```

#### forEach()

```
forEach(当前遍历到的元素，当前元素索引，数组本身)
```

> 无返回值，改变原数组，会导致难以发现的错误，如非必要，尽量维持原数组

#### map()

> 返回新数组，通常用 map() 对数组进行变换，参数与 forEach 相同

```
let arr = [1,2,3]
let newArr = arr.map(v => v + 2)
```
map()和forEach()不会对空位执行回调函数

#### reduce()

遍历对数组中的元素，然后返回合并后的单一结果


reduce回调函数中的参数：`每次调用后返回的值，当前遍历的元素，当前元素索引，数组本身`

`reduce()除了接受回调函数外，还可以接收第二个函数，指定第一次调用回调函数的初始值`

```
let arr = [1, 2, 3, 4, 5];
let sum = arr.reduce((acc, cur) => acc + cur, 0); | let sum = arr.reduce((acc, cur) => acc + cur);
console.log(sum);
```

`数据流处理`

```
var sum = [1, 2, 3, 4, 5].map((i) => i + 2).reduce((acc, cur) => acc + cur,0);
```

### 数组过滤
