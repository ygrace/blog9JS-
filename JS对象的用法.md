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


## 删除属性
1. delete obj.xxx  或者 delete obj['xxx']
2. 区分属性值为undefined和不含属性名
   * 不含属性名
     'xxx' in obj === false
   * 含有属性名，但属性值为undefined
     'xxx' in obj && obj.xxx === undefined
     注意：obj.xxx === undefined不能判定'xxx'是否为obj的属性，有可能它的属性值为undefined,也有可能不存在'xxx'属性  
## 查看属性（读属性）
1. 查看自身所有属性
    Object.keys(obj)
2. 查看自身+共同属性
    console.dir(obj)
    或者自己一次用Object.keys(obj)打印出obj.proto  不推荐
3. 判断一个属性是自身的还是共有的
    obj.hasOwnProperty('toString')
4. 查看属性值
    Object.values(obj)
5. 查看属性名和属性值
    Object entries(obj)  或者 obj

## 原型
* 每个对象都有原型，原型里存着对象的共有属性
* 对象的原型也是对象，因此对象的原型也有原型，是对象的根
* 这个原型的原型是null

## 两种方法查看属性
* 中括号法
  obj['key']
* 点语法
  obj.key
* 坑新人语法  obj[key] 是错的，变量key一边不为'key'
## 修改或增加属性（写属性）
* 直接赋值
  ~~~javascript
  let obj = {'name': 'frank', 'age': 18} // 'name','age'是字符串
  obj.name = 'frank'  // name 是字符串
  obj['name'] = 'frank'
  obj[name] = 'frank' // 错的，name不确定
  obj['na' + 'me'] = 'frank'
  let key = 'name'; obj[key] = 'frank'
  let key = 'name'; obj.key = 'frank'  // 错 obj.key = obj['key']
* 批量赋值
  Object.assign(obj, {'name': 'frank', 'age': 18})
* 修改或增加共有属性
  无法通过自身修改或增加共有属性
~~~javascript
obj = {};
obj1 = {};
obj.toString = 'xxx';  //只会修改obj自身的属性， obj2.toString还是在原型上
~~~
* JS脆弱的地方，只要找到了obj.proto就可以修改原型，但别轻易尝试
* 修改隐藏属性，要改就在开始该，别后来再改，一创建就指定原型
~~~javascript
let obj = Object.create(common);
obj.name = 'frank';
let obj2 = Object.create(common);
obj2.name = 'jack';
~~~








        