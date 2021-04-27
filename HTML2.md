## a标签的用法
超链接文本标签，里面装文本或者图片都可以。点击里面的文字（图片）就会跳转到href属性中相应的地址。
```
  <a href="//baidu.com">百度</a>  这样会自动选择相应的协议。
  <a href="#" target="_blank"><img src="xxx.jpg" /></a>   //样里面就包含了一张图片
  <a href="javascript:;">a</a> // 点这个a什么都不会做
  <a href="mailto:邮件地址>发邮件</a>
  <a href="tel:电话号码">打电话</a> 
```
## img的用法
图片标签，用来展示图片，会发送get请求。是一个可替换的元素，但没有讲被谁替换。有onload和onerror的事件。
```
  <img src="图片路径" alt="图片裂开了" weight="400" height="400"> //alt是图片加载不出来的时候替换显示的内容；
  同时设置宽高会改变图片比例，一般只设置一个
```
## table的用法
表格，一般用来展示数据。
这节课有讲到这几个属性：
table-layout: auto; 根据内容调整大小
table-layout: fixed; 平均显示内容
border-collapse: collapse 合并表格（也可以叫消除间隔）
border-spacing: 0 td的间距，一般用px做单位
```
<table>
    <thead> // 表头
        <tr>  // table row 表格的一行
            <th colspan="2">The table header</th> //colspan合并单元格暂时没讲到
        </tr>
    </thead>
    <tbody> // 表的主体部分
        <tr>
            <td>The table body</td> //td指单个单元格
            <td>with two columns</td>
        </tr>
    </tbody>
    //  缺了tfoot标签，一般表示表格最底下的一行。
</table>

```

## 感想
html和CSS 比起原生js的算法 获取数据等操作显得太简单了，原生CSS就是写起来比较繁杂，又难以复用，懒人都是用bootstrap直接改
别的没有太多感想了，HTML用多了案例看多了跟着做就会了。
别的标签还有input、textarea、select、form等。
