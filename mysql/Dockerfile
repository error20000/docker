
# 基础镜像
FROM centos:7

# 维护信息
MAINTAINER liujian

# 文件复制到镜像 mysql-5.5.62-linux-glibc2.12-x86_64
ADD mysql-5.5.62-linux-glibc2.12-x86_64.tar.gz /usr/local/mysql/

# Mysql安装
ENV JAVA_HOME /usr/local/java/jdk1.8.0_192
ENV PATH ${PATH}:${JAVA_HOME}/bin

#容器支持ssh
RUN yum install -y openssh-server openssh-clients net-tools \
	&& echo "123456" | passwd --stdin root \
	&& ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key \
	&& ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key  \
	&& ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key   

# 开放端口
EXPOSE 22

# 容器启动时运行的命令
CMD ["/usr/sbin/sshd", "-D"]