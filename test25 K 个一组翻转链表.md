## 题目
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。

**示例:**

给定这个链表：```1->2->3->4->5```

当 k = 2 时，应当返回: ```2->1->4->3->5```

当 k = 3 时，应当返回: ```3->2->1->4->5```

**说明 :**

+ 你的算法只能使用常数的额外空间。
+ **你不能只是单纯的改变节点内部的值**，而是需要实际的进行节点交换。

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
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */

var reverseKGroup = function(head, k) {
    if(head === null || head.next === null || k === 0) return head;
    
    const ret = new ListNode();
    ret.next = head;
    
    const getNodeLen = function(nodelist) {
        let len = 1;
        while(nodelist.next) {
            len++;
            nodelist = nodelist.next;
        }
        return len
    };
    const len = getNodeLen(head); //节点长度
    let count = Math.floor(len / k); //转化次数

    let cur = ret
    let pre = ret;
    let cacheNode;

    while(count--) {
        let end = k;
        while(end--) { 
            cacheNode = cur.next;
            cur.next = cur.next.next;
            cacheNode.next = pre.next;
            pre.next = cacheNode;
            
            if (end === k - 1){
                cur = cur.next;
            }
        }
        pre = cur;
    }

    return ret.next;
};
//执行用时 : 120 ms   内存消耗 : 37.6 MB
```