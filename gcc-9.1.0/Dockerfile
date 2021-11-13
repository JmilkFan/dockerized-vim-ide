FROM vim-ide:base

MAINTAINER fanguiju

# install gcc/c++ 9.1.0
ENV GCC_TAR=/opt/gcc-9.1.0.tar.gz
ENV GCC_SRC=/opt/gcc-9.1.0/
ENV GCC_PREFIX=/usr/local/gcc-9.1.0/

RUN curl https://mirrors.tuna.tsinghua.edu.cn/gnu/gcc/gcc-9.1.0/gcc-9.1.0.tar.gz -o $GCC_TAR
RUN tar zxvf $GCC_TAR -C /opt
WORKDIR $GCC_SRC
RUN bash ./contrib/download_prerequisites
RUN bash ./configure --prefix=$GCC_PREFIX --enable-bootstrap --enable-threads=posix --enable-checking=release --with-system-zlib --disable-multilib && make -j 4 && make install
RUN mv /usr/bin/gcc /usr/bin/gcc.4.8.5
RUN mv /usr/bin/g++ /usr/bin/g++.4.8.5
RUN update-alternatives --install /usr/bin/gcc gcc $GCC_PREFIX/bin/gcc 50
RUN update-alternatives --install /usr/bin/g++ g++ $GCC_PREFIX/bin/g++ 50
RUN echo 'export CC=/usr/local/gcc-9.1.0/bin/gcc' >> ~/.bashrc
RUN echo 'export CXX=/usr/local/gcc-9.1.0/bin/g++' >> ~/.bashrc
RUN echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/gcc-9.1.0/lib64' >> ~/.bashrc

CMD ["/bin/bash"]
