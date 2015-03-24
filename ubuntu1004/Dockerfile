FROM ubuntu:lucid

RUN apt-get update && \
    apt-get install -y build-essential gnupg cmake git-core wget

## CMake package is too old
RUN wget http://www.cmake.org/files/v3.1/cmake-3.1.3-Linux-x86_64.sh
RUN echo y | sh cmake-3.1.3-Linux-x86_64.sh
ENV PATH /cmake-3.1.3-Linux-x86_64/bin:$PATH

RUN mkdir -p /build/package
WORKDIR /build

RUN git clone https://github.com/luvit/luvi
WORKDIR luvi
RUN git checkout fixes/packaging
RUN git submodule update --init --recursive
RUN CPACK_DEB=1 make tiny
RUN make package
RUN cp /build/luvi/build/luvi*.deb /build/package
