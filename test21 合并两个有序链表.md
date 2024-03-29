## 题目
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

**示例：**    

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    let ret;
    
    if(l1 === null && l2 === null) {
        return null;
    }
    
    if(l1 === null) {
        return l2;
    }
    
    if(l2 === null) {
        return l1;
    }
    
    if(l1.val < l2.val) {
        ret = l1;
        l1 = l1.next;
    } else {
        ret = l2;
        l2 = l2.next;
    }

    let prev = ret;
    while(l1 !== null && l2 !== null) {
        if(l1.val < l2.val) {
            prev.next = l1;
            l1 = l1.next;
        } else {
            prev.next = l2;
            l2 = l2.next;
        }

        prev = prev.next;
    }
    
    prev.next = l1 === null ? l2 : l1;
    return ret;
};
//执行用时 : 88 ms   内存消耗 : 35.3 MB
```