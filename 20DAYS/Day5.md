# DAY5

## 876.链表的中间节点

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow=head,fast=head;
        while(fast!=null &&fast.next!=null){
            fast=fast.next.next;
            slow=slow.next;
        }
        return slow;
    }
}
```

## 19.删除链表的倒数第N个结点

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        //快慢指针
        ListNode fast=head,slow=head;
        while(n!=-0){
            n--;
            fast=fast.next;
        }
        if(fast==null){
            return head.next;
        }
        fast=fast.next;
        while(fast!=null){
            fast=fast.next;
            slow=slow.next;
        }
        slow.next=slow.next.next;
        return head;
        
        /* 扫两次 
        ListNode t=head;
        int length=1;
        while(t.next!=null){
            length+=1;
            t=t.next;
        }
        t=head;
        int delete_index=length-n;
        if(delete_index==0){
            head=head.next;
            return head;
        }
        while(delete_index-1>0){
            t=t.next;
            delete_index-=1;
        }
        t.next=t.next.next;
        return head;
        */
    }
}
```

