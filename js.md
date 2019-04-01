### 1. 介绍js的数据类型
    6中简单（基本）数据类型  和   1种复杂数据类型 （Object）
    1) 基本类型
        String
        Number
        Boolean
        null
        undefined
        symbol --- ECMAScript 2015 新增: Symbol  (创建后独一无二且不可变的数据类型 )
        
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
```javascript
Object.prototype.toString.call(1) // "[object Number]" 
Object.prototype.toString.call('hi') // "[object String]" 
Object.prototype.toString.call({a:'hi'}) // "[object Object]" 
Object.prototype.toString.call([1,'a']) // "[object Array]" 
Object.prototype.toString.call(true) // "[object Boolean]" 
Object.prototype.toString.call(() => {}) // "[object Function]" 
Object.prototype.toString.call(null) // "[object Null]" 
Object.prototype.toString.call(undefined) // "[object Undefined]" 
Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"
```    
### 6. js实现数值千分位
    number.toLocaleString() 
    
### 7. 上下文this
    1.函数直接用圆括号运行，上下文是 window
    2.对象打点调用,上下文是这个对象
    3.数组（类数组）中枚举出函数，然后运行，上下文是这个类数组对象
    fun2 函数里面的this
    4.定时器调用函数，上写文是 window
    5.被当做事件处理函数，上写文是触发事件的DOM元素
    6.用new调用函数，上下文是函数体内秘密创建的空白对象
    7.用apply、call执行上下文
### 8. apply、call和bind
    apply() 和 call()
    第一个参数： 指定 this 的值
    第二个参数：实际的参数 apply 是数组 call 是一个一个传递
    
    bind
    .call() 或者 .apply() 方法会立即执行，如果函数有返回值会获得返回值
    .bind() 方法不会立即执行目标函数，而是返回一个原函数的拷贝，并且拥有指定this值和初始化函数

```javascript
function a() {}
console.log(typeof a.bind() === 'function'); // 返回是true，先证明a.bind()是一个函数
console.log(a.bind()); // 输出function a() {}，跟原函数一样
console.log(a.bind() == a); // false
console.log(a.bind() === a); // false 不管是 === 还是 == 都是false，证明是拷贝出来一份而不是原先的那个函数
```
### 9.模拟实现bind方法
```javascript
// 判断当前环境的Function对象的原型上有没有bind这个方法，如果没有，那我们就自己添加一个
if (!Function.prototype.bind) {
  /**
   * 添加bind方法
   * @param oThis 目标对象
   * @returns {function(): *} 返回的拷贝函数
   */
  Function.prototype.bind = function(oThis) {
    if (typeof this !== 'function') {
      // closest thing possible to the ECMAScript 5
      // 最接近ECMAScript 5的实现（貌似是这个意思）
      // internal IsCallable function
      // 内部IsCallable函数（🙄什么鬼）
      // 如果当前this对象不是function，就抛出错误，因为只有function才需要实现bind这个方法。。。毕竟是返回函数
      throw new TypeError('Function.prototype.bind - what is trying to be bound is not callable');
    }
    // 声明变量aArgs保存arguments中除了第一个参数的其他参数的数组，因为第一个参数不是函数需要的参数，而是需要绑定的目标对象
    // 这块就用到了call的方法，因为arguments是类数组对象，没有slice这个方法，所以只能从Array那call过来一个使用
    var aArgs = Array.prototype.slice.call(arguments, 1);
    // 保存原先的this对象，是在调用bind的时候没有传入目标对象，那就使用原先的this对象
    var fToBind = this;
    // 声明空函数，在下面的原型中可以使用
    var fNOP = function() {};
    // 需要放回的拷贝函数的本体，从最后的return也知道，最后是返回的fBound这个方法
    var fBound  = function() {
        // this instanceof fBound === true时,说明返回的fBound被当做new的构造函数调用
        // 下面就涉及到刚才说的是bind时初始化参数，还是bind以后调用的时候再传入参数
        return fToBind.apply(
          // 判断原始this对象是不是fBound的实例，或者说this的原型链上有没有fBound
          this instanceof fBound
            // 如果有，就使用原始的this 
          ? this
            // 如果没有，就使用现在的传入的this对象
          : oThis,
          // 获取调用时(fBound)的传参.bind 返回的函数入参往往是这么传递的
          // 这一步就是为了保障在bind时候没有传入参数的时候，调用时候传入的参数能使用上
          aArgs.concat(Array.prototype.slice.call(arguments)));
      };

    // 维护原型关系
    // 判断原始this对象上有没有prototype
    if (this.prototype) {
      // Function.prototype doesn't have a prototype property
      // 如果原始this对象上有prototype 就把fNOP的prototype改成this.prototype，fNOP就继承自原始this了
      fNOP.prototype = this.prototype;
    }
    // 下行的代码使fBound.prototype是fNOP的实例,因此
    // 返回的fBound若作为new的构造函数,new生成的新对象作为this传入fBound,新对象的__proto__就是fNOP的实例
    // 既然fNOP是继承自原始this对象的，那这里的这一步就是让拷贝函数也拥有原始this对象的prototype，继承自同一个地方，师出同门
    fBound.prototype = new fNOP();
    // 最后返回被拷贝出来的函数
    return fBound;
  };
}
```




