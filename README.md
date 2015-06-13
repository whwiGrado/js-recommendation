# js-recommendation
编写高质量代码（改善JavaScript程序的188个建议）读书笔记
## 读后期望
* 能写出简单、清晰、高效的代码
* 能架构一个稳定、健壮、快捷的应用框架
* 能回答一个困扰很多人的技术问题
* 能修复一个应用开发中遇到的大的Bug
* 能非常熟悉某个开源产品
* 能提升客户端应用性能

***

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

***

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
    | 空对象 | toString() | NaN | true | 不转换 |
    | 非空对象 | toString() | 转数字/NaN | true | 不转换 |
    | 空数组 | toString() | 0 | true | 不转换 |
    | 非空数组 | toString() | 转数字(只有一个数字元素)/NaN | true | 不转换 |

*

```

```
*

```
```
*

```
```
*

```
```
*

```
```
*

```
```
*

```
```
*

```
```
*

```
```
*

```
```

