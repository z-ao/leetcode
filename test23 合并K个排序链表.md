## 题目
合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。
 
**示例:**

```
输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6
```

## 解法
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode[]} lists
 * @return {ListNode}
 */
var mergeKLists = function(lists) {
    if(!lists.length || !lists[0]) null;
    
    if(lists.length === 1) return lists[0];
    
    const findMinNodeIndex = function(arr) {
        let minI;
        arr.forEach((item, index) => {
            if(!item) return;
            if(isNaN(minI)) {
                minI = index;
            }

            if(item.val < arr[minI].val) {
                minI = index;
            }
        });
        return minI;
    };

    const mergeNodeArr = function(node, target, arr) {
        const minIndex = findMinNodeIndex(arr);
        const minNode = arr[minIndex];
        if(minNode) {
            if(!node) {
                node = minNode;
                target = node;
            } else {
                target.next = minNode;
                target = target.next;
            }

            arr[minIndex] = arr[minIndex].next;
        } else {
            arr.splice(minNode, 1);
        }

        return !arr.length ? node : mergeNodeArr(node, target, arr);
    }

    return mergeNodeArr(null, null, lists);
};
//执行用时 : 1068 ms   内存消耗 : 42.6 MB
```