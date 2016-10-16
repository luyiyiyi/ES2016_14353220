##Lab3##
本文档包括修改结果，修改过程解释以及实验感想。

###修改结果###
example1.dot：

<img src="http://thumbnail0.baidupcs.com/thumbnail/6c110054794c14ed50bb1dfae7e7fdd7?fid=2852440090-250528-42030781948216&time=1476619200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-tQ1p49RGpAuj%2BSdr4C0CpJOFAic%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6722404797765262950&dp-callid=0&size=c710_u400&quality=100" weight="20%" height="20%" />


example2.dot：

![Img2](http://thumbnail0.baidupcs.com/thumbnail/3cdd218d8a1b29e5101653ce9cbf1dd4?fid=2852440090-250528-758432215962430&time=1476619200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-NE4UATZc1lrvIcem1l5x9W0Y7HU%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6722367146160810233&dp-callid=0&size=c710_u400&quality=100)

###修改过程###
example1：

    由于现在需要输出的是立方结果，因此需要在square.c中修改计算表达式，改为i=i*i*i，这样就可以得到输入经过三次乘积的结果。

example2：

    这个例子中是需要修改迭代的次数，生产者由经过三条通道变成经过两条通道的计算，因此减少一次迭代次数，在iterator中修改次数为2。

###实验感想###
本次的实验在理解后并掌握dol的执行过程后不难完成，主要是着重理解以下三方面：

1. *.c文件：生产者和消费者的c文件中包括初始函数，信号产生函数和信号消费函数，判断进程什么时候被执行或销毁。而在执行进程的c文件中则是包含了计算关系。
2. xml文件：包含了连接关系。process是进程，port是进程中的端口，sw_channel是通道。通过定义input和output把相关的端口和通道连接起来。特别注意的是每条通道需要连接两个端口。


