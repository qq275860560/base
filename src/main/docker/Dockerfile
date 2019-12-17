from centos

MAINTAINER jiangyuanlin@163.com

# centos常用命令
RUN cd /etc/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/etc/yum.conf  &&\
	yum -y update &&\
	yum -y install   epel-release &&\
	yum -y groupinstall "Development tools" &&\
	yum -y groupinstall  "fonts" &&\
    curl -L -k -o /usr/local/bin/ctop    https://github.com/bcicen/ctop/releases/download/v0.7.1/ctop-0.7.1-linux-amd64 &&\
    chmod u+x /usr/local/bin/ctop &&\
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

RUN yum -y install   vim curl wget     

RUN yum -y install  jq tree lsof    expect  cronie     dos2unix  

RUN yum -y install   zip unzip

RUN yum -y install   gcc gcc-c++ make

RUN yum -y install   telnet wireshark net-tools  tcpdump traceroute  nc iptables

RUN yum -y install   subversion git

RUN yum -y install   openssh-server openssh-clients   passwd openssl  

RUN yum -y install   libssh2-devel openldap libtool-ltdl     unixODBC-devel libevent-devel      libxslt *mbstring* *bcmath*  libpcre3 php-mysql httpd mariadb* zlib-devel php-xml libarchive psacct  php-mbstring gnupg libpng-dev  readline-devel  libxslt1-dev lftp crontabs mysql-devel perl-DBI iptraf  libstdc++-devel libxml2-dev gmp  file OpenIPMI-devel libicu-devel libpcre3-dev net-snmp bzip2-devel libcurl4-gnutls-dev libpng-devel  php-gd libevent libxml2* libssl-dev aspell-devel numactl libjpeg-dev ntplibtool php-bcmath net-snmp-devel libXpm-devel php rpm-build pcre-devel iproute libtool-ltdl-devel libjpeg ncurses-devel libxslt-devel iotop unixODBC lzo openssl-devel gmp-devel  httpd-tools libmcrypt-dev openldap-devel nmap-ncat libcurl-deve python-devel python-pip  enchant-devel libpng libssh2 libc-client-devel sysstat libcurl build-essential pcre2 libmysql++-dev perl htop pcre* libxml2-devel libcurl-devel readline libjpeg-devel libaio *ltdl* libmcrypt *libxml2* libxml2 freetype-devel libjpeg* iftop zlib mariadb-devel  libmcrypt-devel libxpm-dev  freetype  || true

# 时区设置为东八区和utf8编码支持
RUN  rm -rf /etc/localtime && ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime &&\
     echo 'ZONE="Asia/Shanghai"' > /etc/sysconfig/clock 

# 中文语言     
#RUN  yum -y reinstall  kde-l10n-Chinese && yum -y reinstall glibc-common && localedef -c -f UTF-8 -i zh_CN zh_CN.utf8  

RUN  echo 'export LANG=zh_CN.UTF-8'  >> /etc/profile && source /etc/profile &&\
     echo 'export LC_ALL=$LANG'  >> /etc/profile && source /etc/profile &&\     
     echo 'export LANGUAGE=zh_CN:zh'  >> /etc/profile && source /etc/profile   &&\
     echo "alias ll='ls -l --color=auto'" >> /etc/profile &&\
     echo "alias grep='grep --color=auto'" >> /etc/profile


# ssh
RUN yum -y install passwd &&\
    echo '123456' | passwd --stdin root  &&\
    echo "root   ALL=(ALL)       ALL" >> /etc/sudoers &&\
    ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key  &&\
    ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key &&\
    mkdir -pv /root/.ssh/ &&\
    cd /root/.ssh/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.ssh/authorized_keys  &&\
    cd /root/.ssh/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.ssh/config  &&\
    cd /root/.ssh/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.ssh/id_rsa  &&\
    cd /root/.ssh/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.ssh/id_rsa.pub  &&\
    chmod -R 600 /root/.ssh/ &&\
    cd /etc/pam.d/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/etc/pam.d/sshd  &&\
    chmod -R 644 /etc/pam.d/sshd &&\
    cd /etc/ssh/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/etc/ssh/sshd_config  &&\
    chmod -R 600 /etc/ssh/sshd_config

# gpg
RUN mkdir -pv /root/.gnupg/ && cd /root/.gnupg/ &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/gpg.conf  &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/pubring.gpg  &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/pubring.gpg~  &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/random_seed  &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/secring.gpg  &&\
    curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/root/.gnupg/trustdb.gpg

# docker   
RUN yum -y install docker

# java   
RUN yum -y install java-1.8.0-openjdk-devel &&\    
    echo "export JAVA_HOME=$(ls -lrt /usr/bin/java | awk '{print  $11}' | xargs ls -lrt | awk '{print  $11}' | awk -F jre '{print $1}')" >> /etc/profile && source /etc/profile   &&\
    echo "export JRE_HOME=$JAVA_HOME/jre" >> /etc/profile && source /etc/profile   &&\
    echo "export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH" >> /etc/profile && source /etc/profile   &&\
    echo 'export JAVA_OPTS="$JAVA_OPTS -server -Xmx2048M  -Dfile.encoding=UTF-8  -Dsun.jnu.encoding=UTF-8 -Duser.language=zh  -Duser.timezone=Asia/Shanghai"'   >> /etc/profile && source /etc/profile   &&\
    cd /usr/bin/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/usr/bin/jstatd.all.policy &&\
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*
    
# nginx php
RUN yum -y install nginx php php-fpm git logrotate npm && \
    sed -i '/;cgi.fix_pathinfo=1/c\cgi.fix_pathinfo=0' /etc/php.ini && \
    sed -i '/listen = 127.0.0.1:9000/c\listen = /var/run/php-fpm/php-fpm.sock' /etc/php-fpm.d/www.conf && \
    sed -i '/;listen.owner = nobody/c\listen.owner = nobody' /etc/php-fpm.d/www.conf && \
    sed -i '/;listen.group = nobody/c\listen.group = nobody' /etc/php-fpm.d/www.conf && \
    sed -i '/user = apache/c\user = nginx' /etc/php-fpm.d/www.conf && \
    sed -i '/group = apache/c\group = nginx' /etc/php-fpm.d/www.conf && \
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*  


# go
RUN mkdir -p /go && chmod -R 777 /go && \
    yum -y install git golang && \
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*    

# node
RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash - && \
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*
	
RUN cd /etc/yum.repos.d/ && 	curl -O https://dl.yarnpkg.com/rpm/yarn.repo && \
	yum -y install yarn && \	
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

# yarn
#RUN curl -o- -L https://yarnpkg.com/install.sh | bash && \	
#	 yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

# pip
RUN cd /tmp && curl -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py	


		