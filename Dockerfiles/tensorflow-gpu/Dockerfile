From tensorflow/tensorflow:latest-devel-gpu-py3

RUN apt-get update && apt-get install -y --no-install-recommends \
        wget \
        curl \
        git \
        zip \
        nkf \
        gcc \
        make \
        sudo \
        openssl \
        openssh-server \
        libssl-dev \
        && \
    apt-get clean

RUN pip install --upgrade pip
RUN pip install \
        opencv-python \
        Cython \
        pillow \
        xlrd

# 日本語化
RUN apt-get install -y --no-install-recommends \
    language-pack-ja-base \
    language-pack-ja \
        && \
    update-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja" && \
    apt-get clean

ENV LANG ja_JP.UTF-8

# JupyterNotebookのパスワード
ENV PASSWORD password

# Vim
RUN apt-get install -y --no-install-recommends \
    vim \
        && \
    apt-get clean

RUN \
    curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

COPY ./vimrc /root/.vimrc

RUN vim -c PlugInstall -c q -c q

WORKDIR /root/volume
