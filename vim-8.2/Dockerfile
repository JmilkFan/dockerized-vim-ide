FROM vim-ide:gcc-9.1.0

MAINTAINER fanguiju

# install vim
COPY vimrc /etc/vim/vimrc

ENV VIM_SRC=/opt/vim
ENV VIM_PREFIX=/usr/local/vim/

RUN git clone --depth 1 -b v8.2.3592 https://github.com/vim/vim $VIM_SRC
WORKDIR $VIM_SRC
RUN git checkout -b v8.2.3592
RUN bash ./configure --prefix=$VIM_PREFIX --with-features=huge --enable-multibyte --enable-pythoninterp=yes --enable-python3interp=yes --with-python-config-dir=/usr/lib64/python2.7/config --with-python3-config-dir=/usr/lib64/python3.6/config-3.6m-x86_64-linux-gnu --enable-gui=gtk2 --enable-cscope && make && make install
RUN echo 'export PATH=$PATH:/usr/local/vim/bin' >> /root/.bashrc

# install Vundle
RUN git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
RUN $VIM_PREFIX/bin/vim -c 'PluginInstall' -c 'qall' -c 'qa!'

# install YCM
RUN export CC=/usr/local/gcc-9.1.0/bin/gcc && export CXX=/usr/local/gcc-9.1.0/bin/g++ && export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/gcc-9.1.0/lib64 && python3 ~/.vim/bundle/YouCompleteMe/install.py --clang-completer

CMD ["/bin/bash"]
