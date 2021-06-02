
## jQuery 如何获取元素

$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素

$('div').has('p'); // 选择包含p元素的div元素

$('div').not('.myClass'); //选择class不等于myClass的div元素

$('div').filter('.myClass'); //选择class等于myClass的div元素

$('div').first(); //选择第1个div元素

$('div').eq(5); //选择第6个div元素

## jQuery 的链式操作是怎样的

$('div').find('h3').eq(2).html('Hello');

分解开来，就是下面这样：

$('div') //找到div元素

　.find('h3') //选择其中的h3元素
 
.eq(2) //选择第3个h3元素

.html('Hello'); //将它的内容改为Hello

## jQuery 如何创建元素

创建元素只需要把新元素放到jQuery构造的函数里就可以了
```
$('<p>Hello</p>');
$('<li class="new">new list item</li>');
$('ul').append('<li>list item</li>');
```
## jQuery 如何移动元素

第一种方法是使用 .insertAfter，将 div 元素移动 p 元素后面：
```
$('div').insertAfter($('p'));
```

第二种方法是使用 .after()，达到同样的效果
```
$('p').after($('div'));
```
## jQuery 如何修改元素的属性
```
$("div").clone() //只克隆了结构，事件丢失
$("div").clone(true) //结构、事件与数据都克隆
```
