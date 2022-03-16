# DAY17

## 82.删除排序链表中的重复元素II

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
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null||head.next==null){
            return head;
        }
        ListNode next=head.next;
        if(head.val==next.val){
            while(next!=null && head.val==next.val){
                next=next.next;
            }
            head=deleteDuplicates(next);
        }
        else{
            head.next=deleteDuplicates(next);
        }
        return head;
    }
}
```

## 15.三数之和

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ans=new ArrayList<List<Integer>>();
        for(int left=0;left<nums.length-2;left++){
            if(nums[left]>0){
                break;
            }
            if(left>0 &&nums[left]==nums[left-1]){
                continue;
            }
            int mid=left+1,right=nums.length-1;
            while(mid<right){
                int sum=nums[left]+nums[mid]+nums[right];
                if(sum<0){
                    while(mid<right &&nums[mid]==nums[++mid]);
                    /*这样会超时
                    while(mid<right && nums[mid]==nums[mid+1]){
                        mid++;
                    }
                    */
                }else if(sum>0){
                    while(mid<right &&nums[right]==nums[--right]);
                    /*
                    while(mid<right && nums[right]==nums[right-1]){
                        right--;
                    }
                    */
                }else{
                    ans.add(new ArrayList<Integer>(Arrays.asList(nums[left],nums[mid],nums[right])));
                    /*
                    while(mid<right){
                        if(nums[mid]==nums[mid+1]){
                            mid++;
                            continue;
                        }
                        if(nums[right]==nums[right-1]){
                            right--;
                            continue;
                        }
                        break;
                    }
                    */
                    while(mid<right &&nums[mid]==nums[++mid]);
                    while(mid<right &&nums[right]==nums[--right]);
                }
            }
        }
        return ans;
    }
}
```

