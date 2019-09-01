## 题目
给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。

**注意：**   
答案中不可以包含重复的四元组。



示例:

```
给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。

满足要求的四元组集合为：
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

## 解法
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[][]}
 */
var fourSum = function(nums, target) {
    if(nums.length < 4) return [];
    
    const sortNums = nums.sort((a, b) => (a - b));
    const numsLen = nums.length;
    
    const ret = [];
    for(let i = 0; i < numsLen - 3; i++) {
        if(sortNums[i] === sortNums[i-1]) continue;
        
        if(sortNums[i] + sortNums[i+1] + sortNums[i+2] + sortNums[i+3] > target) break;
        
        if(sortNums[i] + sortNums[numsLen-1] + sortNums[numsLen-2] + sortNums[numsLen-3] < target) continue;
        
        for(let k = i + 1; k < numsLen - 2; k++) {
            if(k > (i + 1) && sortNums[k] === sortNums[k-1]) continue;
            if(sortNums[i] + sortNums[k] + sortNums[k+1] + sortNums[k+2] > target) break;
            if(sortNums[i] + sortNums[k] + sortNums[numsLen-2] + sortNums[numsLen-1] < target) continue;

            let start = k+1;
            let end = numsLen - 1;
            while(start < end) {
                const sum = sortNums[i] + sortNums[k] + sortNums[start] + sortNums[end];
                if(sum === target) {
                    ret.push([sortNums[i], sortNums[k], sortNums[start], sortNums[end]]);
                    while(sortNums[start] === sortNums[start + 1] && start < end) {
                        start++;
                    }
                    while(sortNums[end] === sortNums[end - 1] && start < end) {
                        end--;
                    }
                    start++;
                } else if(sum > target) {
                    end--;
                } else { //sum < target
                    start++;
                }
            }
        }
    }
    
    return ret;
};
//执行用时 : 124 ms   内存消耗 : 36.8 MB
```