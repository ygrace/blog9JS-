# JS对象的用法
## 定义：
无序数据组合
键值对的集合(key是属性名，value是属性值)

## 写法：
~~~javascript
let obj = {'name':'frank', 'age': 18}
let obj = new Object({'name': 'frank', 'age': 18})
console.log({'name': 'frank', 'age': 18})
~~~
## 注意细节：
* 键名是字符串，永远都是字符串。不是标识符，可以包含任何字符，只要是unicode有的
* 引号可省略，省略之后只能写标识符
* 就算键名省略了，它还是字符串
~~~javascript
var obj = {2: '2222'}
Object.keys(obj)
'2'
~~~
~~~javascript
var obj = {'  ' : '222'}
Object.keys(obj)
         // key是两个空格，也是字符串
~~~
* key永远都是字符串 
## 一些奇怪的属性名
* 所有的属性名会自动变成字符串
  ~~~javascript
    let obj ={
        1: 'a'
        3.2: 'b'
        1e2: true
        1e-2: true
        .234: true
        oxFF: true
    };
    Object.keys(obj)=['1', '3.2', '1e2', '1e-2', '.234', 'oxFF'] 
  ~~~
## 用变量做属性名
之前都是用常量做属性名，变量也可以做属性名
~~~javascript
let p1 = 'name'
let obj = {p1: 'frank'} //这样写，属性名为'p1'
let obj = {[p1]: 'frank' } //这样写，属性名为'name'
~~~
不加[]的属性名会自动变成字符串，加了[]的属性名，现变量求值，再把值当成字符串
~~~javascript
let obj = {
    [1+2+3+4: ''哈哈]
}
{10 : '哈哈'}    //10是字符串
~~~
## 对象的隐藏属性
* JS中每个对象都有隐藏属性
* 这个隐藏属性储存着其共有属性组成的对象的地址
* 这个共有属性组成的对象叫做原型
* 隐藏属性储存着原型的地址




        