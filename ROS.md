##配置ROS##

###ROS配置步骤###
1、建立源列表

    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

2、配置关键字

    sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

3、更新源
 
    sudo apt-get update

4、全安装

	sudo apt-get install ros-jade-desktop-full

5、初始化rosdep（允许系统兼容性）

	sudo rosdep init
	rosdep update

6、环境配置

	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
    source ~/.bashrc

7、获取rosinstall（命令行工具）

	sudo apt-get install python-rosinstall

经过上面7个步骤后，ros就配置成功了。截图如下：

![Img4](https://thumbnail0.baidupcs.com/thumbnail/2c659fcd92afac8d114c343823a51e78?fid=378574653-250528-49414629607651&time=1478534400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-dwdzYXvuuNs8vP4NECmp92N%2FWdw%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=7236650307645746245&dp-callid=0&size=c710_u400&quality=100)
