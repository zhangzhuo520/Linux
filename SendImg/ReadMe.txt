程序简介：
1.可以发送一个文件夹中的所有图片，在接受端分别保存图片和图片有关的信息。
2.程序的接受部分写死了，测试的话可以自己改发送位置和接受位置，代码中有注释。
3.使用C语言以及APUE中的一些技术，包括多线程以及其他。
4.重点在于对内存的手动管理，防止内存泄漏等比较严重的问题，但是到目前为止，内存问题悬而未决。
5.使用数据包有序传输（前期使用sendfile，发现这样做很粗糙，后改为二进制数据包有序发送）。
6.服务器端有两条线程，一条负责读取图片信息，一条负责发送图片信息，通过两个指针控制单向链表的形式进行文件内容的读取以及即时释放。
7.客户端用过单线程逻辑处理数据包。
使用方法：
1.切换到server/client中的build文件夹中
2.cmake ..
3.make
4.cd src/
5. ./ser 或者 ./cli

目前存在的问题：
1.valgrind目前人然跑不通，甚至有一次把memcheck跑死了。问题提示：conditional jump or move depends on uninitialised values.
2.推测应该为缓冲区初始化问题，不过使用memset之后依然存在问题。
3.内存问题，功夫不够，仍需磨练。

个人总结：
1.踩了很多以前没遇到的坑，真正的感受到手动管理内存的恐怖。
2.学到了一丢丢的工程思维，对程序的要求提高到新的高度。
3.零零碎碎的知识点遇到了一大堆，等日后总结。

