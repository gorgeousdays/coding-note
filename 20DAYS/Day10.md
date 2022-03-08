# DAY10

## 21.合并两个有序链表

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        /*递归
       if(list1==null){
           return list2;
       }
       if(list2==null){
           return list1;
       }
       if(list1.val<list2.val){
           list1.next=mergeTwoLists(list1.next,list2);
           return list1;
       }else{
           list2.next=mergeTwoLists(list1,list2.next);
           return list2;
       }*/
       ListNode head=new ListNode(0);
       ListNode l=head;
       while(list1!=null && list2!=null){
           if(list1.val<list2.val){
               l.next=list1;
               l=l.next;
               list1=list1.next;
           }
           else{
               l.next=list2;
               l=l.next;
               list2=list2.next;
           }
       }
       if(list1==null){
           l.next=list2;
       }else{
           l.next=list1;
       }
       return head.next;
    }
}
```

## 206.反转链表

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
    public ListNode reverseList(ListNode head) {
        
        ListNode l;
        if(head!=null && head.next!=null){
            l=reverseList(head.next);
        }
        else{
            return head;
        }
        ListNode lhead=l;
        while(l.next!=null){
            l=l.next;
        }
        l.next=new ListNode(head.val);
        return lhead;
        /*
        ListNode pre=null;
        ListNode cur=head;
        while(cur!=null){
            ListNode next=cur.next;
            cur.next=pre;
            pre=cur;
            cur=next;
        }
        return pre;
        */
    }
}
```

