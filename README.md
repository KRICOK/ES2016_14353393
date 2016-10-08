#<center>DOL配置报告</center>
##Description
####对于DOL框架的描述，我还真没有太多的体会，只知道是搭建在Linux中的一种环境，当然我是使用VMware安装了Ubuntu16来配置这个环境，需要使用ant工具和openjdk-7-jdk，也许在之后的学习中能明白更多吧，目前也的的确确没有什么很清楚的想法。
##How to install
####首先，需要搭建一些环境:
* $ sudo apt-get update
* $ sudo apt-get install ant
* $ sudo apt-get install openjdk-7-jdk
* $ sudo apt-get install unzip
####因为我是使用Ubuntu16，所以openjdk-7-jdk的源已经没有，所以可以选择安装openjdk-8-jdk或者openjdk-9-jdk，或者添加源，从而安装openjdk-7-jdk。这一部分比较简单，没有什么难点。
####然后我首先安装了VMware tools，自己下载了用来配置DOL的两个文件，然后将这两个文件直接拖入虚拟机（不得不说安装VMware tools可以省很多事）。
####新建dol文件夹
* $ mkdir dol
####这里dol文件夹会建在Home中，如下图：
![](https://cl.ly/1p0S1l0X2J2G/1.png)
####然后将dol_ethz.zip解压在dol文件中
* $ unzip dol_ethz.zip -d dol
####如下图：
![](https://cl.ly/3l0U3Q46303R/2.png)
####现在解压systemc
* $ tar -zxvf systemc-2.3.1.tgz
####这样会在home中出现一个systemc-2.3.1的文件夹如下图：
![](https://cl.ly/01300T0Z3R3l/3.png)
####在这之后我们需要编译systemc，进入systemc-2.3.1文件夹然后新建文件夹objdir，进入该文件夹，运行configure。
* $ cd systemc-2.3.1
* $ mkdir objdir
* $ cd objdir
* $ ../configure CXX=g++ --disable-async-updates
####注意在最后一行代码中“g++”与之后的“--”之间会有一个空格，这点不能忘记，不然会出现问题。以下是我从新在新的文件夹krico中完成这个过程之后的截图：
![](https://cl.ly/383l0q3a3K3t/4.png)
####然后输入$ sudo make install完成编译。然后记住路径，可以使用pwd来显示路径。对于我当时的路径应该是
![](https://cl.ly/2G0u2c151B3F/5.png)
####接下来就需要在dol中的build_zip.xml文件中找到如下的内容
* property name="systemc.inc" value="YYY/include"/
* property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/
####将其中“YYY”部分用上面的/home/krico/systemc-2.3.1来替换掉就可以开始编译DOL了
####首先输入$ ant -f build_zip.xml all进行编译，成功的话会显示build successful，然后可以运行第一个例子来检查，如下图：
![](https://cl.ly/1W0E25233D3L/7.png)
####成功出现下图：
![](https://cl.ly/0S1Y2l232z0B/6.png)
####注意这里很容易出现build failed，是因为时间的问题，那么需要在dol/build/bin/main下的runexample.xml中找到如下部分：
![](https://cl.ly/020b3f473F0c/8.png)
####将其修改为
![](https://cl.ly/1F3R3O3N1X1b/9.png)
####这样DOL的配置就完全成功了！
##Experimental experience
####这次实验呢，你会发现又很多奇奇怪怪的地方，也许你认为你按照ppt的指示一步步的去完成，但是结果并不和ppt上显示的正确结果一样，其实很多时候可以自己baidu或者重试来解决，比如有关于Ubuntu16怎么安装openjdk-7-jdk，其实在网络上搜索很快就可以得明确的方法和代码。也许你觉得很坑的地方其实早就有解决方案，重要的是自己有没有去找，去看解决办法，包括TA给的Q&A。
