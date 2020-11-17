# zxy_ADAS

## 1.ros-install.sh is a script for installing the ros-kinetic tool in ubuntu16.04 environment.

### Environment:
ubuntu16.04<br>

### Installation steps:
run command: **sh ros_install.sh** <br>

## 2. steps to install the arm-linux-gcc-4.4.3 environment

### 2.1 download the source file from http://www.arm9.net/download.asp <br>
  
### 2.2 put the file into the directory: /usr/local <br>
### 2.3 tar zxvf tar zxvf arm-linux-gcc-4.4.3-20100728.tar.gz <br>
### 2.4 vim /etc/profile <br>
### 2.5 export PATH=$PATH:/usr/local/opt/FriendlyARM/toolschain/4.4.3/bin <br>
### 2.6 source /etc/profile <br>
### 2.7 echo $PATH and check if the path is added correctly. <br>
      
### 2.8 use command: arm-linux-gcc -v to check if the tool is installed correctly. <br>
   
### 2.9 use command: arm-linux-gcc xxx.c -o xxx to compile the source file. <br>
      
