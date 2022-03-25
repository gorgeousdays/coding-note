# DAY25

## 17.电话号码的字母组合

```java
class Solution {
    List<String> res=new ArrayList<>();

    public List<String> letterCombinations(String digits) {
        String[] str={"abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        for(int i=0;i<digits.length();i++){
            combinations(str[digits.charAt(i)-'0'-2]);
        }
        return res;
    }
    public void combinations(String s){
        List<String> temp=new ArrayList<>();
        for(int i=0;i<s.length();i++){
            if(res.isEmpty()){
                temp.add(s.substring(i,i+1));
            }
            else{
                for(String sres:res){
                    temp.add(sres+s.substring(i,i+1));
                }
            }
        }
        res=temp;
    }

}
```

## 22.括号生产

```java
class Solution {
    List<String> res=new ArrayList<>();
    public List<String> generateParenthesis(int n) {
        generate(n,n,"");
        return res;
    }
    private void generate(int left,int right,String s){
        if(left==0 && right==0){
            res.add(s);
            return;
        }
        if(left>0){
            generate(left-1,right,s+"(");
        }
        if(right>left){
            generate(left,right-1,s+")");
        }
    }
}
```

## 79.单词搜索

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board[0].length;j++){
                if(search(board,word,i,j,0)){
                    return true;
                }
            }
        }
        return false;
    }
    private boolean search(char[][] board,String word,int i,int j,int k){
        if(k>=word.length()){
            return true;
        }
        if(i<0||j<0||i>=board.length||j>=board[0].length||board[i][j]!=word.charAt(k)){
            return false;
        }
        board[i][j]+=1000;//防止使用两遍
        boolean res=search(board,word,i-1,j,k+1)||search(board,word,i+1,j,k+1)||search(board,word,i,j-1,k+1)||search(board,word,i,j+1,k+1);
        board[i][j]-=1000;
        return res;
    }
}
```

