# DAY19

## 438. 找到字符串中所有字母异位

```java
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> ans=new ArrayList<>();

        int[] sArray=new int[26];
        int[] pArray=new int[26];
        for(char pchar:p.toCharArray()){
            pArray[pchar-'a']++;
        }
        int left=0,right=0;
        while(right<s.length()){
            sArray[s.charAt(right)-'a']++;
            while((right-left+1)==p.length()){
                if(Arrays.equals(sArray,pArray)){
                    ans.add(left);
                }
                sArray[s.charAt(left)-'a']--;
                left++;
            }
            right++;
        }
        return ans;
    }
}
```

## 713.乘积小于K的子数组

```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int count=0;
        int left=0,right=0;
        int ans=1;
        while(right<nums.length){
            ans*=nums[right];
            while(left<=right&&ans>=k){
                ans/=nums[left];
                left++;
            }
            count+=right-left+1;
            right++;
        }
        return count;
    }
}
```

## 209. 长度最小的子数组

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int length=10000;
        int left=0,right=0;
        int ans=0;
        while(right<nums.length){
            ans+=nums[right];
            while(left<=right && ans>=target){
                length=Math.min(length,right-left+1);
                ans-=nums[left];
                left++;
            }
            right++;
        }
        return length==10000?0:length;
    }
}
```

