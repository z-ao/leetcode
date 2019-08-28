## 题目
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

示例 1:

```
输入: ["flower","flow","flight"]
输出: "fl"
```

示例 2:

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```

**说明:**

所有输入只包含小写字母 a-z 。

## 解法
```
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    let ret = '';
    
    if(strs.length === 0) return ret;
    
    let shortStr = strs.reduce((ret, item) => {
        if(ret.length > item) {
            ret = item;
        }
        return ret;
    });
    

    for(let i = 0; i < shortStr.length; i++) {
        const val = shortStr.charAt(i);
        const allHas = strs.every(item => {
            return item.charAt(i) === val;
        });
        
        if(allHas) {
            ret += val;
        } else {
            break;
        }
    }
    
    return ret;
};
//执行用时 : 84 ms   内存消耗 : 34.5 MB
```