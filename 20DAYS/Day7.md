# DAY7

## 733.图像渲染

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int newColor) {
        int target=image[sr][sc];
        if(target!=newColor){
            dfs(image,sr,sc,target,newColor);
        }  
        return image;
    }
    public void dfs(int[][] image,int sr,int sc,int target,int newColor){
        if(image[sr][sc]==target){
            image[sr][sc]=newColor;
            if(sr+1<image.length){
                dfs(image,sr+1,sc,target,newColor);
            }
            if(sr-1>=0){
                dfs(image,sr-1,sc,target,newColor);
            }
            if(sc+1<image[0].length){
                dfs(image,sr,sc+1,target,newColor);
            }
            if(sc-1>=0){
                dfs(image,sr,sc-1,target,newColor);
            }
        }
    }
}
```

## 695.岛屿的最大面积

```java
class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        int max=0;
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[0].length;j++){
                max=Math.max(dfs(grid,i,j),max);
            }
        }
        return max;
    }
    public int dfs(int[][] grid,int i,int j){
        if(i<0||j<0||i>=grid.length||j>=grid[0].length||grid[i][j]==0){
            return 0;
        }
        grid[i][j]=0;
        int ans=1;
        ans+=dfs(grid,i-1,j);
        ans+=dfs(grid,i+1,j);
        ans+=dfs(grid,i,j+1);
        ans+=dfs(grid,i,j-1);
        return ans;
    }
}
```

