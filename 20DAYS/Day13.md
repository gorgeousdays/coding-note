# DAY13

## 231.2 的幂

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return (n&(n-1))==0 && n>0;
    }
}
```

## 191.位1的个数

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int res=0;
        while(n!=0){
            res+=(n&1);
            n=n>>>1;//算术右移>> 会超时  要用逻辑右移>>>
        }
        return res;
    }
}
```

