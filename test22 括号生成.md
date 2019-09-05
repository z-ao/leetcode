## 题目
给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。

例如，给出 n = 3，生成结果为：
 

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

## 解法
```
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    const ret = [];
    
    const bukets = function(arr, str, start, end, num) {
        if(str.length === num * 2) {
            arr.push(str);
            return;
        }
        
        if(start < num) {
            bukets(arr, str+'(', start+1, end, num);
        } 

        if(end < start) {
            bukets(arr, str+')', start, end+1, num);
        }
    }
    
    bukets(ret, '', 0, 0, n);
    
    return ret
};
//执行用时 : 80 ms   内存消耗 : 35.3 MB
```