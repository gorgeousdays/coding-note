# DAY26

## 213.打家劫舍||

```java
class Solution {
    public int rob(int[] nums) {
        if(nums.length==1){
            return nums[0];
        }
        if(nums.length==2){
            return Math.max(nums[0],nums[1]);
        }

        return Math.max(robit(Arrays.copyOfRange(nums,0,nums.length-1)),robit(Arrays.copyOfRange(nums,1,nums.length)));
    }

    private int robit(int [] nums){
        int n=nums.length;
        int []dp=new int[n+1];
        dp[0]=nums[0];
        dp[1]=Math.max(nums[0],nums[1]);
        for(int i=2;i<n;i++){
            dp[i]=Math.max(dp[i-1],dp[i-2]+nums[i]);
        }
        return dp[n-1];
    }
}
```

## 55.跳跃游戏

```java
class Solution {
    public boolean canJump(int[] nums) {
        int len=nums.length-1;
        int maxDis=nums[0]; 
        for(int i=1;i<len;i++){
            if(i<=maxDis){
                maxDis=Math.max(maxDis,nums[i]+i);
            }
        }

        return maxDis>=len;
    }
}
```

