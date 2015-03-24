FROM debian:7.8

RUN apt-get update && \
    apt-get install -y build-essential gnupg cmake git

RUN mkdir -p /build/package
WORKDIR /build

RUN git clone https://github.com/luvit/luvi
WORKDIR luvi
RUN git checkout fixes/packaging
RUN git submodule update --init --recursive
RUN CPACK_DEB=1 make tiny
RUN make package
RUN cp /build/luvi/build/luvi*.deb /build/package
