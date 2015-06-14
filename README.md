# js-recommendation
编写高质量代码（改善JavaScript程序的188个建议）读书笔记
## 读后期望
* 能写出简单、清晰、高效的代码
* 能架构一个稳定、健壮、快捷的应用框架
* 能回答一个困扰很多人的技术问题
* 能修复一个应用开发中遇到的大的Bug
* 能非常熟悉某个开源产品
* 能提升客户端应用性能


## 目录
1. JavaScript 语言基础（33个建议）
2.
3.
4.
5.
6.
7.
8.
9.


### 第一章
* 减少全局变量污染

```
    把全局变量追加到一个命名空间下 e.g.
        var my = {};
        my.name = {
            "first-name" : "Hongwei",
            "last-name" : "Wang"
        };
        my.work = {
            "Education" : "Bupt",
            "Companies" : "Youdao",
            "Post" : "FE"
        };
        window.my = my;
```

* 防止浮点数溢出

```
    Bug:
        a = 0.1 + 0.2; // 0.30000000000000004
    浮点数中的整数运算是精确的，所以浮点数溢出可以通过指定精度来避免 e.g.
        a = (1+2)/10; //0.3
```

* JavaScript 类型自动转换

    | 作用目标 | 字符串操作环境 | 数字运算环境 | 逻辑运算环境 | 对象操作环境 |
    | ------- | ----------- | ---------- | ---------- | ---------- |
    | undefined | "undefined"  | NaN | false | Error |
    | null | "null"  | 0 | false | Error |
    | "" | 不转换 | 0 | false | String |
    | 0 | "0"  | 不转换 | false | Number |
    | true | "true"  | 1 | 不转换 | Boolean |
    | false | "false"  | 0 | 不转换 | Boolean |
    | 空对象 | 对象的toString() | NaN | true | 不转换 |
    | 非空对象 | 对象的toString() | 转数字/NaN | true | 不转换 |
    | 空数组 | 数组的toString() | 0 | true | 不转换 |
    | 非空数组 | 数组的toString() | 转数字(只有一个数字元素)/NaN | true | 不转换 |

    ![alt text](/images/toString.png)

* 数据类型的检测

```
    function typeOf(o) {
        var _toString = Object.prototype.toString;
        var _type = {
            "undefined" : "undefined",
            "number" : "number",
            "boolean" : "boolean",
            "string" : "string",
            "[object Function]" : "function",
            "[object Array]" : "array",
            "[object Date]" : "date",
            "[object RegExp]" : "regexp",
            "[object Error]" : "error"
        }
        return _type[typeof o] || _type[_toString.call(o)] || (o ? "object" : "null");
    }

```

* 避免误用 parseInt

```
    parseInt(string, radix); 建议指定第二个参数
    not recommended:
        parseInt("010"); // 8(默认八进制)
        parseInt("0x10"); // 16(默认十六进制)
    recommended:
        parseInt("010", 10); //10
        parseInt("0x10", 10); //0(从字符串的第0个位置开始检查是否是数字，检测到非数字，则输出前面的数字)
```

* 防止 JavaScript 自动插入分号

```
    分行书写的代码应该确保单行不形成独立的合法的逻辑语义
    error:
        var i = a ? 1 : b
                  ? 2 : c
                  ? 3 : 4;
    correct:
        var i = a ? 1
              : b ? 2
              : c ? 3
              : 4;
```

* 区分 number 与 NaN 、+Infinity/-Infinity

```
    Bug:
        typeof 不能区分普通数字与 NaN、+Infinity/-Infinity
    fix:
        function isNumber(value) {
            if(typeof value === "number"){
                return isNaN(value) ? "NaN"
                  : isFinite(value) ? "number"
                  : "+Infinity/-Infinity";
            }else{
                return "NaN";
            }
        }

```

* undefined

```
    undefined 会出现的3种情况
        1. 从一个对象及其原型链中查找某个属性未找到时返回 undefined
        2. 将没有显式的通过 return 语句返回值的函数赋值给某个变量(构造函数用 new 实例化时除外)时，返回 undefined
        3. 函数声明的形参个数 > 调用时传入的参数个数，多余的形参将被设置为 undefined
    对于浏览器不支持 undefined 关键字时，需要自定义 undefined，方式有:
        1. var undefined = void null;
        2. var undefined = void 1;
        3. var undefined = function(){};
```

* 使用假值

```
    下面的6个值的布尔值都是 false
    0             // Number
    NaN           // Number
    ""            // String
    null          // Object
    undefined     // Undefined
    false         // false
```

* == 与 ===

```
    建议使用 === 和 !== ，而尽量避免使用 ==
    === 的算法规则，e.g.: 判断 x === y
        x 与 y 的数据类型不同 ? false
        : x 的数据类型为 Null 或 Undefined ? true
        : x 的数据类型为 Number ?
            if( x 是 NaN || y 是 NaN ) : false
            else if( x、y 其中一个是+0，另个一个是-0 ) : true
            else if( x、y 的数值相等) : true
            else : false
        : x 的数据类型是 String ?
            if( x、y 的字符序列完全相等 ) : true
            else : false
        : x 的数据类型是 Boolean ?
            if( x、y 同 ture 或同 false ) : true
            else : false
        : x 的数据类型是 Object ?
            if( x、y 引用相同的对象 ) : true
            else : false

```

*

```
```
