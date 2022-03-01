# DAY3

## 283.移动零

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int j=0;
        for(int i=0;i<=nums.length-1;i++){
            if(nums[i]!=0){
                nums[j++]=nums[i];
            }
        }
        while(j<nums.length){
            nums[j++]=0;
        }

        /* 另开一块空间
        int[] ans=new int[nums.length];
        int j=0;
        for(int i=0;i<=nums.length-1;i++){
            if(nums[i]!=0){
                ans[j]=nums[i];
                j++;
            }
        }
        for(int i=j;i<=nums.length-1;i++){
            ans[i]=0;
        }
        System.arraycopy(ans, 0, nums, 0, nums.length);
        */
    }
}
```

## 167.两数之和 II - 输入有序数组

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left=0,right=numbers.length-1;
        while(left<right){
            int sum=numbers[left]+numbers[right];
            if(sum==target){
                return new int[]{left+1,right+1};
            }
            else if(sum<=target){
                left++;
            }
            else{
                right--;
            }
        }
        return null;
    }
}
```

