# NOTE

1. queue的参数传递为浅拷贝，修改后无法更新到原对象（1014）

2. 定义数组一定要赋初值（1016）

3. 排序时注意多个条件，如分数相同则序号小的在前，此外求rank的时候考虑分数相同rank相同的情况（1025）

4. 有些时候输出单例用is，复例用are（1035）

5. unordered_map的顺序并不是插入顺序, 可以考虑用vector<pair<string,string>>来代替。(1035)

6. 读取一行string时，如果string带空格  不能用cin>>s 要用getline(cin, s)

7. while(!s.empty() && s.top() == v[current] 获取stack的top时要先判空

8. isdigit()和isalpha()来判断char是否数字或字符（1061）

9. 有的时候超出数据类型，要考虑上下溢出（1065）

10. string头文件 stoi()函数将n进制的字符串转为10进制  to_string()将数值转化为字符串  排序string时用的cmp函数是char a, char b（1069）

11. 掌握gcd函数，还有负数的情况（1081）

12. BST中序遍历是自小到大(1099)

13. 如果能通过测试样例，但是提交后wa了，可能是测试样例的特殊性导致代码某处出错（1030 dis[s] = 0而不是dis[0]=0 起点不是0）

14. 直接输出字符串超时 采用printf("%s\n",it->c_str());string 转char* 输出更快 不超时（1047） 需要回顾一下字符串的方法

15. set无法通过索引访问（1063）            

16. 完全二叉树可以用性质做 root=1，当前节点i，左孩子2i，右孩子2*i+1。(1064)

17. isalnum兼有isdigit()和isalpha()两者功能  tolower()字母转小写（1071）

18. dfs太深可能会段错误， 可以采用bfs(1091)

19. lower_bound和upper_bound

20. `s.earse(s.begin())`移除字符串s中的第一个字符；`s.insert(0, n, '0');`在字符串s前加n个0

21. `reverse(begin(v), end(v))`可以倒转vector或者数组中的值

22. `is_permutation(v1.begin(), v1.end(), v2.begin())`判断v2是否是v1的一个序列，返回值0或1

23. 全排列

    ```c++
    string s = "12345";
    do {
    cout << s << endl;
    }while(next_permutation(s.begin(), s.end()));
    ```

24. `fill`在`#include<algorithm>`中，用法`fill(e[0], e[0] + 500 * 500, INF)`

25. `getline(cin, s)`前面如果有换行，要在前面加`getchar()`吸收换行符

26. string转字符数组char *c

    ```c++
    string s = "abc";
    char *c = s.c_str();
    ```

27. 浮点数的比较不能直接用==，可以使用自定义eps = 1e-8

    

