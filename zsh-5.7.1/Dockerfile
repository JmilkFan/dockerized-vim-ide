FROM vim-ide:vim-8.2

MAINTAINER fanguiju

# install zsh
COPY zshrc /root/.zshrc
COPY p10k.zsh /root/.p10k.zsh

ENV ZSH_SRC=/opt/zsh
ENV ZSH_PREFIX=/usr/local/zsh

RUN git clone -b zsh-5.7.1 https://github.com/zsh-users/zsh.git $ZSH_SRC
WORKDIR $ZSH_SRC
RUN git checkout -b 5.7.1
RUN bash ./Util/preconfig && ./configure --prefix=$ZSH_PREFIX && make -j 20 install.bin install.modules install.fns
RUN command -v $ZSH_PREFIX/bin/zsh | tee -a /etc/shells
RUN chsh -s $ZSH_PREFIX/bin/zsh
RUN echo 'export PATH=$PATH:/usr/local/zsh/bin' >> /root/.zshrc

# install oh-my-zsh
RUN bash -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k

CMD ["/usr/local/zsh/bin/zsh"]
