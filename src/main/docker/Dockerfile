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
	curl -L -k -o /usr/local/bin/jq https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 &&\
    chmod u+x /usr/local/bin/jq &&\    
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

RUN yum -y install   net-tools telnet openssh-clients libaio expect libarchive lzo  gcc gcc-c++  libtool libtool-ltdl libtool-ltdl-devel ncurses-devel      pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel unzip    libstdc++-devel  net-tools telnet openssh-clients *ltdl*  file   rpm-build build-essential libpcre3 libpcre3-dev libssl-dev libjpeg* libjpeg-dev libxslt1-dev  libcurl4-gnutls-dev libxml2-dev libmysql++-dev  libpng-dev libmcrypt-dev  libxpm-dev epel-release  dos2unix   net-tools telnet openssh-clients libaio expect || true
RUN yum -y install   libarchive lzo  gcc gcc-c++  libtool libtool-ltdl libtool-ltdl-devel ncurses-devel      pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel unzip    libstdc++-devel  net-tools telnet openssh-clients *ltdl*  file   rpm-build docker   nmap-ncat ntp subversion git telnet ntpdate net-tools expect traceroute tree vim wget zip unzip lsof tcpdump wireshark sysstat iotop iptraf nc iptables lftp dos2unix bridge-utils iproute jq  gcc-c++ libaio numactl.x86_64 passwd openssl openssh-server openssh-clients crontabs cronie net-snmp-devel libxml2-devel  || true
RUN yum -y install   libcurl-deve libevent libevent-devel  mysql-devel curl-devel  php php-gd php-mysql php-bcmath php-mbstring php-xml curl curl-devel net-snmp   net-snmp-devel perl-DBI  httpd mariadb*  mariadb-devel libxml2-devel  unixODBC unixODBC-devel libssh2 libssh2-devel OpenIPMI-devel openldap openldap-devel  libxml2 libxml2-devel openssl openssl-devel bzip2 bzip2-devel libcurl libcurl-devel libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel gmp gmp-devel libmcrypt libmcrypt-devel readline readline-devel libxslt libxslt-devel libjpeg.x86_64 libpng.x86_64  || true
RUN yum -y install   freetype.x86_64 libjpeg-devel.x86_64 libpng-devel.x86_64 freetype-devel.x86_64 libxml2*  *libxml2* bzip2-devel *bcmath* *mbstring* openldap openldap-devel libc-client-devel libcurl-devel enchant-devel libpng-devel libXpm-devel freetype-devel  libxslt-devel net-snmp-devel  libc-client-devel libicu-devel unixODBC-devel  aspell-devel readline-devel libxml2-devel libxml2   bzip2 perl pcre2 dos2unix   net-tools telnet openssh-clients libaio expect libarchive lzo  gcc gcc-c++  libtool libtool-ltdl libtool-ltdl-devel ncurses-devel      pcre-devel wget net-tools gcc zlib  || true
RUN yum -y install   zlib-devel make openssl-devel unzip    libstdc++-devel  net-tools telnet openssh-clients htop psacct    || true
RUN yum -y install    libevent libaio numactl.x86_64 kde-l10n-Chinese glibc-common  build-essential libpcre3  pcre*   pcre-devel libpcre3-dev libssl-dev libjpeg* libjpeg-dev libxslt1-dev  libcurl4-gnutls-dev libxml2-dev libmysql++-dev  libpng-dev libmcrypt-dev  libxpm-dev  dos2unix    || true
RUN yum -y install    iftop iptraf nc iptables lftp dos2unix bridge-utils iproute jq gcc gcc-c++ make  || true
RUN yum -y install    gnupg rpm-build    python-devel python-pip   httpd-tools nmap-ncat ntp subversion git telnet net-tools expect traceroute  tree vim wget zip unzip lsof tcpdump wireshark sysstat iotop  || true


# 时区设置为东八区和utf8编码支持
RUN  rm -rf /etc/localtime && ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime &&\
     echo 'ZONE="Asia/Shanghai"' > /etc/sysconfig/clock 

# 中文语言     
RUN  yum -y install kde-l10n-Chinese  && yum reinstall glibc-common && localedef -c -f UTF-8 -i zh_CN zh_CN.utf8  

RUN  echo 'export LANG=zh_CN.UTF-8'  >> /etc/profile && source /etc/profile &&\
     echo 'export LC_ALL=$LANG'  >> /etc/profile && source /etc/profile &&\     
     echo 'export LANGUAGE=zh_CN:zh'  >> /etc/profile && source /etc/profile   &&\
     echo "alias ll='ls -l --color=auto'" >> /etc/profile &&\
     echo "alias grep='grep --color=auto'" >> /etc/profile


# ssh
RUN echo '123456' | passwd --stdin root  &&\
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
RUN cd /etc/docker/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/etc/docker/daemon.json &&\
    cd /lib/systemd/system/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/lib/systemd/system/docker.service

# java   
RUN yum -y install java-1.8.0-openjdk-devel &&\    
    echo "export JAVA_HOME=$(ls -lrt /usr/bin/java | awk '{print  $11}' | xargs ls -lrt | awk '{print  $11}' | awk -F jre '{print $1}')" >> /etc/profile && source /etc/profile   &&\
    echo "export JRE_HOME=$JAVA_HOME/jre" >> /etc/profile && source /etc/profile   &&\
    echo "export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH" >> /etc/profile && source /etc/profile   &&\
    echo 'export JAVA_OPTS="$JAVA_OPTS -server -Xmx2048M  -Dfile.encoding=UTF-8  -Dsun.jnu.encoding=UTF-8 -Duser.language=zh  -Duser.timezone=Asia/Shanghai"'   >> /etc/profile && source /etc/profile   &&\
    cd /usr/bin/ && curl -O  https://raw.githubusercontent.com/qq275860560/base/master/src/main/centos/usr/bin/jstatd.all.policy &&\
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*
    
# nginx php python
RUN yum -y install nginx php php-fpm git logrotate npm && \
    sed -i '/;cgi.fix_pathinfo=1/c\cgi.fix_pathinfo=0' /etc/php.ini && \
    sed -i '/listen = 127.0.0.1:9000/c\listen = /var/run/php-fpm/php-fpm.sock' /etc/php-fpm.d/www.conf && \
    sed -i '/;listen.owner = nobody/c\listen.owner = nobody' /etc/php-fpm.d/www.conf && \
    sed -i '/;listen.group = nobody/c\listen.group = nobody' /etc/php-fpm.d/www.conf && \
    sed -i '/user = apache/c\user = nginx' /etc/php-fpm.d/www.conf && \
    sed -i '/group = apache/c\group = nginx' /etc/php-fpm.d/www.conf && \
    yum -y install python-setuptools && \
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*  


# go
RUN mkdir -p /go && chmod -R 777 /go && \
    yum -y install git golang && \
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*    

# node
RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash - && \
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*
	
RUN	wget https://dl.yarnpkg.com/rpm/yarn.repo -O /etc/yum.repos.d/yarn.repo && \
	yum -y install yarn && \	
	yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

# yarn
#RUN curl -o- -L https://yarnpkg.com/install.sh | bash && \	
#	 yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

# pip
RUN wget https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py	


		