# STL基础篇

## 1. 什么是C++标准模板库（STL）？

STL，即**标准模板库 STL**（Standard Template Library）。

- 是 C++ 标准库的一部分，不需要单独安装，只需要#include 头文件。

- STL 就是借助模板把常用的数据结构及其算法都实现了一遍，并且做到了**数据结构和算法的分离**。

## 2. STL六大部件

- 容器（Containers）
- 分配器（Allocators）
- 算法（Algorithm）
- 迭代器（Iterators）
- 适配器（Adapters）
- 仿函数（Functors）

## 3. 基础使用 Vector

vector（矢量），是一种「**变长数组**」，即“自动改变数组长度的数组”。

### 3.1  引入

```c++
#include <vector>
using namespace std;
```

### 3.2 定义

```c++
// vector<类型名> 变量名
vector<int> name;
vector<double> name;
vector<char> name;
vector<struct node> name;
vector<vector<int> > name;//注意：> >之间要加空格

// vector数组就是一个一维数组,如果定义成vector数组的数组，那就是二维数组。
vector<int> array[SZIE]; //二维变长数组
```

```c++
// 二维数组中，它的一维形式就是地址。
#include <iostream>
using namespace std;

int main(){
    int arr[3][2];//定义一个3行2列的地址
    cout<<arr[0]<<endl; //输出arr第1行的地址
    cout<<arr[1]<<endl; //输出arr第2行的地址
    cout<<arr[2]<<endl; //输出arr第3行的地址
    return 0;
}
// vector容器也可以这样理解
```

```
0x61fe00 //arr第1行的地址
0x61fe08 //arr第2行的地址
0x61fe10 //arr第3行的地址
```

### 3.3 元素访问

```c++
// 下标访问
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> vi;
    vi.push_back(1);
    cout<<vi[0]<<endl;
    return 0;
}
```

```c++
// 迭代器访问
// 迭代器（iterator）可以理解为指针： vector<类型名>::iterator 变量名;
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    //v.begin()返回v的首元素地址
    vector<int>::iterator it=v.begin();
    for (int i = 0; i < v.size(); i++)
    {
       cout<<it[i]<<" ";
    }
    /*for (int i = 0; i < v.size(); i++)
    {
       cout<<*(it+i)<<" ";
    }*/
    return 0;
}
```

```
0 1 2 3 4
```

与此同时，迭代器与for循环还有一种优雅的写法。

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    //vector的迭代器不支持it<v.end()的写法，因此循环条件只能it!=v.end()
    for (vector<int>::iterator it=v.begin(); it!=v.end();it++)
    {
        cout<<*it<<" ";
    }
    return 0;
}
// 与遍历字符串有异曲同工之妙
/*
	string str;
    str="Hello World";
    for (int i = 0; str[i]!='\0'; i++)
    {
        cout<<str[i]<<" ";
    }

*/
```

### 3.4 常用函数

**（1）push_back()**

```c++
void std::vector<int>::push_back(const int &__x)
```

在vector后面添加一个元素item

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    return 0;
}
```

**（2）pop_back()**

```c++
void std::vector<int>::pop_back()
```

栈元素的压入和弹出就是push和pop

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    cout<<"pop_back前:"<<endl;
    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    cout<<endl;
    v.pop_back();
    cout<<"pop_back后:"<<endl;

    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    return 0;
}
```

```
pop_back前:
0 1 2 3 4
pop_back后:
0 1 2 3
```

**（3）size()**

```c++
std::size_t std::vector<int>::size()
```

返回vector中所含元素的个数，时间复杂度为O(1)

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    cout<<v.size()<<endl;
    return 0;
}
```

**（4）clear()**

```c++
void std::vector<int>::clear()
```

**一键清空vector中的所有元素**，**时间复杂度为O(N)**，其中N为vector中原属和元素的个数。

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    v.clear();
    cout<<endl;
    cout<<"size = "<<v.size()<<endl;
    return 0;
}
```

**（5）insert()**

```c++
insert(__position,__x);
insert(要插入的地址，要插入的元素);

参数：
__position：– A const_iterator into the %vector.
__x:– Data to be inserted.
```

是根据指定位置在vector中插入元素

```c++
#include <iostream>
#include <vector>
using namespace std;

int main(){
    vector<int> v;
    for (int i = 0; i < 5; i++)
    {
        v.push_back(i);
    }
    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    v.insert(v.begin()+2,-1); //将-1插入v[2]的位置
    cout<<endl;
    for (int i = 0; i < v.size(); i++)
    {
        cout<<v[i]<<" ";
    }
    return 0;
}
```

```
0 1 2 3 4 
0 1 -1 2 3 4
```

**（6）erase()**

```c++
erase(__position);
erase(__positionBegin,__positionEnd);
```

同样，与clear()简单粗暴清空vector不同的是erase()，删除指定位置的元素。

erase()有两种用法：

- 删除一个元素

  ```c++
  #include <iostream>
  #include <vector>
  using namespace std;
  
  int main(){
      vector<int> v;
      for (int i = 0; i < 5; i++)
      {
          v.push_back(i);
      }
      for (int i = 0; i < v.size(); i++)
      {
          cout<<v[i]<<" ";
      }
      //删除v[3]
      v.erase(v.begin()+3);
      cout<<endl;
      for (int i = 0; i < v.size(); i++)
      {
          cout<<v[i]<<" ";
      }
      return 0;
  }
  ```

  ```
  0 1 2 3 4 
  0 1 2 4
  ```

- 删除一个区间内的元素

  ```c++
  #include <iostream>
  #include <vector>
  using namespace std;
  
  int main(){
      vector<int> v;
      for (int i = 0; i < 5; i++)
      {
          v.push_back(i);
      }
      for (int i = 0; i < v.size(); i++)
      {
          cout<<v[i]<<" ";
      }
      //删除v[1]到v[4]的元素
      v.erase(v.begin()+1,v.begin()+4);
      cout<<endl;
      for (int i = 0; i < v.size(); i++)
      {
          cout<<v[i]<<" ";
      }
      return 0;
  }
  ```

  ```
  0 1 2 3 4 
  0 4
  ```

### 3.5 vector常见用途

**（1）储存数据**

vector本身可以作为数组使用，而且在一些元素个数不确定的场合可以很好地节省空间。

**（2）用邻接表存储图**

使用vector实现邻接表，更为简单。
