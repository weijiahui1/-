### 1. 介绍js的数据类型
    6中简单（基本）数据类型  和   1种复杂数据类型 （Object）
    1) 基本类型
        String
        Number
        Boolean
        null
        undefined
        symbol  
        ECMAScript 2015 新增: Symbol  (创建后独一无二且不可变的数据类型 )
        
    链接：http://es6.ruanyifeng.com/#docs/symbol
    2) 引用类型
        object
        Array  Date  RegExp  Function
        
    基本包装类型： Boolean  Number  String 
    单体内置对象： Global对象   Math对象
    
### 2. 介绍js有哪些内置对象？
    Object 是 JavaScript 中所有对象的父对象
    数据封装类对象：Object、Array、Boolean、Number 和 String
    其他对象：Function、Arguments、Math、Date、RegExp、Error
    
    参考：https://www.ibm.com/developerworks/cn/web/wa-objectsinjs-v1b/index.html
    
### 3. 请指出 JavaScript 宿主对象和原生对象的区别？
    宿主对象 主要是指 DOM和BOM
    原生对象 是Object、Function、Array、String、Boolean、Number、Date、RegExp、Error、Math等对象。

### 4. typeof 
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

### 5. Object.prototype.toString.call()
    Object.prototype.toString.call(1) // "[object Number]" 
    Object.prototype.toString.call('hi') // "[object String]" 
    Object.prototype.toString.call({a:'hi'}) // "[object Object]" 
    Object.prototype.toString.call([1,'a']) // "[object Array]" 
    Object.prototype.toString.call(true) // "[object Boolean]" 
    Object.prototype.toString.call(() => {}) // "[object Function]" 
    Object.prototype.toString.call(null) // "[object Null]" 
    Object.prototype.toString.call(undefined) // "[object Undefined]" 
    Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"
    
### 6. js实现数值千分位
    number.toLocaleString() 
    
### 


