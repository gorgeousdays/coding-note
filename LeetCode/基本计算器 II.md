## 基本计算器 II$^{*}$

日期：2021-3-11

### 题目

给你一个字符串表达式 `s` ，请你实现一个基本计算器来计算并返回它的值。

整数除法仅保留整数部分。

### 思路

与[昨天的题](https://leetcode-cn.com/problems/basic-calculator/)思路基本相近。由于存在四种运算符，则要考虑优先级

### 算法

```python
#python的eval函数
class Solution:
  def calculate(self, s: str) -> int:
     return eval(s.replace('/','//'))
```



```C++
//C++ LeetCode题解
class Solution {
public:
    int calculate(string s) {
        vector<int> stack;
        char sign = '+';
        int num = 0;
        int n = s.length();
        for (int i = 0; i < n; ++i) {
            if (isdigit(s[i])) {
                num = num * 10 + int(s[i] - '0');
            }
            if (!isdigit(s[i]) && s[i] != ' ' || i == n - 1) {
                switch (preSign) {
                    case '+':
                        stack.push_back(num);
                        break;
                    case '-':
                        stack.push_back(-num);
                        break;
                    case '*':
                        stack.back() *= num;
                        break;
                    default:
                        stack.back() /= num;
                }
                preSign = s[i];
                num = 0;
            }
        }
        return accumulate(stack.begin(), stack.end(), 0);//累加求和 三个形参 头两个指定要累加的元素范围 第三个形参则是累加的初值
    }
};
```

