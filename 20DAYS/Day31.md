# Day31

## 1143. 最长公共子序列

```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int length1=text1.length(),length2=text2.length();
        int [][]dp=new int[length1+1][length2+1];
        for(int i=1;i<=length1;i++){
            for(int j=1;j<=length2;j++){
                if(text1.charAt(i-1)==text2.charAt(j-1)){
                    dp[i][j]=dp[i-1][j-1]+1;
                }
                dp[i][j]=Math.max(dp[i-1][j],dp[i][j]);
                dp[i][j]=Math.max(dp[i][j-1],dp[i][j]);
            }
        }
        return dp[length1][length2];
    }
}
```

## 583. 两个字符串的删除操作

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
                    dp[i][j]=Math.min(dp[i-1][j-1]+2,dp[i-1][j]+1);
                    dp[i][j]=Math.min(dp[i][j],dp[i][j-1]+1);
                }
            }
        }
        return dp[length1][length2];
    }
}
```

