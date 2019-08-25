## 题目
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

**说明:**你不能倾斜容器，且 n 的值至少为 2。

<img src="https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg" />

示例:

```
输入: [1,8,6,2,5,4,8,3,7]
输出: 49
```

## 解法
```
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    if(height.length < 2) return 0;
    
    let max =  0;
    let startIndex = 0;
    let endIndex = height.length - 1;
    while(startIndex < endIndex) {
        const startVal = height[startIndex];
        const endVal = height[endIndex];
        const minH = Math.min(startVal, endVal);
        max = Math.max(max, minH * (endIndex - startIndex));

        if(startVal <= endVal) {
            startIndex++;
        } else {
            endIndex--;
        }
    }
    
    return max;
};
//执行用时 : 88 ms   内存消耗 : 35.5 MB
```