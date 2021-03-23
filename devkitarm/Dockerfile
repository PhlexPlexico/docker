FROM devkitpro/toolchain-base

MAINTAINER Dave Murphy <davem@devkitpro.org>

RUN dkp-pacman -Syyu --noconfirm 3ds-dev nds-dev gp32-dev gba-dev nds-portlibs && \
    dkp-pacman -S --needed --noconfirm `dkp-pacman -Slq dkp-libs | grep '^3ds-'` && \
    dkp-pacman -Scc --noconfirm 
RUN apt update && sudo apt install automake build-essential wget unzip zip \
        libreadline-gplv2-dev libncursesw5-dev libssl-dev \
        libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev -y
RUN wget https://github.com/3DSGuy/Project_CTR/releases/download/makerom-v0.17/makerom-v0.17-ubuntu_x86_64.zip
RUN unzip makerom-v0.17-ubuntu_x86_64.zip && \
    mv ./makerom /usr/local/bin/makerom && \
    mv ./ext_key.txt /usr/local/bin/ext_key.txt && \
    mv ./ignore_3dstool.txt /usr/local/bin/ignore_3dstool.txt && \
    chmod +x /usr/local/bin/makerom
RUN git clone https://github.com/Steveice10/bannertool.git && \
    cd bannertool && \
    git submodule update --init && \
    make && \
    unzip ./output/bannertool.zip && \
    mv linux-x86_64/bannertool /usr/local/bin/bannertoolexec && \
    chmod +x /usr/local/bin/bannertoolexec && \
    cd ..
RUN wget https://github.com/dnasdw/3dstool/releases/download/v1.2.6/3dstool_linux_x86_64.tar.gz && \
    tar -zxvf 3dstool_linux_x86_64.tar.gz && \
    mv ./3dstool /usr/local/bin/3dstool && \
    chmod +x /usr/local/bin/3dstool
RUN wget https://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz && \
    tar xzf Python-3.8.5.tgz && \
    cd Python-3.8.5 && \
    ./configure --enable-optimizations && \
    make install
ENV DEVKITARM=${DEVKITPRO}/devkitARM
