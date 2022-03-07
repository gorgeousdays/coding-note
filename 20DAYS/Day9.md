# DAY9

## 542.01矩阵

```java
class Solution {
    static int[][] dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};


    public int[][] updateMatrix(int[][] mat) {
        //广度优先 从全部0点开始
        Queue<int[]> queue = new LinkedList<>();
        for(int i=0;i<mat.length;i++){
            for(int j=0;j<mat[0].length;j++){
                if(mat[i][j]==0){
                    queue.add(new int[]{i,j});
                }
                else{
                    mat[i][j]=-1;
                }
            }
        }
        //不断计算旁边点的值
        while(!queue.isEmpty()){
            int [] point=queue.poll();
            for(int d=0;d<4;d++){
                int x = point[0] + dirs[d][0];
                int y = point[1] + dirs[d][1];
                if(x>=0&&x<mat.length&&y>=0&&y<mat[0].length&&mat[x][y]==-1){
                    mat[x][y]=mat[point[0]][point[1]]+1;
                    queue.add(new int[]{x,y});
                }
            }
        }
        return mat;
    }
}
```

## 994.腐烂的橘子

```java
class Solution {
    public int orangesRotting(int[][] grid) {
        if(grid==null ||grid.length==0){
            return 0;
        }
        Queue<int[]> queue = new LinkedList<>();
        int count=0;//统计新鲜橘子数目
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[0].length;j++){
                if(grid[i][j]==2){
                    queue.add(new int[]{i,j});
                }
                else if(grid[i][j]==1){
                    count++;
                }
            }
        }
        int time=0;
        while(!queue.isEmpty()&&count>0){
            time++;
            int size=queue.size();//一定要先定义size 不然queue的size会不断变化
            //for(int i=0;i<queue.size();i++){
            for(int i=0;i<size;i++){
                int[] point=queue.poll();
                int x=point[0],y=point[1];
                if(x-1>=0&&grid[x-1][y]==1){
                    grid[x-1][y]=2;
                    count--;
                    queue.add(new int[]{x-1,y});
                }
                if(x+1<grid.length&&grid[x+1][y]==1){
                    grid[x+1][y]=2;
                    count--;
                    queue.add(new int[]{x+1,y});
                }
                if(y+1<grid[0].length&&grid[x][y+1]==1){
                    grid[x][y+1]=2;
                    count--;
                    queue.add(new int[]{x,y+1});
                }
                if(y-1>=0&&grid[x][y-1]==1){
                    grid[x][y-1]=2;
                    count--;
                    queue.add(new int[]{x,y-1});
                }
            }
        }

        return count==0?time:-1;
    }
}
```

