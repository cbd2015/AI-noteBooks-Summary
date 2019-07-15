# AI-noteBooks-Summary
（1）install NVIDIA Driver
    Ubuntu系统更新-->NVIDIA binary dirver-version 384.130来自nvidia-384（专有，tested）

# Install   Docker-ce
  2、Ubuntu 14.04 16.04 (使用apt-get进行安装)
  （2）Blog Reference参考： https://www.cnblogs.com/xzkzzz/p/8918704.html
    使用官方安装脚本自动安装：  curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
复制代码
### step 1: 安装必要的一些系统工具
sudo apt-get update
sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common
### step 2: 安装GPG证书
curl -fsSL http://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
#### Step 3: 写入软件源信息
sudo add-apt-repository "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"
#### Step 4: 更新并安装 Docker-CE
sudo apt-get -y update
sudo apt-get -y install docker-ce

#### 安装指定版本的Docker-CE:
#### Step 1: 查找Docker-CE的版本:
#### apt-cache madison docker-ce
####   docker-ce | 17.03.1~ce-0~ubuntu-xenial | http://mirrors.aliyun.com/docker-ce/linux/ubuntu xenial/stable amd64 Packages
####   docker-ce | 17.03.0~ce-0~ubuntu-xenial | http://mirrors.aliyun.com/docker-ce/linux/ubuntu xenial/stable amd64 Packages
#### Step 2: 安装指定版本的Docker-CE: (VERSION 例如上面的 17.03.1~ce-0~ubuntu-xenial)
#### sudo apt-get -y install docker-ce=[VERSION]
复制代码
3、CentOS 7 (使用yum进行安装)
复制代码
#### step 1: 安装必要的一些系统工具
	sudo yum install -y yum-utils device-mapper-persistent-data lvm2
#### Step 2: 添加软件源信息
	sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
#### Step 3: 更新并安装 Docker-CE
  sudo yum makecache fast
	sudo yum -y install docker-ce
#### Step 4: 开启Docker服务
	sudo service docker start

#### 注意：
#### 官方软件源默认启用了最新的软件，您可以通过编辑软件源的方式获取各个版本的软件包。例如官方并没有将测试版本的软件源置为可用，你可以通过以下方式开启。同理可以开启各种测试版本等。
#### vim /etc/yum.repos.d/docker-ce.repo
####   将 [docker-ce-test] 下方的 enabled=0 修改为 enabled=1
####
#### 安装指定版本的Docker-CE:
#### Step 1: 安装指定版本的docker-ce-selinux
#### yum install https://download.docker.com/linux/centos/7/x86_64/stable/Packages/docker-ce-selinux-17.03.2.ce-1.el7.centos.noarch.rpm
#### Step 2: 查找Docker-CE的版本:
#### yum list docker-ce.x86_64 --showduplicates | sort -r
####   Loading mirror speeds from cached hostfile
####   Loaded plugins: branch, fastestmirror, langpacks
####   docker-ce.x86_64            17.03.1.ce-1.el7.centos            docker-ce-stable
####   docker-ce.x86_64            17.03.1.ce-1.el7.centos            @docker-ce-stable
####   docker-ce.x86_64            17.03.0.ce-1.el7.centos            docker-ce-stable
####   Available Packages
#### Step 3: 安装指定版本的Docker-CE: (VERSION 例如上面的 17.03.0.ce.1-1.el7.centos)
#### sudo yum -y install docker-ce-[VERSION]
复制代码
4、Centos7 rpm包安装
复制代码
如果您无法使用Docker的仓库来安装Docker，则可以下载该 .rpm文件以供手动安装。每次要升级Docker时，都需要下载一个新文件。
1、访问 https://download.docker.com/linux/centos/7/x86_64/stable/Packages/ 并下载.rpm您想要安装的Docker版本的文件。
2、安装Docker CE，安装docker之前需要安装docker-ce-selinux 将下面的路径更改为您下载Docker软件包的路径。
yum install docker-ce-selinux-***.ce-1.el7.centos.noarch.rpm
yum install docker-ce-***.ce-1.el7.centos.x86_64.rpm
3、启动Docker。
systemctl start docker
复制代码
