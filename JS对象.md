# JS对象
## 声明对象的两种语法
写法：
let obj = {'name': 'frank', 'age': 18}	//简单写法
let obj = net Object({'name': 'frank'})   //标准写法
console.log({'name': 'frank', 'age': 18 })	//匿名对象
细节：
键名是字符串，不是标识符，可以包含任意字符
引号可以省略，但是省略后只能写标识符。但就算省略了，键名也还是字符串。

## 如何删除对象的属性
delete obj.xxx 或 delete obj['xxx']
这样可以删除obj的xxx属性。注意区分属性值为undefined和不含属性名。
不含属性名：'xxx' in obj === false
含有属性名但值是undefined： 'xxx' in obj && obj.xxx === undefined
obj.xxx === undefined 不能判断'xxx' 是否是obj的属性。
类比：你有没有带卫生纸。没有→不含属性；有，但没带→有但值是undefined。

## 如何查看对象的属性
查看自身所有属性： Object.keys(obj)
查看自身+共有属性：console.log(obj)或依次用Object.keys打印出obj.__proto__
判断一个属性是自身还是共有：obj.hasOwnProperty('toString')
查看一个属性：
中括号语法： obj['key'] // 最推荐使用的写法
点语法： obj.key
坑新人语法： obj[key] //变量key值一般不为'key'

## 如何修改或增加对象的属性
直接赋值：
let obj = {name: 'frank'} // name 是字符串
obj.name = 'frank' // name是字符串
obj['name'] = 'frank'
obj[name] = 'frank' // 错，因为name的值不能确定
obj['na' + 'me'] = 'frank'
let key = 'name'; obj[key] = 'frank'
let key = 'name'; obj.ket = 'frank' 错，因为obj.key 等价于 obj['key']
批量赋值：
Object.assign(obj, {age: 18, gender: 'man'})

修改或增加共有属性：
无法通过自身修改或增加共有属性。
obj.__proto__.toString = 'xxx' 这样所有的对象方法都会被修改。
但一般来说不要修改原型，会引起很多问题。

修改隐藏属性：
不推荐用__proto__：
let obj = {name: 'frank'}
let obj2 = {name: 'jack'}
let common = {kind: 'human'}
obj.__proto__ = conmon    obj2.__proto__ = common
推荐用Object.create：
let obj = Object.create(common)
obj.name = 'frank'
let obj2 = Object.create(common)
obj2.name = 'jack'
如果要改就一开始改好，不要中途再修改。

### 'name' in obj和obj.hasOwnProperty('name') 的区别
'name' in obj：是检测对象obj中是否存在'name' 这个属性，obj本身或者原型中有的话都会返回true.
obj.hasOwnProperty('name')：检测对象obj中是否存在'name'属性，仅obj自身中有此属性时才返回true.
