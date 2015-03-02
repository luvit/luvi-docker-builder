FROM stackbrew/centos:5

RUN rpm -Uvh http://dl.fedoraproject.org/pub/epel/5/x86_64/epel-release-5-4.noarch.rpm
RUN yum install -y rpmdevtools git gnupg rpm-sign gcc make

## CMake package is too old
RUN wget http://www.cmake.org/files/v3.1/cmake-3.1.3-Linux-x86_64.sh
RUN echo y | sh cmake-3.1.3-Linux-x86_64.sh
ENV PATH /cmake-3.1.3-Linux-x86_64/bin:$PATH

RUN rpmdev-setuptree
RUN mkdir -p /build/package
WORKDIR /build

RUN git clone https://github.com/luvit/luvi
WORKDIR luvi
RUN git checkout fixes/packaging
RUN git submodule update --init --recursive
RUN CPACK_RPM=1 make tiny
RUN make package
RUN cp /build/luvi/build/luvi-*.rpm /build/package
