# 创龙 AM5018

## 1. 设置minicom

- 安装minicom 

  ```
   sudo apt-get install minicom
  ```
  
- 配置步骤

  ```
  1. $ sudo minicom -s
  2. --> serial port setup
  3. --> serial device :        /dev/ttyUSB0
  4. --> Hardware Flow Control: no
  ```
## 2. SDK安装与交叉编译环境设置

- 安装TI原生SDK

  ```
  Host# ./ti-processor-sdk-linux-rt-am57xx-evm-04.03.00.05-Linux-x86-Install.bin
  ```

- 交叉编译环境设置

  ```
  实际就是把交叉编译工具链所在目录添加进环境变量PATH中
  1. Host#  sudo gedit /etc/profile
  2. 在profile文件最后添加 export PATH=$PATH:/home/tronlong/ti-processor-sdk-linux-rt-am57xx-evm-04.03.00.05/linux-devkit/sysroots/x86_64-arago-linux/usr/bin/
  3. Host#  source /etc/profile
  ```
- 

