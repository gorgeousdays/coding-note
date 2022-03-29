# Day30

## 300. 最长递增子序列

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] dp=new int[nums.length];
        Arrays.fill(dp,1);
        for(int i=1;i<nums.length;i++){
            for(int j=0;j<i;j++){
                if(nums[i]>nums[j]){
                    dp[i]=Math.max(dp[i],dp[j]+1);
                }
            }
        }
        int res=0;
        for(int i=0;i<dp.length;i++){
            res=Math.max(res,dp[i]);
        }
        return res;
    }
}
```

## 673. 最长递增子序列的个数

```java
class Solution {
    public int findNumberOfLIS(int[] nums) {
        if(nums.length<=1){
            return nums.length;
        }
        int[] dp=new int[nums.length];
        int[] count=new int[nums.length];
        Arrays.fill(dp,1);
        Arrays.fill(count,1);

        int maxlength=0;

        for(int i=1;i<nums.length;i++){
            for(int j=0;j<i;j++){
                if(nums[i]>nums[j]){
                    if(dp[j]+1>dp[i]){
                        dp[i]=dp[j]+1;
                        count[i]=count[j];
                    }
                    else if(dp[j]+1==dp[i]){
                        count[i]+=count[j];
                    }
                }
                if(dp[i]>maxlength) maxlength=dp[i];
            }
        }
        int res=0;
        for(int i=0;i<dp.length;i++){
            if(maxlength==dp[i]){
                res+=count[i];
            }
        }
        return res;
    }
}
```

