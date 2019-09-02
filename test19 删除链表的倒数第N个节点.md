## 题目
给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

**示例：**    

```
给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
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
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    let storeArr = [];
    
    let node = head;
    while(node !== null) {
        storeArr.push(node);
        node = node.next;
    }
    
    if(storeArr.length === 1) {
        return null;
    }
    if(storeArr.length === n) {
        return head.next
    }

    const deleteParent = storeArr.slice(storeArr.length - n - 1, storeArr.length - n)[0];
    const deleteChild = storeArr.slice(storeArr.length - n + 1, storeArr.length - n + 2)[0];
    deleteParent.next = deleteChild;

    storeArr = null;
    return head;
};
//执行用时 : 88 ms   内存消耗 : 33.9 MB
```