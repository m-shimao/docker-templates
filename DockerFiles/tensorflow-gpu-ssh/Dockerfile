From tensorflow/tensorflow:latest-devel-gpu-py3

RUN apt-get update && apt-get install -y --no-install-recommends \
        vim \
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
        pillow

## default ssh setting
RUN echo "root:root" | chpasswd

RUN \
  sed -ri 's/^PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config \
  && sed -ri 's/^#GSSAPIAuthentication yes/GSSAPIAuthentication no/' /etc/ssh/sshd_config \
  && sed -ri 's/^UsePrivilegeSeparation yes/UsePrivilegeSeparation no/' /etc/ssh/sshd_config \
  && sed -ri 's/^UsePAM yes/UsePAM no/' /etc/ssh/sshd_config \
  && sed -ri 's/^PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config
