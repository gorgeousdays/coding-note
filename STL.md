#  STL

## vector

```c++
//初始化
vector<int> nums;
vector<int> nums{1,2,3};
vector<int> nums(n);//长度为n,全0
vector<int> nums(n,2);//长度为n,全2
vector<vector<bool> > dp(m, vector<bool>(n,true));//m*n的true数组

//成员函数
bool empty();
size_type size();
reference back();//返回最后一个元素的引用
void push_back(const value_type& val);
void pop_back();
```

## string

```c++
//初始化
string s;
string s = "abc";

//成员函数
size_t size();
bool empty();
void push_back(char c);
void pop_back();
string substr(size_t pos, size_t len);
int strcmp(const char *str1, const char *str2);//strcmp返回的是字符ascii码的差值
//string.find函数
int index = s.find('a');//返回下标
int index = s.find('a', 5);//从下标5开始找,寻找a出现的第一次下标
if(s.find('a', 5) != string::npos){
    int index = s.find('a', 5);
}
//strcmp	
```

## unordered_map

```c++
//初始化
unordered_map<int, int> m;
unordered_map<string, vector<int> > m;

//成员函数
size_type size();
bool empty();
size_type count(const key_type &key);//返回key出现的次数,但由于不存在重复键,返回0或1,可用于判断是否存在key
size_type erase(const key_type &key);//通过key清除hashmap的键值对
```

## unordered_set

```c++
//初始化
unordered_set<int> s;
unordered_set<string> s;

//成员函数
size_type size();
bool empty();
size_type count(const key_type &key);
pair<iterator, bool> insert(const key_type &key);
size_type erase(const key_type &key);//删除key,删除成功返回1，不存在返回0
```

## queue

```c++
//初始化
queue<int> q;
queue<string> q;

//成员函数
bool empty();
size_type size();
void push(const value_type &val);
value_type& front();
void pop();
```

## stack

```c++
//初始化
stack<int> s;
stack<string> s;

//成员函数
bool empty();
size_type size();
void push(const value_type &val);
value_type& top();
void pop();

```

## pair

```c++
vector<pair<string, int> > v;//构建

pair<string, int> temp = makr_pair("abc", 123);
v.push_back(temp);
cout << temp.first << " " << temp.second << endl;
cout << v[0].first << " " << v[0].second << ednl;
```

