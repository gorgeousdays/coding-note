# DAY22

## 1091. 二进制矩阵中的最短路径

```java
class Solution {
    int [][] dir=new int[][]{{0,1},{0,-1},{1,0},{-1,0},{1,1},{1,-1},{-1,1},{-1,-1}};
    public int shortestPathBinaryMatrix(int[][] grid) {
        int row=grid.length,col=grid[0].length;
        if(grid[0][0]!=0 ||grid[row-1][col-1]!=0){
            return -1;
        } 

        boolean[][] visited=new boolean[row][col];
        Queue<int[]> queue=new LinkedList<>();
        visited[0][0]=true;
        queue.offer(new int[]{0,0});
        int step=1;

        while(!queue.isEmpty()){
            int n=queue.size();
            while(n-->0){
                int[] cur=queue.poll();
                int x=cur[0],y=cur[1];
                if(x==row-1 &&y==col-1){
                    return step;
                }

                for(int i=0;i<dir.length;i++){
                    int cx=x+dir[i][0],cy=y+dir[i][1];
                    if(cx<0||cy<0||cx>=row||cy>=col||visited[cx][cy]==true||grid[cx][cy]==1){
                        continue;
                    }
                    visited[cx][cy]=true;
                    queue.offer(new int[]{cx,cy});
                }
            }
            step++;
        }
        return -1;
    }
}
```

## 130. 被围绕的区域

```java
class Solution {
    public void solve(char[][] board) {
        if(board==null||board.length==0||board[0].length==0){
            return;
        }
        int row=board.length,col=board[0].length;
        for(int i=0;i<row;i++){
            dfs(board,i,0);
            dfs(board,i,col-1);
        }
        for(int i=0;i<col;i++){
            dfs(board,0,i);
            dfs(board,row-1,i);
        }
        for(int i=0;i<row;i++){
            for(int j=0;j<col;j++){
                if(board[i][j]=='O'){
                    board[i][j]='X';
                }
                if(board[i][j]=='A'){
                    board[i][j]='O';
                }
            }
        }
        return;
    }
    public void dfs(char[][] board,int i,int j){
        if(i<0||j<0||i>=board.length||j>=board[0].length||board[i][j]!='O'){
            return;
        }
        board[i][j]='A';
        dfs(board,i-1,j);
        dfs(board,i+1,j);
        dfs(board,i,j-1);
        dfs(board,i,j+1);
        return;
    }
}
```

## 797.所有可能的路径

```java
class Solution {
    List<List<Integer>> res=new ArrayList<>();
    Stack<Integer> temp=new Stack<>();
    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {
        dfs(graph,0);
        return res;
    }
    public void dfs(int[][]graph,int n){
        temp.push(n);
        if(n==graph.length-1){
            res.add(new ArrayList<>(temp));
        }
        for(int i:graph[n]){
            dfs(graph,i);
        }
        temp.pop();
    }
}
```

