# DAY1

## 二分查找

```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;
        while (low <= high) {
            int mid = (high + low) / 2;
            int num = nums[mid];
            if (num == target) {
                return mid;
            } else if (num > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return -1;
    }
}
```

## 第一个错误的版本



```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int low=1,high=n;
        while(low<high){
            //int mid=(low+high)/2;//这样会溢出
            //int mid=low+((high-1)>>1);
            int mid = low + (high - low) / 2; 
        
            if(isBadVersion(mid)){
                high=mid;
            }
            else{
                low=mid+1;
            }
        }
        return low;
    }
}
```

## 搜索插入位置

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int low=0,high=nums.length-1;
        while(low<=high){
            int mid=(high-low)/2+low;
            int num=nums[mid];
            if(num==target){
                return mid;
            }else if(num>target){
                high=mid-1;
            }else{
                low=mid+1;
            }
        }
        return low;
    }
}
```

