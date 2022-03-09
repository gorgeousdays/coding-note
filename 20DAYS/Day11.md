# Day11

## 77.组合

```java
//参考评论区题解，核心思想是树的剪枝
class Solution {
    private List<List<Integer>> ans=new ArrayList<>();
    public List<List<Integer>> combine(int n, int k) {
        getcombine(n,k,1,new ArrayList<>());
        return ans;
    }
    public void getcombine(int n, int k, int start, List<Integer> list){
        if(k==0){
            ans.add(new ArrayList<>(list));
            return;
        }
        for(int i = start;i <= n - k + 1;i++) {
            list.add(i);
            getcombine(n, k - 1, i+1, list);
            list.remove(list.size() - 1);
        }
    }
}
```

## 46.全排列

```java
class Solution {
    private List<List<Integer>> ans=new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        List<Integer> output = new ArrayList<Integer>();
        for (int num : nums) {
            output.add(num);
        }
        int n=nums.length;
        
        getpermute(n,output,0);
        return ans;
    }
    public void getpermute(int n,List<Integer> output,int first){
        if (first == n) {
            ans.add(new ArrayList<Integer>(output));
        }
        for (int i = first; i < n; i++) {
            // 动态维护数组
            Collections.swap(output, first, i);
            // 继续递归填下一个数
            getpermute(n, output, first + 1);
            // 撤销操作
            Collections.swap(output, first, i);
        }
    }
}
```

## 784.字母大小写全排列

```java

class Solution {
    private List<String> ans=new ArrayList<>();
    public List<String> letterCasePermutation(String s) {
        char[] str = s.toCharArray();
        process(str, 0);
        return ans;
    }

    public void process(char[] str, int index){
        if(index == str.length){
            ans.add(String.valueOf(str));
            return;
        }
        if(str[index] > '9' || str[index] < '0'){ 
            process(str, index + 1); // 不改变大小写，继续传递
            changeFormat(str, index); // 改变大小写，大写变小写，小写变大写
            process(str, index + 1); // 改变后继续传递
        } else{  // 如果是数字。什么都不变。继续传递
            process(str, index + 1);
        }   
    }
    public void changeFormat(char[] str, int index){
        if(str[index] >= 'A' && str[index] <= 'Z'){
            str[index] = (char)(str[index] - 'A' + 'a');
        } else if(str[index] >= 'a' && str[index] <= 'z'){
            str[index] = (char)(str[index] - 'a' + 'A');
        }
    }
}
```

