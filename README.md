# dockerized-vim-ide
Dockerized VIM IDE

# building image

```
$ git clone https://github.com/JmilkFan/dockerized-vim-ide.git

$ cd dockerized-vim-ide
$ docker image build -t vim-ide:base ./base/
$ docker image build -t vim-ide:gcc-9.1.0 ./gcc-9.1.0/
$ docker image build -t vim-ide:vim-8.2 ./vim-8.2/
$ docker image build -t vim-ide:zsh-5.7.1 ./zsh-5.7.1/
```
