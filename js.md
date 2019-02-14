### 1. 介绍js 的数据类型
    6中简单（基本）数据类型  和   1种复杂数据类型 （Object）
    基本类型
    String
    Number
    Boolean
    null
    undefined
    symbol  
    ECMAScript 2015 新增: Symbol  (创建后独一无二且不可变的数据类型 )
    链接：http://es6.ruanyifeng.com/#docs/symbol
    引用类型
    object
    Array Date RegExp  Function
    基本包装类型： Boolean  Number  String 
    单体内置对象： Global对象   Math对象

### 2.typeof 
    typeof 1 // 'number'
    typeof '1' // 'string'
    typeof undefined // 'undefined'
    typeof true // 'boolean'
    typeof Symbol() // 'symbol'
    typeof b // b 没有声明，但是还会显示 undefined

    typeof function(){} // 'Function'
    typeof 对于对象，除了函数都会显示 object
    typeof [] // 'object'
    typeof {} // 'object'
    typeof console.log // 'function'


