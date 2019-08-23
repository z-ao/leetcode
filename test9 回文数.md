## 题目
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。



**说明:**   
假设我们的环境只能存储 32 位大小的有符号整数，那么其数值范围为 [−231,  231 − 1]。如果数值超过这个范围，qing返回  INT_MAX (231 − 1) 或 INT_MIN (−231) 。


示例 1:

```
输入: 121
输出: true
```

示例 2:

```
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
```

示例 3:

```
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```


## 解法
```
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if(x < 0) return false;
    if(x < 10) return true;
    
    let ret = true;
    x = x.toString();
    while(x.length > 1) {
        if(x.slice(0, 1) !== x.slice(-1)) {
            ret = false;
            break;
        }
        
        x = x.slice(1, -1)
    }
    
    return ret;
};
//执行用时 : 320 ms   内存消耗 : 45.5 MB
```