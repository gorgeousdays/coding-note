# DAY32

## 72.编辑距离

```java
class Solution {
    public int minDistance(String word1, String word2) {
        int length1=word1.length(),length2=word2.length();
        int [][]dp=new int[length1+1][length2+1];
        for(int i=0;i<=length1;i++){
            dp[i][0]=i;
        }
        for(int j=0;j<=length2;j++){
            dp[0][j]=j;
        }
        for(int i=1;i<=length1;i++){
            for(int j=1;j<=length2;j++){
                if(word1.charAt(i-1)==word2.charAt(j-1)){
                    dp[i][j]=dp[i-1][j-1];
                }
                else{
                    dp[i][j]=Math.min(dp[i-1][j-1],dp[i-1][j]);
                    dp[i][j]=Math.min(dp[i][j],dp[i][j-1])+1;
                }
            }
        }
        return dp[length1][length2];
    }
}
```

## 322. 零钱兑换

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp=new int[amount+1];
        Arrays.fill(dp,1,dp.length,Integer.MAX_VALUE);

        for(int i=0;i<coins.length;i++){
            for(int j=coins[i];j<=amount;j++){
                if(dp[j-coins[i]]!=Integer.MAX_VALUE){
                    dp[j]=Math.min(dp[j],dp[j-coins[i]]+1);
                }
            }
        }
        return dp[amount]==Integer.MAX_VALUE?-1:dp[amount];
    }
}
```

## 343. 整数拆分

```java
class Solution {
    public int integerBreak(int n) {
        int[] dp=new int[n+1];

        for(int i=2;i<=n;i++){
            for(int j=1;j<i;j++){
                dp[i]=Math.max(dp[i],Math.max(dp[i-j]*j,j*(i-j)));

            }
        }
        return dp[n];
    }
}
```

