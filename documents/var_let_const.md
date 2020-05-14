# var let const

## 作用域

- 全局作用域 [ES5]
- 函数作用域 [ES5]
- 块级作用域 [ES6]

* 变量提升
* 暂时性锁区

在未申明之前调用变量：

- var -> undefined
- let -> ReferenceError; let 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”

```
let a = 'outside';
if(true) {
   console.log(a);//Uncaught ReferenceError: a is not defined
    let a = "inside";
}
```

当前作用域顶部到该变量声明位置中间的部分，都是该 let 变量的死区，在死区中，禁止访问该变量。由此，我们给出结论，let 声明的变量存在变量提升， 但是由于死区我们无法在声明前访问这个变量。

## 4.全局变量 vs 全局对象的属性

ES5 中全局对象的属性与全局变量基本是等价的，但是也有区别，比如通过 var 声明的全局变量不能使用 delete 从 window/global （ global 是针对与 node 环境）上删除，不过在变量的访问上基本等价。

ES6 中做了严格的区分，使用 var 和 function 声明的全局变量依旧作为全局对象的属性，使用 let, const 命令声明的全局变量不属于全局对象的属性。
