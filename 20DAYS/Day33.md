# Day33

## 201. 数字范围按位与

```java
class Solution {
    public int rangeBitwiseAnd(int left, int right) {
        while(right>left){
            right &=right-1;
        }
        return right;
    }
}
```

