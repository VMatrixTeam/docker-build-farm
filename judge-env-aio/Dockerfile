FROM debian:bullseye
ENV LC_ALL=C
RUN useradd -U -m -s /bin/sh judge
RUN apt update
RUN apt install -y software-properties-common cabal-install ghc curl make libcurl4-openssl-dev golang golint nodejs lua5.3 rustc cargo xz-utils default-jdk-headless pypy pypy3 pylint python3 python3-pip pylint3 clang libclang-dev ruby scala libboost-all-dev cmake libgtest-dev gnat gcc g++ gfortran gcc-multilib g++-multilib libsqlite3-dev libpq-dev fp-compiler valgrind locales
RUN apt-get autoremove --purge && apt-get clean
RUN rm -rf /var/lib/apt/lists/*
RUN rm -rf /var/log/*
RUN rm -rf /var/cache/*
RUN cd /usr/src/gtest && cmake . && make && cp ./lib/*.a /usr/lib
RUN pip3 install xmltodict
RUN curl -fsSL https://github.com/oclint/oclint/releases/download/v21.05/oclint-21.05-llvm-12.0.0-x86_64-linux-ubuntu-20.04.tar.gz | tar -C /tmp -xz && rm /tmp/oclint-21.05/LICENSE && cp -r /tmp/oclint-21.05/* /usr && rm -rf /tmp/oclint-21.05
