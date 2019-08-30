## 题目
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。


```
例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).
```

## 解法
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
    const sortNums = nums.sort((a, b) => (a-b));

    let ret;

    for(let i = 1; i < sortNums.length - 1; i++) {
        let sIndex = 0;
        let eIndex = sortNums.length - 1;
        
        while(sIndex < eIndex && ret !== target) {
            const sum = sortNums[sIndex] + sortNums[i] + sortNums[eIndex];
            ret = Math.abs(ret - target) < Math.abs(sum - target) ? ret : sum;

            if(sum <= target) {
                sIndex = sIndex + 1 === i ? sIndex + 2 : sIndex + 1;
            } else {
                eIndex = eIndex - 1 === i ? eIndex - 2 : eIndex - 1;
            }
        };
    }
    
    return ret;
};
//执行用时 : 104 ms   内存消耗 : 34.9 MB
```