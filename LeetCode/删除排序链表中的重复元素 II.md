## 删除排序链表中的重复元素 II

日期：2021-3-25

### 题目

存在一个按升序排列的链表，给你这个链表的头节点 head ，请你删除链表中所有存在数字重复情况的节点，只保留原始链表中 没有重复出现 的数字。

返回同样按升序排列的结果链表。

```
输入：head = [1,2,3,3,4,4,5]
输出：[1,2,5]

输入：head = [1,1,1,2,3]
输出：[2,3]
```

### 思路

递归删除或者采用两个指针pre和cur，存储前后的值，如果一样就删掉cur然后往后指向，这样就只要遍历一次就好了。但要考虑只剩一个节点或者不剩节点的情况。

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
    ListNode* deleteDuplicates(ListNode* head) {
        if(head==nullptr||head->next==nullptr){
            return head;
        }
        ListNode* next=head->next;
        if(head->val==next->val){
            while(next!=nullptr&&head->val==next->val){
                 next=next->next;
            }
            head=deleteDuplicates(next);    
        }
        else{
            head->next=deleteDuplicates(next);
        }
        return head;
    }
};
```

