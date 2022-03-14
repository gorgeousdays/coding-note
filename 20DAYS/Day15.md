# DAY15

## 34.在排序数组中查找元素的第一个和最后一个位置

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int [] result=new int[2];
        result[0]=getLeft(nums,target);
        result[1]=getRight(nums,target);
        return result;
    }
    public int getRight(int[] nums,int target){
        if(nums.length==0){
            return -1;
        }
        int left=0;
        int right=nums.length-1;
        while(left<=right){
            int mid=left+(right-left)/2;
            if(nums[mid]==target && (mid+1>=nums.length||nums[mid+1]!=target)){
                return mid;
            }
            else if(nums[mid]<=target){
                left=mid+1;
            }
            else{
                right=mid-1;
            }
        }
        return -1;
    }
    public int getLeft(int[] nums,int target){
        if(nums.length==0){
            return -1;
        }
        int left=0;
        int right=nums.length-1;
        while(left<=right){
            int mid=left+(right-left)/2;
            if(nums[mid]==target&&(mid-1<0 || nums[mid-1]!=target)){
                return mid;
            }
            else if(nums[mid]>=target){
                right=mid-1;
            }
            else{
                left=mid+1;
            }
        }
        return -1;
    }
}
```

## 33.搜索选择排序数组

```java
class Solution {
    public int search(int[] nums, int target) {
        for(int i=0;i<nums.length;i++){
            if(nums[i]==target){
                return i;
            }
        }
        return -1;
    }
}
```

## 74.搜索二维矩阵

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row=matrix.length;
        int col=matrix[0].length;
        int left=0,right=row*col-1;
        
        while(left<=right){
            int mid=left+(right-left)/2;
            int i=mid/col;
            int j=mid%col;
            if(matrix[i][j]==target){
                return true;
            }
            else if(matrix[i][j]>target){
                right=mid-1;
            }
            else{
                left=mid+1;
            }
        }
        return false;
    }
}
```

