# javascript-arith
楼梯算法问题(斐波那契数列）

description:一人只能走一层或者两层

target: 到达 N  层共有多少种路线


走到第 N 层，实际上是走到了（n-1)层+1层 或者 (n-2)层 + 2层  => f(n)=f(n-1)+f(n-2);
   
```javascript
    // var test  = [1]
    // var test  = [1,1]  [2]
    // var test  = [1,1,1] [1,2] [2,1]
    // var test  = [1,1,1,1] [1,2,1] [1,1,1] [2,2] [2,1,1]
    ...
```
```javascript
function stairs(stariNum) {
        if (!(stariNum > 0)) {
            throw new Error('请输入正整数')
        }
        if (stariNum === 1) {
            return 1;
        }
        if (stariNum === 2) {
            return 2;
        }
        return stairs(stariNum - 1) + stairs(stariNum - 2); //在不考虑递归优化情况下，超过1000时，firefox有内存泄露风险
    }

    stairs(40);
```
尾递归调用

```javascript
  function stairsOptimize(num, next = 1, total = 2) {
        if (num === 1) {
            return 1
        }
        if (num === 2) {
            return total
        }
        return stairsOptimize(num - 1, total, next + total)
    }

    stairsOptimize(40)
```
ps:尾调用优化
```text
即只保留内层函数的调用帧。如果所有函数都是尾调用，那么完全可以做到每次执行时，调用帧只有一项，这将大大节省内存。这就是“尾调用优化”的意义。
```
