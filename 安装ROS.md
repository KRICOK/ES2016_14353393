#安装ROS

###首先，由于以前的虚拟机无论如何用尽千方百计都不能连上网络，所以我重新安装了一个ubuntu，专门来做这个安装ROS

###直接根据TA给的ppt找到那个网址，然后根据网址的顺序来一步步的安装这个ROS
* 第一步是添加软件源，一旦添加了正确的软件源，操作系统就知道去哪里下载程序，并根据命令自动安装软件，输入下面的指令。
* sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
* sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

![](https://github.com/KRICOK/ES2016_14353393/blob/master/first.png?raw=true)

* 需要更新apt，输入以下代码
* sudo apt-get update

![](https://github.com/KRICOK/ES2016_14353393/blob/master/second.png?raw=true)

* 接着就是开心（坑爹）的安装过程了，和ppt上说的一样，耗时的的确确很长。下面是命令和最后完成安装之后的截图，实在是太长了，所以只能截最后完成的地方。
* sudo apt-get install ros-kinetic-desktop-full

![](https://d17oy1vhnax1f7.cloudfront.net/items/1H0A2H2y1141280X3y07/three.png?v=ac1bb01d)

* 初始化rosdep
* sudo rosdep init
* rosdep update

![](https://d17oy1vhnax1f7.cloudfront.net/items/2E392k041V0W442F1I2r/4.png?v=4284cceb)

* 环境设置
* echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc 
* source ~/.bashrc
* 安装rosinstall，同样只是截图到最后完成安装的部分，也比较长。
* sudo apt-get install python-rosinstall

![](https://d17oy1vhnax1f7.cloudfront.net/items/2G3P0k1o1F3h3R3e2Z1r/5.png?v=8761b1c6)

###经过上面的步骤你的ROS就安装完成并且配置齐全。

###至于实验感想，这次实验不过是按照步骤把ROS安装完成，没有特别多的想法，对了，安装耗时的确很长。
