# Day27

## 45.跳跃游戏||

```java
class Solution {
    public int jump(int[] nums) {
        int[] dp=new int[nums.length];
        int start=0;
        for(int i=1;i<nums.length;i++){
            while(i>start+nums[start]){
                start++;
            }
            dp[i]=dp[start]+1;
        }
        return dp[nums.length-1];
    }
}
```

## 62.不同路径

```java
class Solution {
    public int uniquePaths(int m, int n) {
        
        int[][] dp=new int[m][n];
        for(int i=0;i<m;i++){
            dp[i][0]=1;
        }
        for(int i=0;i<n;i++){
            dp[0][i]=1;
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j]=dp[i][j-1]+dp[i-1][j];
            }
        }
        return dp[m-1][n-1];
        
        //组合方法 m+n−2次，其中有m-1次向下移
        /*
        long res = 1;
        for (int x = n, y = 1; y < m; ++x, ++y) {
            res = res * x / y;
        }
        return (int)res;
        */
    }
}
```

