## 题目
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。 

示例1:

```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。
```

示例2:

```
输入: "cbbd"
输出: "bb"
```

## 解法
```
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
    const sArr = s.split('');

    let maxPalindromic = sArr.slice(0, 1);
    
    var isPalindromic = function(strArr) {
        let ret = true;
        const strArrLen = strArr.length;
        const middleIndex = Math.trunc(strArr.length / 2);
        
        var index =0;
        while( index < middleIndex) {
            const endIndex = strArrLen - index - 1;
            if(strArr[index] !== strArr[endIndex]) {
                ret = false; 
                break;
            }
            index++;
        }
        return ret;
    }

    for(var i =0; i < sArr.length; i++) {
        let lastIndex = sArr.length;
        if(lastIndex - i + 1 >= maxPalindromic.length) { // 当前有可能最大
            while(i < lastIndex){
                const validatorArr = sArr.slice(i, lastIndex+ 1);
                const isValid = isPalindromic(validatorArr);

                if(isValid) {
                    const isMax = maxPalindromic.length < (lastIndex - i + 1);
                    maxPalindromic = isMax ? validatorArr : maxPalindromic;
                    break;
                }

                lastIndex -= 1;
                
                //不可能最大
                if(maxPalindromic.length >= lastIndex - i + 1) {
                    break;
                }
            }
        }
    }
    return maxPalindromic.join('');
};
//执行用时 : 2588 ms   内存消耗 : 41.1 MB
```