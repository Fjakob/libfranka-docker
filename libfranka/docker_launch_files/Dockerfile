FROM ubuntu:22.04

### Make installation non interactive so that docker doesnt crash during build
ENV DEBIAN_FRONTEND noninteractive

### OS setup
RUN apt-get update &&\
    apt-get install -y\
    build-essential \
    cmake \
    doxygen \
    graphviz \
    lcov \
    libeigen3-dev \
    libpoco-dev \
    rename \
    valgrind \
    lsb-release \
    dpkg \
    git \
    && rm -rf /var/lib/apt/lists/*
    
### Python setup
RUN apt-get update &&\
    apt-get install python3.10 -y &&\
    apt install python3-pip -y &&\
    apt install -y python3-tk &&\
    apt install python3-gi-cairo -y &&\
    pip install --upgrade pip &&\
    pip install numpy==1.23.1 &&\
    pip install matplotlib==3.5.2
    
WORKDIR /docker_volume

### Install Libfranka
COPY ./install_libfranka.sh /install_libfranka.sh
RUN chmod +x /install_libfranka.sh
ENTRYPOINT [ "/install_libfranka.sh" ]

CMD ["/bin/bash"]

### Important: for every reboot: run xhost +local:docker
