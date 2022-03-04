# DAY6

## 3.无重复字符的最长子串

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        //评论区的滑动窗口解法,记录上一次字符出现的时间，不用set存储
        int[] last=new int[128];
        for(int i=0;i<128;i++){
            last[i]=-1;
        }
        int n=s.length();
        
        int res=0;
        int start=0;
        for(int i=0;i<n;i++){
            int index=s.charAt(i);
            start=Math.max(start,last[index]+1);//如果在之后存在重复字符，则start,则会更新start
            res=Math.max(res,i-start+1);
            last[index]=i;
        }
        return res;


        //窗口滑动+hash表存储已经存在的元素
        /*
        Set<Character> occ = new HashSet<Character>();
        int right=-1;
        int ans=0;
        for(int i=0;i<s.length();i++){
            if(i!=0){
                occ.remove(s.charAt(i - 1));
            }
            while( right+1<s.length() && !occ.contains(s.charAt(right+1)) ){
                occ.add(s.charAt(right+1));
                right+=1;
            }
            ans=Math.max(ans,right-i+1);
        }
        return ans;
        */
    }
}
```

## 567.字符串的排列

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        //滑动窗口 官解思路
        int n=s1.length();
        int m=s2.length();
        if(n>m){
            return false;
        }

        int[] cnt1=new int[26];
        int[] cnt2=new int[26];
        for(int i=0;i<n;i++){
            cnt1[s1.charAt(i)-'a']++;
            cnt2[s2.charAt(i)-'a']++;
        }
        //匹配前n个字符
        if (Arrays.equals(cnt1, cnt2)) {
            return true;
        }
        //开始滑动窗口,弹出第一个，增加后一个
        for (int i = n; i < m; ++i) {
            ++cnt2[s2.charAt(i) - 'a'];
            --cnt2[s2.charAt(i-n) - 'a'];
            if (Arrays.equals(cnt1, cnt2)) {
                return true;
            }
        }
        return false;

        /*性能极差
        for(int i=0;i<s2.length()-s1.length()+1;i++){
            int[] numbers=initnumbers(s1);
            for(int j=i;j<s1.length()+i;j++){
                numbers[s2.charAt(j)]--;
            }
            if(judge(numbers)){
                return true;
            }  
        }
        return false;
        */
    }
    /*
    public int[] initnumbers(String s1){
        int[] numbers=new int[128];
        for(int i=0;i<128;i++){
            numbers[i]=-0;
        }
        
        for(int i=0;i<s1.length();i++){
            numbers[s1.charAt(i)]++;
        }
        return numbers;
    }

    public boolean judge(int[] numbers){
        for(int i=0;i<numbers.length;i++){
            if(numbers[i]>0){
                return false;
            }
        }
        return true;
    }
    */

}
```

