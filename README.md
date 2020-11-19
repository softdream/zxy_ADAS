# 开发环境配置
## 一、开发环境要求
本项目要求在 Ubuntu16.04 环境下配置 ROS，arm交叉编译环境和常用的工具库：Opencv, PCL和Eigen库，以下分别介绍各工具的配置步骤。<br>

## 二、 ROS-kinetic 的安装
### 1. ros-kinetic 所依赖的系统
       ros-kinetic 对应 Ubuntu16.04，ros-melodic 对应 Ubuntu18.04， 可根据你所使用的 Ubuntu 版本选择对应的 ros 版本。<br>
### 2. ros-kinetic 的安装步骤
#### 2.1 配置源
``` sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' ```<br>
#### 2.2 设置keys
``` sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 ```<br>
#### 2.3 更新源
```sudo apt-get update```<br>
#### 2.4 安装完全版ROS
```sudo apt-get install ros-kinetic-desktop-full```<br>
完全版ros包含了rviz，gazebo，rqt等等各种工具.<br>
#### 2.5 配置环境变量
将路径添加到 ```~/.bashrc```文件中<br>
```echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc```<br>
```source ~/.bashrc```<br>
#### 2.6 安装依赖
```sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential```
#### 2.7 初始化rosdep
```sudo apt install python-rosdep```<br>
```sudo rosdep init```<br>
```rosdep update```<br>

### 3. 通过脚本安装ros-kinetic
运行```sh ros_install.sh```脚本可直接在Ubuntu16.04环境下安装好ros-kinetic.<br>

## 三、ARM交叉编译工具链 arm-linux-gcc 的安装
### 1. 版本要求
用户可根据需求选择 arm-linux-gcc 的版本，本文以 arm-linux-gcc 4.4.3 为例，在 Ubuntu16.04 环境下安装配置arm交叉编译环境, 更高版本的安装方式与此相同。<br>
### 2. 安装步骤
#### 2.1 下载 arm-linux-gcc 压缩包

#### 2.2 将压缩包解压到文件夹中
```sudo tar -zxvf arm-linux-gcc-4.4.3.tar.gz-c/```<br>

#### 2.3 在 ```/usr/local``` 目录下新建一个文件夹 ```/arm``` 用来保存所有库文件
 ```cd /usr/local```<br>
 ```mkdir arm```<br>
#### 2.4 将```/toolschain/4.4.3``` 目录下的所有文件拷贝到 ```/usr/local/arm```文件夹中
```sudo chmod 777 /usr/local/arm```<br>
```sudo cp -rf ./arm-linux-gcc 4.4.3/toolschain/4.4.3 /usr/local/arm```<br>
#### 2.4 配置环境变量
打开 ```~/.bashrc```文件，在文件的末尾添加：<br>
 ```export PATH=$PATH:/usr/local/bin``` <br>
 退出执行<br>
 ```source ~/.bashrc```<br>
#### 2.5 检测环境变量是否配置成功
执行 ```echo $PATH``` <br>
如果显示 ```/usr/local/arm/bin``` 则说明环境变量配置成功。<br>

#### 2.6 检测安装是否成功
可通过执行```arm-linux-gcc -v```查看当前安装的编译工具链版本号，如果能正确显示版本号说明安装成功。<br>

## 三、Ubuntu16.04 环境下 Opencv4.3.0 的安装配置
#### 1. 安装 CMake
```sudo apt-get install cmake```<br>
#### 2. 安装依赖环境
```sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg-dev libswscale-dev libtiff5-dev```<br>
```sudo apt-get install libgtk2.0-dev```<br>
```sudo apt-get install pkg-config```<br>
#### 3. 下载 Opencv4.3.0
https://opencv.org/releases/ <br>
#### 4. 解压
```unzip opencv-4.3.0.zip```<br>
#### 5. 新建 build 文件夹
``` cd opencv-4.3.0```<br>
```mkdir build```<br>
#### 6. 运行 cmake command
```cd build```<br>
```sudo cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local .. ```
#### 7. 编译
```sudo make -j8```<br>
#### 8. 安装
```sudo make install```<br>
#### 9. 配置环境变量
打开 ld.so.conf 文件<br>
```sudo vim /etc/ld.so.conf```<br>
在文件末尾添加：<br>
```include /usr/local/lib```<br>
运行```sudo ldconfig```<br>
打开 bash.bashrc 文件<br>
```sudo vim /etc/bash.bashrc```<br>
在文件末尾添加：<br>
```PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig```
```export PKG_CONFIG_PATH```<br>
运行```source /etc/bash.bashrc```<br>
#### 10. 检测安装是否成功
```pkg-config opencv --modversion```<br>
如果能够正确显示版本号，则安装成功。<br>

## 四、Ubuntu16.04 环境下的 PCL 库安装配置
#### 1. 安装依赖
```sudo apt-get update```<br>
```sudo apt-get install git build-essential linux-libc-dev```<br>
```sudo apt-get install cmake cmake-gui ```<br>
```sudo apt-get install libusb-1.0-0-dev libusb-dev libudev-dev```<br>
```sudo apt-get install mpi-default-dev openmpi-bin openmpi-common```<br>  
```sudo apt-get install libflann1.8 libflann-dev```<br>
```sudo apt-get install libeigen3-dev```<br>
```sudo apt-get install libboost-all-dev```<br>
```sudo apt-get install libvtk5.10-qt4 libvtk5.10 libvtk5-dev```<br>
```sudo apt-get install libqhull* libgtest-dev```<br>
```sudo apt-get install freeglut3-dev pkg-config```<br>
```sudo apt-get install libxmu-dev libxi-dev```<br> 
```sudo apt-get install mono-complete```<br>
```sudo apt-get install qt-sdk openjdk-8-jdk openjdk-8-jre```<br>

#### 2. 下载 pcl最新 源码
``` git clone https://github.com/PointCloudLibrary/pcl.git ```<br>

#### 3. 编译源码
``` cd pcl```<br>
```mkdir build```<br>
```cd build```<br>
```cmake -DCMAKE_BUILD_TYPE=None -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_GPU=ON -DBUILD_apps=ON -DBUILD_examples=ON -DCMAKE_INSTALL_PREFIX=/usr ..```<br>
```make```<br>
#### 4. 安装
```sudo make install```<br>

## 五、 Ubuntu16.04 环境下 Eigen 库的配置安装
### 1. apt-get 方式安装
#### 1.1 安装步骤
执行 ```sudo apt-get install libeigen3-dev```<br>
该方法默认将 Eigen 库安装至 ```/usr/local/include```文件夹中,可将之复制到 ```/usr/include``` 文件夹中: <br>
```sudo cp -r /usr/local/include/eigen3 /usr/include```<br>


### 2. 源码方式安装
#### 2.1 下载源码
http://eigen.tuxfamily.org/index.php?title=Main_Page <br>
#### 2.2 解压缩
``` tar -zxvf eigen-3.3.8.tar.gz```<br>
#### 2.3 编译
```cd eigen-3.3.8```<br>
```mkdir build```<br>
```cd build```<br>
```cmake ..```<br>
```make```<br>
#### 2.4 安装
```sudo make install```<br>




      
