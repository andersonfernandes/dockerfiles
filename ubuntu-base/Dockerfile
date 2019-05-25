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
      wget \
      zsh \
      tmux

RUN add-apt-repository ppa:neovim-ppa/stable && apt update
RUN apt install -y neovim
RUN curl -fLo /home/doe/.local/share/nvim/site/autoload/plug.vim --create-dirs \
      https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

RUN useradd -p $(openssl passwd -1 123456) -m -d /home/doe doe
RUN usermod -aG sudo doe
RUN chsh doe --shell /bin/zsh

RUN mkdir -p /home/doe/workspace/
RUN mkdir -p /home/doe/.config/nvim/
RUN chown -R doe /home/doe/

USER doe

RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
ENV ZSH_THEME avit
ENV TERM screen-256color
ENV LANG en_US.UTF-8
ENV LC_CTYPE en_US.UTF-8

COPY config/tmux/.tmux.conf /home/doe/
COPY config/nvim/init.vim /home/doe/.config/nvim/

RUN nvim +PlugInstall +qall > /dev/null

WORKDIR /home/doe

CMD ["zsh"] 
