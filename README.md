# Wise2C Apt Source for Docker/K8S/Ceph/NFS installation
Wise2C Apt Source for Docker/K8S/Ceph/NFS installation

使用方法

Apt Source服务器安装好docker，直接运行命令：

docker run -d -p 2008:2008 --name=apt-source wise2c/apt-source:v1.15.0

在需要安装docker/k8s/ceph/nfs的其它主机上：

注释原来source.list原来内容（记得先备份），只添加 ：

###############################################

deb http://apt-source-server-ip:2008/debs apt-source-server-ip wise2c main
deb-src http://apt-source-server-ip wise2c main

###############################################

上面的 apt-source-server-ip 请写为上述服务器的真实IP地址

接着执行一次apt-get update命令后即可直接用 apt-get install命令命令安装相关软件了。例如：

apt-get install docker docker-python docker-compose

apt-get install rsync python-chardet jq nfs-utils
  
apt-get install kubernetes-cni kubectl kubelet kubeadm

apt-get install ceph-deploy ceph ceph-radosgw rbd-nbd rbd-mirror
