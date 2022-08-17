## leetcode 23 合并多个升序链表

题目链接：https://leetcode.cn/problems/merge-k-sorted-lists/



### 题目内容
给你一个链表数组，每个链表都已经按升序排列。

请你将所有链表合并到一个升序链表中，返回合并后的链表


```
解题思路
 1. 采用分治思想，每次都处理两个列表成一个列表
 2. 然后再将两个列表进行再一次合并就可以找到最终解答
```

### 核心代码
```
    //合并两个链表，谁小就谁在前面，然后指针往下一节点移动
    private ListNode mergeTwoList(ListNode node1, ListNode node2) {
        if (node1 == null) return node2;
        if (node2 == null) return node1;
        if (node1.val >= node2.val) {
            node2 = mergeTwoList(node1, node2.next);
            return node2;
        }
        node1 = mergeTwoList(node1.next, node2);
        return node1;
    }
    
    //分治思想，将数组分成2个列表2个列表一块处理
    public ListNode merge(ListNode[] lists, int left, int right) {
        if (left == right) return lists[left];
        int middle = left + (right - left) / 2;
        ListNode l1 = merge(lists, left, middle);
        ListNode l2 = merge(lists, middle+1, right);
        return mergeTwoList(l1, l2);
    }
    
```




