## 题目
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/original_images/17_telephone_keypad.png" />

示例:

```
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

## 解法
```
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    if(!digits) return [];

    const ret = [];
    const config = {
        2: 'abc',
        3: 'def',
        4: 'ghi',
        5: 'jkl',
        6: 'mno',
        7: 'pqrs',
        8: 'tuv',
        9: 'wxyz'
    };
    
    const disitsArr = digits.split('').map(item => {
        return config[item];
    });
    
    const deep = function(num, arr, ret) {
        const itemStrArr = arr[0].split('');
        itemStrArr.forEach(s => {
            const retItem = num + s;
            
            const nextDeepArr = arr.slice(1);
            if(nextDeepArr.length) {
                deep(retItem, nextDeepArr, ret);
            } else {
                ret.push(retItem);
            }
        });
    }
    
    deep('', disitsArr, ret);
    
    return ret;
};
//执行用时 : 76 ms   内存消耗 : 33.9 MB
```