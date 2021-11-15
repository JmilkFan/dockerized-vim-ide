FROM centos:centos7.9.2009

MAINTAINER fanguiju

# prepare install
RUN mkdir /etc/yum.repos.d/backup && mv /etc/yum.repos.d/*.repo /etc/yum.repos.d/backup
RUN curl https://mirrors.aliyun.com/repo/Centos-7.repo -o /etc/yum.repos.d/CentOS-Base.repo
RUN yum install epel-release -y
RUN yum install https://packages.endpoint.com/rhel/7/os/x86_64/endpoint-repo-1.7-1.x86_64.rpm -y
RUN yum clean all && yum makecache && yum repolist

# install Ctags
RUN yum install ctags -y
RUN ln -s /usr/bin/ctags /usr/local/bin/ctags

# install Cscope
RUN yum install cscope -y

# gcc/c++ 9.1.0 dependent
RUN yum install -y bzip2 zlib-devel make gcc gcc-c++

# vim dependent
RUN yum install -y git python-pip python-devel python3 python3-devel ncurses-devel
RUN pip install cmake
RUN pip3 install pylint

# zsh dependent
RUN yum install -y autoconf

CMD ["/bin/bash"]
