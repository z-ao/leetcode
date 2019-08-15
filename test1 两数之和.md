## 题目
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。   
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。   

示例:
```
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

## 解法
```
// 解法1 暴力循环
var twoSum = function(nums, target) {
    var ret = [];
    for(var i = 0; i < nums.length - 1; i++) {
        for(var k = i + 1; k < nums.length; k++) {
            if(nums[i] + nums[k] === target){
                ret.push(i, k);
            }
        }
    }
    return ret
};
// 执行用时 : 200 ms   内存消耗 : 34.6 MB

//解法2 哈希表
var twoSum = function(nums, target) {
    var ret = [];
    for(var i = 0; i < nums.length; i++) {
        const mixValue = target - nums[i];
        const mixIndex = nums.indexOf(mixValue, i + 1);
        if(mixIndex !== -1) {
            ret.push(i, mixIndex)
        }
    }
    return ret
};
//执行用时 : 184 ms   内存消耗 : 34.8 MB
```