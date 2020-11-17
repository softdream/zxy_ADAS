# zxy_ADAS

1.ros-install.sh is a script for installing the ros-kinetic tool in ubuntu16.04 environment.

Environment:
ubuntu16.04

Installation steps:
sh ros_install.sh

2. steps to install the arm-linux-gcc-4.4.3 environment
  2.1 download the source file from http://www.arm9.net/download.asp
  
  2.2 put the file into the directory: /usr/local
      and run:
      tar zxvf tar zxvf arm-linux-gcc-4.4.3-20100728.tar.gz
      vim /etc/profile
      add a sentence:
      export PATH=$PATH:/usr/local/opt/FriendlyARM/toolschain/4.4.3/bin
      source /etc/profile
      echo $PATH and check if the path is added correctly.
      
   2.3 use command: arm-linux-gcc -v to check if the tool is installed correctly.
   
   2.4 use command: arm-linux-gcc xxx.c -o xxx to compile the source file.
      
