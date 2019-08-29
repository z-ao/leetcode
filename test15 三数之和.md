## 题目
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

**注意**：答案中不可以包含重复的三元组

示例 1:

```
例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

示例 2:

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```

## 解法
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    if(new Set(nums).size === 1 && nums[2] === 0) { //hack
        return [[0, 0, 0]];
    }
    
    let ret = new Set();

    const sortNums = nums.sort((a, b) => (a - b));

    for(let i = 1; i < sortNums.length - 1; i++) {
        const val = sortNums[i];
        let s = 0,
            e = sortNums.length - 1;

        while(s < e) {
            const sVal = sortNums[s];
            const eVal = sortNums[e];
            
            const sum = sVal + val + eVal;
            switch(true) {
                case sum > 0:
                    e = (e - 1) === i ? e - 2: e - 1;
                    break;
                case sum < 0:
                    s = (s + 1) === i ? s + 2: s + 1;
                    break;
                case sum === 0:
                    const item = [sVal, val, eVal].sort((a, b) => (a - b));

                    ret.add(item.toString())
                    s = (s + 1) === i ? s + 2: s + 1;
                    break;
                default:
                    break;
            }
        }
    }
    ret = [...ret].map(item => item.split(',').map(num => Number(num)));
    return ret;
};
//执行用时 : 700 ms   内存消耗 : 52.9 MB
```