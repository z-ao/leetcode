## 题目
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。

请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

你可以假设 nums1 和 nums2 不会同时为空。  

示例1:

```
nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
```

示例2:

```
nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5
```

## 解法
```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    let ret;

    const longNum = nums1.length > nums2.length ? nums1 : nums2; //长数组
    const shortNum = nums1.length <= nums2.length ? nums1 : nums2; //短数组
    const retNum = [].concat(shortNum); //目标数组默认值为短数组

    let shortMinIndex = 0; //插入目标数组最小索引
    longNum.forEach((item, index) => { //遍历长数组
        while(item > shortNum[shortMinIndex]){
            shortMinIndex++;
        }

        retNum.splice(index + shortMinIndex, 0, item);
    });
    
    if(retNum.length % 2 === 0) {
        ret = (retNum[retNum.length/ 2 - 1] + retNum[retNum.length/ 2]) / 2;
    } else {
        ret = retNum[Math.floor(retNum.length/ 2)];
    };
    
    return ret;
};
//执行用时 : 164 ms   内存消耗 : 39.4 MB
```