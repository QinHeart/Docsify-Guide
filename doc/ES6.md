# ES6

## 面向对象编程

> 把事物分解为一个一个对象，然后由对象进行分工，合作

特征：封装、继承、多态



### ES6中的类和对象

1. 创建类：

   ```
   class name{
   	constructor(name){
   		this.name = name;
   	}
   	sing(songName){
   		console.log(this.name + '唱歌' + songName)
   	}
   }
   ```

   `constructor可以接受传递过来的参数，同时返回实例对象`

   创建实例

   ```
   var xx = new name()
   ```

   `类必须使用new实例化对象`

2. 继承 `extends`

   ```
   class Son extends Star{}
   ```

   - `super`关键字可以用于访问和调用对象父类上的函数

     ```
     class Son extends Father{
         constructor(x,y){
             super(x,y)
         }
     }
     ```

     ```
     say(){
     	console.log(super.say() + "的儿子");
     }
     ```

     `super` 必须放到子类 this 之前

     ```
     constructor(x,y){
          super(x,y)
          this.x = x,
          this.y = y
     }
     ```


 3. 注意点

    - 先定义类，才能实例化

      函数写到 constructor 中

      ```
      constructor(x, y) {
      		(this.x = x), (this.y = y), this.sum();
      	}
      	sum() {
      		console.log(this.x + this.y);
      	}
      ```

    - 使用共有的属性和方法必须要加 this

    - 类中 this 指向问题
      - constructor 中 this 指向 创建的实例
      - 函数中的 this 指向调用者