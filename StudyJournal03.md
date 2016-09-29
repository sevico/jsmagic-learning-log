今天主要学习了廖雪峰老师的高阶函数一章，觉得学到了不少JavaScript 中
的坑和技巧。比如用1*'12'可以将字符串转换成数字。sort的默认行为是将数组中
所有元素都转换成字符串再进行字典序大小排序。以及关于 map 这个经典的练习题：
'use strict';

var arr = ['1', '2', '3'];
var r;
r = arr.map(parseInt);
alert('[' + r[0] + ', ' + r[1] + ', ' + r[2] + ']');
结果竟然是[1, NaN, NaN]，小明百思不得其解，请帮他找到原因并修正代码。

由于map()接收的回调函数可以有3个参数：callback(currentValue, index, array)，通常我们仅需要第一个参数，而忽略了传入的后面两个参数。不幸的是，parseInt(string, radix)没有忽略第二个参数，导致实际执行的函数分别是：

parseInt('0', 0); // 0, 按十进制转换

parseInt('1', 1); // NaN, 没有一进制

parseInt('2', 2); // NaN, 按二进制转换不允许出现2

可以改为r = arr.map(Number);，因为Number(value)函数仅接收一个参数。



思客教程中学到了『创建 NPM 包』中的『将项目转化成 ES6』之前的位置，
用minimist实现了 drunk 功能。在其中遇到了 NODE_PATH环境变量的设置
问题。目前的练习代码已放在 github：https://github.com/sevico/greet
#问题
1.在提交代码时，忽然想问自己在 git push 命令里加不加-u 参数的区别，
查到官方手册，说是和 upstream 有关，但具体会怎么影响？我似乎不是太清楚。
2.对在模块化JavaScript 中的通配符导入那个练习不是很懂。

明天开始继续学习『创建 NPM 包』中的其他内容。