## 题目
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

**示例1：**    

```
输入: "()"
输出: true
```

**示例2：**    

```
输入: "()[]{}"
输出: true
```

**示例3：**    

```
输入: "(]"
输出: false
```

**示例4：**    

```
输入: "([)]"
输出: false
```

**示例5：**    

```
输入: "{[]}"
输出: true
```

## 解法
```
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let ret = true;
    
    const bracketStack = [];
    const bracketConf = {
        '(': ')',
        '{': '}',
        '[': ']'
    }
    const startBracketArr = ['(', '{', '['];
    
    for(str of s) {
        const isStartBrack = startBracketArr.includes(str);
        if(isStartBrack) {
            bracketStack.push(str);
        } else {
            const bracket = bracketStack.pop();
            const isCurrent = bracketConf[bracket] === str;
            if(!isCurrent) {
                ret = false;
                break;
            }
        }
    };
    
    if(bracketStack.length) {
        ret = false;
    }
    
    return ret;
};
//执行用时 : 80 ms   内存消耗 : 33.8 MB
```