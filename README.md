# Linux-record

## install-cmake
1.下载二进制CMake文件 官方下载页面：  
https://cmake.org/download/  

2.解压cmake文件包:   
tar -xvf cmake-xx.tar.gz  

3.移动到系统文件目录内:   
mv cmake-xx /usr/local/cmake  

4.写入终端环境并更新:   
echo 'export PATH="/usr/local/cmake/bin:$PATH"' >> ~/.bashrc  
source ~/.bashrc  

5.cmake --version  

PS:  
更新版本 --> 重复1 2 3


## CentOS7 安装GCC 11
来源：  
[CentOS7 安装GCC 11](https://blog.csdn.net/weixin_53213086/article/details/128063036)  
  
[CentOS 7 下载最新版gcc和依赖](https://www.cnblogs.com/codeRhythm/p/13906360.html#:~:text=%E5%9C%A8%E7%BA%BF%E5%AE%89%E8%A3%85%20sudo%20yum%20install%20-y%20centos-release-scl%20sudo%20yum,install%20-y%20devtoolset-9-gcc%20devtoolset-9-gcc-c%2B%2B%20%23%20%E5%AE%89%E8%A3%85%E4%BA%86%E4%B9%8B%E5%90%8E%2C%E5%B9%B6%E6%B2%A1%E6%9C%89%E6%9B%BF%E6%8D%A2%E6%97%A7%E7%9A%84%2C%E6%89%80%E4%BB%A5%E8%BF%99%E9%87%8C%E9%80%89%E6%8B%A9%E8%BF%9E%E6%8E%A5%E5%88%B0%E6%9C%80%E6%96%B0%E7%9A%84gcc%2Fg%2B%2B%20echo%20%22s)  
  
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

# Install Latest Git ( Git 2.x ) on CentOS 7 / RHEL 7  
第一种：  
1.git --version  
2.  
sudo yum -y remove git  
sudo yum -y remove git-*  

3.sudo yum -y install https://packages.endpointdev.com/rhel/7/os/x86_64/endpoint-repo.x86_64.rpm  

4.sudo yum install git  

第二种：  
1.  
sudo yum -y remove git*  
sudo yum -y install epel-release  
sudo yum -y groupinstall "Development Tools"  
sudo yum -y install wget perl-CPAN gettext-devel perl-devel  openssl-devel  zlib-devel curl-devel expat-devel  getopt asciidoc xmlto docbook2X  
sudo ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi    

2.  
sudo yum -y install wget curl  
export VER="v2.41.0"  
wget https://github.com/git/git/archive/${VER}.tar.gz  
tar -xvf ${VER}.tar.gz  
rm -f ${VER}.tar.gz  
cd git-*  
make configure  
sudo ./configure --prefix=/usr  
sudo make  
sudo make install

3. git --version  
