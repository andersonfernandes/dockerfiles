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

RUN add-apt-repository ppa:neovim-ppa/stable && apt update
RUN apt install -y neovim

RUN useradd -p $(openssl passwd -1 123456) -m -d /home/admin admin
RUN usermod -aG sudo admin

USER admin
WORKDIR /home/admin
