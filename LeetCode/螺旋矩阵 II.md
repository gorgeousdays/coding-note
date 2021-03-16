## 螺旋矩阵 II

日期：2021-3-16

### 题目

给你一个正整数 `n` ，生成一个包含 `1` 到 `n2` 所有元素，且元素按顺时针顺序螺旋排列的 `n x n` 正方形矩阵 `matrix` 。

```
输入：n = 3
输出：[[1,2,3],[8,9,4],[7,6,5]]
```

### 思路

创建矩阵 然后旋转遍历

### 算法

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        rows, columns = n, n
        matrix = [[0]*n for i in range(n)]#创建n*n的矩阵
        left, right, top, bottom = 0, columns-1, 0, rows-1
        nn = 1
        while nn <= n**2:
            for column in range(left, right+1):
                matrix[top][column] = nn
                nn += 1
            for row in range(top+1, bottom+1):
                matrix[row][right] = nn
                nn += 1
            for column in range(right-1, left, -1):
                matrix[bottom][column] = nn
                nn += 1
            for row in range(bottom, top, -1):
                matrix[row][left] = nn
                nn += 1
            left, right, top, bottom = left+1, right-1, top+1, bottom-1 
        return matrix



```

