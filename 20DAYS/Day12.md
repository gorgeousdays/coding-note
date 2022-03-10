# DAY12

## 70.爬楼梯

```java
class Solution {
    public int climbStairs(int n) {
        if(n<=2){
            return n;
        }
        //超时
        //return climbStairs(n-1)+climbStairs(n-2);
        int f1=1;
        int f2=2;
        for(int f=3;f<=n;f++){
            int temp=f1+f2;
            f1=f2;
            f2=temp;
        }
        return f2;
    }
}
```

## 198.打家劫舍

```java
class Solution {
    public int rob(int[] nums) {
        int n=nums.length;
        if(n==0){
            return 0;
        }
        if(n==1){
            return nums[0];
        }
        int[] robit=new int[n];

        robit[0]=nums[0];
        robit[1]=Math.max(nums[0],nums[1]);
        for(int i=2;i<n;i++){
            robit[i]=Math.max(robit[i-1],robit[i-2]+nums[i]);
        }
        return robit[n-1];
    }
}
```

## 120.三角形最小路径和

```java
class Solution {
    Integer[][] memo;
    public int minimumTotal(List<List<Integer>> triangle) {
        int n=triangle.size();
        int[][] dp = new int[n + 1][n + 1];

        for (int i = n - 1; i >= 0; i--) {
            for (int j = 0; j <= i; j++) {
                dp[i][j] = Math.min(dp[i + 1][j], dp[i + 1][j + 1]) + triangle.get(i).get(j);
            }
        }

        return dp[0][0];
        /* 递归+记忆化
        memo = new Integer[triangle.size()][triangle.size()];
        return dfs(triangle,0,0);
        */
    }
    //直接暴力dfs会超时，需要记忆化
    public int dfs(List<List<Integer>> triangle, int i, int j) {
        if (i == triangle.size()) {
            return 0;
        }
        //记忆化
        if (memo[i][j] != null) {
            return memo[i][j];
        }
        //
        return memo[i][j] = Math.min(dfs(triangle, i + 1, j), dfs(triangle, i + 1, j + 1)) + triangle.get(i).get(j);
    }
}
```

