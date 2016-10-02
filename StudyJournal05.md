今天在廖雪峰的 js 教程中学习了标准对象，箭头函数等概念，箭头函数完全修复了this的指向，this总是指向词法作用域，也就是外层调用者obj。
学习了 json 表达方式。
在 jsmagic 教程中完成了『实现 Lodash 的工具函数』一章，完成了所有练习题。
现将我做的答案记录如下：
### Exercise: 独立记数器

```
function makeCounter(init) {
    var counter = init;
     function increment () {
        counter = counter + 1;
         return counter;
    }

    function decrement() {
        counter = counter - 1;
        return counter;
    }

    function value() {
        return counter;
    }

    return [increment, decrement];
}
```

### 练习：实现 _.once
```
once : function (func){
        var count=0;
        var result=undefined;
        return function () {
            if(count==0){
                result = func();
                count=count+1;
            }
            return result;
    }
```
### 练习：缓存结果

```
memoize:function (func,cache_key){
    var mem = {};
    var cache = {};
    return function(arg,key){
        if(cache_key===undefined){
            if(mem.hasOwnProperty(arg)){
                return mem[arg];
            }
            else{
                var res = func(arg);
                if(cache_key===undefined){
                    mem[arg]=res;
                }else{
                    mem[cache_key(arg)]=res;
                }

                return res;
            }
        }
        else{
            if(mem.hasOwnProperty(cache_key(arg))){
                return mem[cache_key(arg)];
            }
            else{
                var res = func(arg);
                mem[cache_key(arg)]=res;
                return res;
            }
        }





    }
}
```
以上代码都顺利地通过了测试。
