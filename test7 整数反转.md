## 题目
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

示例 1:

```
输入: 123
输出: 321
```

示例 2:

```
输入: -123
输出: -321
```

示例 3:

```
输入: 120
输出: 21
```

注意:

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

## 解法
```
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    const min = Math.pow(-2, 31);
    const max = Math.pow(2, 31) - 1;
    
    let ret = 0;
    while(x !== 0) {
        const pop = x % 10;
        x = Math.trunc(x / 10);
        
        const temp = ret * 10 + pop;
        if(temp < min || temp > max) {
            ret = 0;
            break;
        }
        ret = temp;
    }
    return ret;
};
//执行用时 : 104 ms   内存消耗 : 35.5 MB
```