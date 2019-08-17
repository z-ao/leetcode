## 题目
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。   

示例1:

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

示例2:

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

示例3:

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

## 解法
```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    var strArr = [];
    var maxLen = 0;
    for(i = 0; i < s.length; i++) {
        var value = s[i];
        if(strArr.includes(value)) { //如果重复
            maxLen = Math.max(strArr.length, maxLen); //替换长度
            
            var strIndex = strArr.indexOf(value);
            strArr.splice(0, strIndex + 1);
        }
        
        strArr.push(value);
    }
    
    maxLen = Math.max(strArr.length, maxLen);
    
    return maxLen;
};
//执行用时 : 108 ms   内存消耗 : 37.9 MB
```