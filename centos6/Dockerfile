FROM stackbrew/centos:6

RUN yum install -y cmake rpmdevtools git gnupg rpm-sign gcc make

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
