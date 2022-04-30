# webserver-project

## 运行项目的注意事项
1. 需要修改项目中网站的根目录，在http_conn.cpp文件中14行，修改网页.index.html所在文件夹的路径
2. 生成可执行文件命令行： `g++ *.cpp -o app -pthread`
3. 运行可执行文件app： ./app 10000
4. 浏览器访问服务器：服务器IP地址:10000/index.html
5. 压力测试：先cd进入test_presure\webbench-1.5文件夹，然后使用 `make` 命令，
 ```cpp
 ./webbench -c 1000 -t 5 服务器IP地址:10000/index.html
参数：
   -c 表示客户端数 
   -t 表示时间
```
## locker.h
线程同步机制封装类
```CPP
// 互斥锁类
class locker

// 条件变量类
class cond

// 信号量类
class sem
```

## threadpool.h 
线程类
```CPP
// 线程池类，将它定义为模板类是为了代码复用，模板参数T是任务类
template<typename T>
class threadpool
```
## http_conn.h
定义http_conn类，http_conn类主要解析HTTP请求，然后生成响应

## http_conn.cpp
http_conn类成员函数具体实现和几个epoll需要的函数

## main.cpp
主函数，创建套接字，实现与客户端进行连接，并加入epoll对象，使用线程池处理事件
