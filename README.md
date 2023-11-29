# Linux-record

## install-cmake
1.下载二进制CMake文件 官方下载页面：https://cmake.org/download/  
2.解压cmake文件包: tar -xvf cmake-xx.tar.gz  
3.移动到系统文件目录内: mv cmake-xx /usr/local/cmake  
4.写入终端环境并更新: path echo 'export PATH="/usr/local/cmake/bin:$PATH"' >> ~/.bashrc source ~/.bashrc  
5.cmake --version  

PS:  
更新版本 --> 重复1 2 3


## CentOS7 安装GCC 11
1.先卸载以前的旧版本  
yum remove gcc  
yum remove gdb  
  
2.验证卸载  
gcc -v  
g++ -v  
gdb  
执行这三个命令都会报错  

3.执行如下命令  
sudo yum install scl-utils  
sudo yum install centos-release-scl  

4.查看 SCL 软件源下提供哪些软件集  
yum list all --enablerepo='centos-sclo-rh' | grep "devtoolset"  

5.安装需要的工具链（如果需要安装gcc 11，就下devtoolset-11-toolchain；如果需要安装gcc10，就下devtoolset-10-toolchain；gcc 9、gcc 8等以此类推）  
//直接下载开发的工具链，它会自动把 gcc, gcc-c++, make, gdb 等依赖也都完整下载下来  
sudo yum install -y devtoolset-11-toolchain  

6.配置环境变量,在/etc/profile文件末尾添加如下的代码  
&ensp;&ensp;&ensp;第一种：  
&ensp;&ensp;&ensp;&ensp;&ensp;PATH=$PATH::/opt/rh/devtoolset-11/root/usr/bin  
&ensp;&ensp;&ensp;&ensp;&ensp;export PATH  
&ensp;&ensp;&ensp;&ensp;&ensp;sudo scl enable devtoolset-11 bash  
&ensp;&ensp;&ensp;第二种：  
&ensp;&ensp;&ensp;&ensp;&ensp;echo "source /opt/rh/devtoolset-9/enable" >> /etc/profile  
&ensp;&ensp;&ensp;&ensp;&ensp;source /etc/profile  




