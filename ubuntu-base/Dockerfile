FROM ubuntu:18.04
MAINTAINER Anderson Fernandes <fernandesanderson14@gmail.com>

RUN apt update && apt install -y \
      build-essential \
      software-properties-common \
      python-dev \
      python-pip \
      python3-dev \
      python3-pip \
      sudo \
      libc6-dev \
      gcc \
      g++ \
      make \
      dpkg-dev \
      git \
      curl \
      tmux

RUN useradd -p $(openssl passwd -1 123456) -m -d /home/admin admin
RUN usermod -aG sudo admin

RUN add-apt-repository ppa:neovim-ppa/stable && apt update
RUN apt install -y neovim
RUN mkdir -p /home/admin/.config/nvim/
COPY config/nvim/init.vim /home/admin/.config/nvim/
RUN curl -fLo /home/admin/.local/share/nvim/site/autoload/plug.vim --create-dirs \
      https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

RUN mkdir /home/admin/workspace/

RUN chown -R admin /home/admin/
USER admin

RUN nvim +PlugInstall +qall > /dev/null

WORKDIR /home/admin
