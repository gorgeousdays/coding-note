# DAY4

## 344.反转字符串

```java
class Solution {
    public void reverseString(char[] s) {
        int n=s.length;
        for(int i=0;i<n/2;i++){
            char temp=s[i];
            s[i]=s[n-i-1];
            s[n-i-1]=temp;
        }

    }
}
```

## 557.反转字符串中的单词 III

```java
class Solution {
    public String reverseWords(String s) {
        StringBuilder ans = new StringBuilder();
        for(String str:s.split(" ")){
            char[] chars=str.toCharArray();
            reverseString(chars);
            ans.append(chars).append(" ");
        }
        return ans.toString().trim(); //最后会多加空格
    }
    public void reverseString(char[] s) {
        int n=s.length;
        for(int i=0;i<n/2;i++){
            char temp=s[i];
            s[i]=s[n-i-1];
            s[n-i-1]=temp;
        }

    }
}
```

