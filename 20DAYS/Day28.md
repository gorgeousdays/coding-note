# DAY28

## 5.最长回文子串

```java
class Solution {
    public String longestPalindrome(String s) {
        String res="";
        for(int i=0;i<s.length();i++){
            String s1=palindrome(s,i,i);
            String s2=palindrome(s,i,i+1);
            res=res.length()>s1.length()?res:s1;
            res=res.length()>s2.length()?res:s2;
        }
        return res;
    }
    private String palindrome(String s,int left,int right){
        while(left>=0&&right<s.length()){
            if(s.charAt(left)==s.charAt(right)){
                left--;
                right++;
            }
            else{
                break;
            }
        }
        return s.substring(left+1,right);
    }
}
```

## 413.等差数列划分

```java
class Solution {
    public int numberOfArithmeticSlices(int[] nums) {
        int n=nums.length,res=0;
        int[] dp=new int[n];
        for(int i=2;i<n;i++){
            if(nums[i]-nums[i-1]==nums[i-1]-nums[i-2]){
                dp[i]=dp[i-1]+1;
            }else{
                dp[i]=0;
            }
            res+=dp[i];
        }
        return res;
    }
}
```

