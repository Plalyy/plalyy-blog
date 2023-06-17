---
title: Make和Makefile
date: 2021-04-21 00:12
category: 技术
---

同样是本科毕设需要，学一下Make

<!--more-->

## Make和Makefile

Make，一般指GNU Make，用于完成自动化编译的工具。Makefile文件为Make指明编译规则。

Makefile描述整个工程的编译链接规则，基本规则为：

```makefile
TARGET...: DEPENDENCIES...
	COMMAND
	...
```

- TARGET：目标程序产生文件，如可执行文件、目标文件。目标也可以是clean等要执行的动作。
- DEPENDENCIES：用来产生目标的输入文件列表，一个目标常依赖多个文件。
- COMMAND：shell命令或shell下执行的程序，make执行的动作，每个命令行起始字符必须为TAB。

如果DEPENDENCIES中有文件更新，COMMAND就会执行。make命令回味每个TAB开始的命令创建一个Shell进程去执行。

## DEMO

目前有三个文件main.c、A.c、B.c，main依赖A和B。

```makefile
main: main.o A.o B.o
	gcc -o main main.o A.o B.o
main.o: main.c
	gcc -c main.c
A.o: A.c
	gcc -c A.c
B.o: B.c
	gcc -c B.c
clean:
	rm *.o
	rm main
```

首先使用make，此后若更改了A.c或B.c，重新执行make时会检查最后更改时间，只重新编译更改的文件。make clean清空编译文件。

## Makefile变量

## Makefile伪目标



## 参考

[1] make工具和Makefile的使用： https://blog.csdn.net/FRS2023/article/details/120839849