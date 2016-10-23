##DeadLock##
本文档包括四个部分：死锁实验结果，死锁产生的条件，死锁产生的原因，对死锁进一步理解后的实验优化。

###实验结果###
![IMG1](https://thumbnail0.baidupcs.com/thumbnail/ed3912e126c8e26a2a67041bf480f5bd?fid=974006230-250528-767696678340897&time=1477184400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-lXVsWUMvR05CK%2ByraqZmqBXVPaw%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6874484067149591869&dp-callid=0&size=c710_u400&quality=100)

###四个条件###
1、 互斥：每次资源只能被一个线程占有；

2、 占有并等待：一个线程在等待请求的资源时，保持已占有的资源不变；

3、 非抢占：资源仅在占有的线程结束后被自愿释放，不能被强行剥夺；

4、 循环等待：若干线程之间形成一种头尾相连的循环等待关系；

###死锁现象的解释###


![IMG](https://thumbnail0.baidupcs.com/thumbnail/cddc866f594c51d34bbf7bbe5851fe45?fid=974006230-250528-313602449156898&time=1477188000&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-qnrMuRoUClfY03qRJycIZALZVMg%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6874830519125665152&dp-callid=0&size=c710_u400&quality=100)
如上图所示，由于synchronized关键字，因此同一个对象的被描述的代码段只能执行一个。因此当a执行至b.last()时，由于b也在停在执行a.last()之前，因此产生冲突。此时a需要等待b的第一段执行完毕，同理b也处于等待a的过程。因此产生死锁。

###基于死锁理解的实验优化###
![IMG2](https://thumbnail0.baidupcs.com/thumbnail/e1c0962482c9d3acb64ed224e5cbf487?fid=974006230-250528-685974988671669&time=1477188000&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-zqeYbYNLdxhEp%2FBH2vNmvaqCRvM%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6874814693984368278&dp-callid=0&size=c710_u400&quality=100)
由于cpu的调度算法良好，因此在调度时很难等到a和b的同时执行至相互等待。因此我删除了count的等待时间，在a的线程中直接加入sleep休眠时间，令a停在b.last（）前，而b会在休眠结束前完成创建并被执行，从而停在a.last（），因此当休眠结束时，a、b会互相停止在第一段代码等待对方执行，从而陷入死锁。