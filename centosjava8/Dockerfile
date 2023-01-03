
#docker pull centos
#download jdk-8u351-linux-x64.tar.gz from https://www.oracle.com/java/technologies/downloads/#java8
#account http://www.codebaoku.com/jdk/jdk-oracle-account.html

FROM centos
MAINTAINER name-q<1620206666@qq.com>
 
ENV MYPATH /usr/local
WORKDIR $MYPATH

#将镜像更改为vault.centos.org
#解决错误Error: Failed to download metadata for repo "appstream": Cannot prepare internal mirrorlist: No URLs in mirrorlist
RUN cd /etc/yum.repos.d/ && \
    sed -i -e "s|mirrorlist=|#mirrorlist=|g" /etc/yum.repos.d/CentOS-* && \
    sed -i -e "s|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g" /etc/yum.repos.d/CentOS-*

#安装vim编辑器
RUN yum -y install vim
#安装ifconfig命令查看网络IP
RUN yum -y install net-tools
#安装java8及lib库
RUN yum -y install glibc.i686
RUN mkdir /usr/local/java
#ADD 是相对路径jar,把jdk-8u171-linux-x64.tar.gz添加到容器中,安装包必须要和Dockerfile文件在同一位置
ADD jdk-8u351-linux-x64.tar.gz /usr/local/java/
#配置java环境变量
ENV JAVA_HOME /usr/local/java/jdk1.8.0_351
ENV JRE_HOME $JAVA_HOME/jre
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib:$CLASSPATH
ENV PATH $JAVA_HOME/bin:$PATH
 
#EXPOSE 80
 
CMD echo $MYPATH
CMD echo "success--------------ok"
CMD /bin/bash


#docker build -t centosjava8:1.0 .