FROM debian:bullseye

RUN DEBIAN_FRONTEND=noninteractive apt update --assume-yes
RUN DEBIAN_FRONTEND=noninteractive apt install --no-install-recommends --assume-yes build-essential git ca-certificates make xxd file wget gettext-base cmake dpkg-dev lsb-release
RUN DEBIAN_FRONTEND=noninteractive apt install --no-install-recommends --assume-yes liblo-dev nodejs libcurl4-openssl-dev build-essential libasound2-dev libeigen3-dev libfftw3-dev libfftw3-double3 libfftw3-single3 libgsl-dev libjack-jackd2-dev libltc-dev libmatio-dev libsndfile1-dev libsamplerate0-dev  libboost-all-dev nlohmann-json3-dev libsoundio-dev libxerces-c-dev libgtkmm-3.0-dev libcairomm-1.0-dev libcunit1-dev

RUN mkdir /build
RUN git config --global pull.rebase false
RUN cd /build && git clone https://github.com/gisogrimm/ov-client
RUN cd /build/ov-client && git submodule update --init --recursive

COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
