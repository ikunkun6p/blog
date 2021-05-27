# JS的执行时机
## 为什么代码会打印出6个6
首先用let声明了一个全局变量i，初始值为0。然后通过for循环操作 i，并设置了一个定时器setTimeout。
但在JS的函数中for循环任务优先级要高于定时器setTimeout，所以会先完成for循环的计算。
（不断判断 i 是否小于6，如若不是则每次给 i 的值加1，完成这一步后 i 的值已经变成了6，此时setTimeout开始运行，此时函数作用域内 i 的值已经是6）

## 打印0、1、2、3、4、5
```
for(let i = 0; i<6; i++){
  setTimeout(()=>{ 
    console.log(i)   // 就是打印出每一次循环 i 的值
  },0)
}
```

##  其他方法
```
let i = 0
for(i = 0; i<6; i++){
    ! function(i){
        setTimeout(()=>{
            console.log(i)
        },0)
    } (i)
}
```
