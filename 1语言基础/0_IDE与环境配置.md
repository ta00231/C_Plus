# IDE 选择 与 环境配置

## 1. IDE 选择

- VSCode

## 2. 环境配置

- 远程Linux服务器连接
- 远程C++环境适配

## 3. 干活！

### 1）下载并安装 VSCode（官网地址如下）

[Download Visual Studio Code - Mac, Linux, Windows](https://code.visualstudio.com/Download)

![image-20231005103729624](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005103729624.png)

### 2）配置远程连接

- 进入插件界面，安装三个必要插件。

![image-20231005104419625](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005104419625.png)

- 进入配置文件，配置连接地址等。

![image-20231005104302390](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005104302390.png)

​	Host：服务器别名；

​	HostName：Linux服务器地址；

​	User：连接的用户名。

![image-20231005104616239](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005104616239.png)

- 点击连接按钮，连接配置好的服务器（此处为4090）。

![image-20231005105721695](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005105721695.png)

![image-20231005105745879](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005105745879.png)

- 选择系统 Linux，并在框内输入密码。

![image-20231005110044811](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005110044811.png)

![image-20231005110131121](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005110131121.png)

- 登陆成功后界面如下：

![image-20231005110245524](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005110245524.png)

![image-20231005110617225](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005110617225.png)

### 3）C++ 环境配置

- 安装编写与编译插件。

![image-20231005110909823](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005110909823.png)

![image-20231005111040774](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005111040774.png)

- 在Linux上安装一下 cmake：

  [Linux（Ubuntu）安装cmake & 配置cmake PATH-CSDN博客](https://blog.csdn.net/qq_38327353/article/details/107528837#:~:text=通过下载ssh文件安装cmake 1 sudo wget https%3A%2F%2Fcmake.org%2Ffiles%2Fv3.18%2Fcmake-3.18.0-Linux-x86_64.sh 2,sudo chmod %2Bx cmake-3.18.0-Linux-x86_64.sh 3 sudo .%2Fcmake-3.18.0-Linux-x86_64.sh)

  ![image-20231005133836187](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005133836187.png)

- 点击齿轮，进入Extension Settings，设置cmake远程路径

  ![image-20231005135210691](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005135210691.png)

- 创建文件夹，在本地试图打开；

  ![image-20231005111725619](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005111725619.png)

- 创建文件 “test.cpp” 

  ![image-20231005113048035](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005113048035.png)

- 编写测试代码，简单测试一下环境

  ```C++
  // test.cpp
  #include<iostream>
  using namespace std;
  
  int main(){
      cout << "Hello Remote Server!" << endl;
      return 0;
  }
  ```

  需要先装一个调试的插件

  ![image-20231005114240439](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005114240439.png)

  按下F5，选择g++，开启Debug

  ![image-20231005122005861](C:\Users\Not a Literary Gaint\AppData\Roaming\Typora\typora-user-images\image-20231005122005861.png)

# 操作来源参考

[2023年最全VSCode远程Linux搭建C++工程开发利器 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/599003187)

[vscode的远程开发与调试——以C/Ｃ＋＋为例_vscode远程debug-CSDN博客](https://blog.csdn.net/lengye7/article/details/129401570)

[一键搞定 VSCode 下的 C/C++基本开发环境配置 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/137760796)

[Linux（Ubuntu）安装cmake & 配置cmake PATH-CSDN博客](https://blog.csdn.net/qq_38327353/article/details/107528837#:~:text=通过下载ssh文件安装cmake 1 sudo wget https%3A%2F%2Fcmake.org%2Ffiles%2Fv3.18%2Fcmake-3.18.0-Linux-x86_64.sh 2,sudo chmod %2Bx cmake-3.18.0-Linux-x86_64.sh 3 sudo .%2Fcmake-3.18.0-Linux-x86_64.sh)

[windows10下VScode构建树莓派pico开发环境遇坑笔记_hell0joe的博客-CSDN博客](https://blog.csdn.net/hellojef/article/details/129038984)

