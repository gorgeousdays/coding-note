# DAY20

## 200. 岛屿数量

```java
class Solution {
    public int numIslands(char[][] grid) {
        int res=0;
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[0].length;j++){
                if(grid[i][j]=='1'){
                    res+=1;
                    dfs(grid,i,j);
                }
            }
        }
        return res;
    }
    public void dfs(char[][] grid,int i,int j){
        if(i>=grid.length||j>=grid[0].length||i<0||j<0){
            return;
        }
        if(grid[i][j]=='0'||grid[i][j]=='2'){
            return;
        }
        grid[i][j]='2';
        dfs(grid,i+1,j);
        dfs(grid,i-1,j);
        dfs(grid,i,j+1);
        dfs(grid,i,j-1);
    }
}
```

## 547. 省份数量

```java
class Solution {
    public int findCircleNum(int[][] isConnected) {
        int res=0;
        for(int i=0;i<isConnected.length;i++){
            if(dfs(isConnected,i)>0){
                res++;
            }
        }
        return res;
    }
    public int dfs(int[][] isConnected,int i){
        if(isConnected[i][i]!=1){
            return 0;
        }
        int res=1;
        isConnected[i][i]=0;
        for(int j=0;j<isConnected.length;j++){
            if(isConnected[i][j]==1){
                res+=dfs(isConnected,j);
            }
        }
        return res;
    }
}
```

