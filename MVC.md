# 什么是MVC
MVC是一种架构设计模式，它通过关注点分离鼓励改进应用程序组织。
MVC包括三类对象，将他们分离以提高灵活性和复用性。
M---Model（数据模型）负责操作所有数据
V---View（识图）负责所有UI界面
C---Controller（控制器）负责其他
MVC用一种业务逻辑、数据、界面显示分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。
### MVC示例
Model：用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法，会有一个或多个视图监听此模型。一旦模型的数据发生变化，模型将通知有关的视图。
```
Model = {
  data : {需要用到的数据},
  create : {增数据},
  delete : {删数据},
  updata : {更新数据},
  get : {获取数据}
}
```
View---在屏幕上的表示，描绘的是model的当前状态。当模型的数据发生变化，视图相应地得到刷新自己的机会
```
View = {
  el: null,
  html: ` `,
  init() {初始化页面},
  render() {渲染页面}
}
```
Controller---定义用户界面对用户输入的响应方式，起到不同层面间的组织作用，用于控制应用程序的流程，它处理用户的行为和数据model上的改变
```
Controller = {
  init(){
    View.init()View初始化
    View.render()//第一次渲染
    event : {用哈希表记录}
    Controtller.autoBindEvents()//自动绑定事件 
  }
}
```

## EventBus 有哪些 API，是做什么用的，给出伪代码示例
EventBus基本的api有on（监听事件），trigger(emit)（触发事件）,off（取消监听）方法。 用于模块间的通讯，view组件层面，父子组件、兄弟组件通信都可以使用eventbus处理。
```
//EventBus.js
class EventBus{
    constructor(){
        this._eventBus =$(window)
    }
    on(eventName, fn){
        return this._eventBus.on(eventName,fn)
    }
    trigger(eventName,data){
        return this._trigger.tiggger(eventName,data)
    }
    off(eventName, fn){
        return this._eventBus.off(eventName,fn)
    }
}
export default EventBus
//new.js
import EventBus from 'EventBus.js'
const e = new EventBus()
e.on()
e.trigger()
e.off()
```

## 表驱动编程
所谓表驱动法(Table-Driven Approach)，简单讲是指用查表的方法获取值。在数值不多的时候我们可以用逻辑语句(if 或case)的方法来获取值，但随着数值的增多逻辑语句就会越来越长，此时表驱动法的优势就显现出来了。表驱动法是一种编程模式，从表(哈希表)里面查找信息，只将重要的信息放在表里，然后利用表来编程，与逻辑语句相比较有着更稳定的复杂度。
说通俗一点，就是将许多类似但不重复的代码，取出重要的数据做成表再调用。例如：
```
function weekday(day) {    if(day&7===0){
      return '星期天';
    }
    else if(day%7===2){
      return '星期二';
    }
    else if(day%7===3){
      return '星期三';
    }
    else if(day%7===4){
      return '星期四';
    }
    else if(day%7===5){
      return '星期五';
    }
    else if(day%7===6){
      return '星期六';
    }
}
```
## 如何理解模块化
模块化可以让面条式代码（写的烂的代码）变成结构分明逻辑清晰的框架式代码。

在Java中有一个重要带概念——package，逻辑上相关的代码组织到同一个包内，包内是一个相对独立的王国，不用担心命名冲突什么的，那么外部如果使用呢？直接import对应的package即可 import java.util.ArrayList; 遗憾的是JavaScript在设计时定位原因，没有提供类似的功能，开发者需要模拟出类似的功能，来隔离、组织复杂的JavaScript代码，我们称为模块化。 一个模块就是实现特定功能的文件，有了模块，我们就可以更方便地使用别人的代码，想要什么功能，就加载什么模块。当然，模块开发需要遵循一定的规范。

1. 代码模块化之后,无论是代码的整体性还是后期进行代码维护都变的简单明了起来。 一个模块实现一个特定功能，想要删改就可以很快定位。
2. 模块化可以降低代码耦合度，减少重复代码，提高代码重用性。
3. 一个模块就是一个独立的文件，该文件内部的所有变量，外部无法获取，如果你希望外部能够读取模块内部的某个变量，就必须使用export命令输出该变量，使用import命令输入其他模块提供的功能。

