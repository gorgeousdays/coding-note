# DAY14

## 190.颠倒二进制位

```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        //return Integer.reverse(n);

        int res=0;
        for(int i=0;i<32;i++){
            int last=n&1;
            res=res<<1|last;//左移结果添加最后一位
            n=n>>1;
        }
        return res;
    }
}
```

## 138.只出现一次的数字

```java
class Solution {
    public int singleNumber(int[] nums) {
       int res=nums[0];
       for(int i=1;i<nums.length;i++){
           res=res^nums[i];
       }
       return res;
    }
}
```

