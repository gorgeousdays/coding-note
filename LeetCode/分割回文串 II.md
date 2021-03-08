# 分割回文串 II$^{*}$

日期：2021-3-8    

### 题目

给你一个字符串 `s`，请你将 `s` 分割成一些子串，使每个子串都是回文。返回符合要求的 **最少分割次数** 。

### 思路

由题意得，字符串$s[0...n]$可以分隔成为子串$s_1[0...i],s_2[(i+1)...j],...,s_k[(m+1)...n]$,且每个子串都为回文串。

由于存在$s_k[(m+1)...n]$为回文串，则字符串$s[1..n]$的最少分割次数$f[n]$等于$f[m]+1$，由此构建状态转移方程
$$
f[i]=\cases{
min_{0\le j\le i}\{f[j]\}+1,s[(j+1)...i]为回文串\\
0,s[0...i]为回文串
}
$$
**关于回文串判断算法：**

$g(i,j)$表示$s[i...j]$是否为回文串
$$
g(i,j)=\cases{True,i\ge j\\
g(i+1,j-1)\land(s[i]=s[j]),otherwise
}
$$


### 算法

```c++
class Solution {
public:
    int minCut(string s) {
        int n = s.size();
        vector<vector<int>> g(n, vector<int>(n, true));
        //预处理 先计算所有串的状态 判断是否为回文串 遍历所有情况
        for (int i = n - 1; i >= 0; --i) {
            for (int j = i + 1; j < n; ++j) {
                g[i][j] = (s[i] == s[j]) && g[i + 1][j - 1];
            }
        }

        vector<int> f(n, INT_MAX);
        
        for (int i = 0; i < n; ++i) {
             // 如果 s[0...j]为回文，则无须分割
            if (g[0][i]) {
                f[i] = 0;
            }
            //如果不是回文
            else {
                // 如果与前面形成回文，则消耗一次分割次数
                for (int j = 0; j < i; ++j) {
                    if (g[j + 1][i]) {
                        f[i] = min(f[i], f[j] + 1);
                    }
                }
            }
        }
        return f[n - 1];
    }
};
```

