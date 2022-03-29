# Day29

## 91.解码方法

```java
class Solution {
    public int numDecodings(String s) {
        if(s.length()==0||s.charAt(0)=='0'){
            return 0;
        }
        int[] dp=new int[s.length()+1];
        dp[0]=1;

        for(int i=0;i<s.length();i++){
            dp[i+1]=s.charAt(i)=='0'?0:dp[i];
            if(i>0&&(s.charAt(i-1)=='1'|| (s.charAt(i-1)=='2'&& s.charAt(i)<='6'))){
                dp[i+1]+=dp[i-1];
            }
        }
        return dp[s.length()];
        
    }
}
```

## 139.单词拆分

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        int length=s.length();
        boolean[] dp=new boolean[length+1];
        dp[0]=true;
        for(int i=1;i<=length;i++){
            for(int j=0;j<i;j++){
                if(dp[j]&&wordDict.contains(s.substring(j,i))){
                    dp[i]=true;
                    break;
                }
            }
        }
        return dp[length];
    }
}
```

