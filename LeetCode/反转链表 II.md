## 反转链表 II

日期：2021-3-18 

### 题目

给你单链表的头指针 `head` 和两个整数 `left` 和` right` ，其中` left <= right` 。请你反转从位置 `left` 到位置 `right` 的链表节点，返回 反转后的链表 。 

```
输入：head = [1,2,3,4,5], left = 2, right = 4
输出：[1,4,3,2,5]
```

```
输入：head = [5], left = 1, right = 1
输出：[5]
```

### 思路

为了实现对链表的翻转，可以设定哨兵（适用于所有链表操作）于链表头部，最后返回即可。

主要步骤为找`left` 然后往后`right-left`次逐一翻转，最后将`left`前与`right`后的点进行处理即可。

### 算法

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int l, int r) {
        //采用哨兵的思想，即对头节点进行标记，最后返回dummyHead->next即可
        ListNode* dummyHead = new ListNode(0);
        dummyHead->next = head;

        r -= l;//计算left和right之间的距离

        ListNode* hh = dummyHead;
        //找到left点
        while(l> 1){
            hh = hh->next;
            l--;
        }

        ListNode* prv = hh->next;
        ListNode* cur = prv->next;
        //翻转链表left至right
        while (r> 0) {
            ListNode* nxt = cur->next;
            cur->next = prv;
            prv = cur;
            cur = nxt;
            r--;
        }
        hh->next->next = cur;//hh->next即为left节点，令其指向right原来的下一个点
        hh->next = prv;//hh指向right
        return dummyHead->next;
    }
};
```

