##Lab 2##
本文档包括三个部分：DOL框架简介，DOL配置过程，实验心得。

###DOL框架描述###

DOL是一个能使应用自动映射到多处理器SHAPES结构平台的框架。DOL通常包含以下三部分：

- **DOL应用程序接口（API）**：提供计算和交流的路径，使SHAPES平台的平行分布式应用可用。
- **DOL功能仿真**：用以测试应用。
- **DOL映射优化**：计算出应用映射到SHAPES平台上的最佳映射。


###DOL配置过程###
1. 安装必要的环境

        $ sudo apt-get update：更新源信息。
        $ sudo apt-get install ant：安装Ant，用于自动化调用程序完成项目的编译，打包，测试等。
        $ sudo apt-get install openjdk-7-jdk：安装JDK，编译Java文件。
        $ sudo apt-get install unzip

2. 解压文件
           
        $ mkdir dol：新建dol的文件夹。
        $ unzip dol_ethz.zip -d dol：将dolethz.zip解压到 dol文件夹中
        $ tar -zxvf systemc-2.3.1.tgz：解压systemc

3. 编译system-c

        $ cd systemc-2.3.1：解压后进入systemc-2.3.1的目录下
        $ mkdir objdir：新建一个临时文件夹objdir
		$ cd objdir：进入该文件夹objdir
		$ ../configure CXX=g++ --disable-async-updates：运行configure(能根据系统的环境设置一下参数，用于编译)
		$ sudo make install：编译
		$ pwd：记录当前的工作路径
运行configure成功之后如下：

      ![Img1](https://thumbnail0.baidupcs.com/thumbnail/6a614cc769e6c25e8bbc01c6172eee4d?fid=974006230-250528-477534316028803&time=1474963200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-LcfvXmqcapS5ZpMch9Zq78JWcEo%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6278049049149683347&dp-callid=0&size=c710_u400&quality=100)

4. 编译DOL

		$ cd ../dol：进入DOL文件夹，修改build_zip.xml文件找到上面编译的systemc位置，修改如下：
		<property name="systemc.inc" value="YYY/include"/>
		<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
		（“YYY”为pwd记录下的工作路径）
		$ ant -f build_zip.xml all：编译
编译成功后如下：

    ![Img3](https://thumbnail0.baidupcs.com/thumbnail/24444f9c4870828527b8a4638b7408f2?fid=974006230-250528-868912421968638&time=1474963200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-XdZj1Koi0hYMZdGLWJBew0siYnQ%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6278193596330704952&dp-callid=0&size=c710_u400&quality=100)

5. 测试运行

		$ cd build/bin/main：进入build/bin/mian路径
		$ ant -f runexample.xml -Dnumber=1：运行第一个例子
测试运行成功：

	![Img4](https://thumbnail0.baidupcs.com/thumbnail/8bdf9a2f682b7d6130785be0dcd840b7?fid=974006230-250528-80252407065696&time=1474963200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-fm9O2gA8MJbEC9A5mGUrP68mN04%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6278230187595991045&dp-callid=0&size=c710_u400&quality=100)

###实验心得###
整个配置过程还是很顺利的，一些工具在之前的实验中也已经安装配置好了。唯一的bug还是因为一时大意漏改了路径。之后第一个测试例子也成功运行了。

DOL配置完之后，对它的整体框架有了更好的了解，在这个过程中同时也熟悉了Linux系统的操作。