FROM masm/archlinux

RUN pacman -Syu --noconfirm --needed cmake git gnupg make gcc yasm fakeroot

RUN mkdir -p /build/package
WORKDIR /build

RUN git clone https://github.com/luvit/luvi
WORKDIR luvi
#RUN git checkout fixes/packaging
RUN git submodule update --init --recursive
RUN make tiny && make -j4
ADD PKGBUILD /build/luvi/PKGBUILD
RUN chown -R arch . && su arch makepkg

RUN cp /build/luvi/luvi*.tar.xz /build/package
