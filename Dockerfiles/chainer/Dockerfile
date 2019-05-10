From nvidia/cuda:10.0-devel

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    libsm6 \
	libxext6 \
	libglib2.0-0 \
	libxrender1 \
	libxrender-dev \ 
    wget \
    curl \
    git \
    zip \
    nkf \
	gcc \
	make \
	sudo \
	openssl \
	libssl-dev \
    python3-dev python3-numpy python3-pip python3-tk python3-setuptools \
        && \
    apt-get clean

RUN pip3 install --upgrade pip
RUN pip3 install \
	opencv-python \
	Cython \
	pillow \
	matplotlib \
	IPython \
	jupyter \
    tqdm \
    albumentations \
    pandas \
    chainer \
    chainercv \
    cupy-cuda100 \
    ideep4py \
    scikit-learn

# 日本語化
RUN apt-get install -y --no-install-recommends \
    language-pack-ja-base \
    language-pack-ja \
        && \
    update-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja" && \
    apt-get clean

ENV LANG ja_JP.UTF-8

# JupyterNotebookのパスワード
RUN mkdir /root/.jupyter
COPY jupyter_notebook_config.py /root/.jupyter/
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
