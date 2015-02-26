FROM stackbrew/ubuntu:saucy

RUN apt-get update && \
    apt-get install -y build-essential gnupg ruby ruby-dev cmake git
RUN gem install fpm

RUN mkdir -p /build/package
WORKDIR /build

RUN git clone https://github.com/luvit/luvi
WORKDIR luvi
RUN git checkout feat/packaging
RUN git submodule update --init --recursive
RUN make tiny
RUN make package-deb
RUN cp /build/luvi/luvi*.deb /build/package
