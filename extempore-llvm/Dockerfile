FROM ubuntu:vivid

# based on an original dockerfile by Sébastien Rannou
MAINTAINER Ben Swift <ben@benswift.me>

# need to use a PPA for an up-to-date CMake version (3.1 required)
RUN apt-get install --yes software-properties-common && add-apt-repository ppa:george-edison55/cmake-3.x && apt-get update --yes

# get other deps (listed in alphabetical order)
RUN apt-get install --yes binutils curl g++ cmake patch python unzip xzdec && apt-get clean && rm -rf /var/lib/apt/lists/*

# download, patch, and build LLVM
RUN curl -O http://llvm.org/releases/3.7.0/llvm-3.7.0.src.tar.xz && \
    xzdec llvm-3.7.0.src.tar.xz | tar -xf - && \
    cd /llvm-3.7.0.src && \
    curl -s https://raw.githubusercontent.com/digego/extempore/llvm-3.7/extras/extempore-llvm-3.7.0.patch | patch -p0 -i - && \
    cd /llvm-3.7.0.src && mkdir cmake-build && cd cmake-build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_TERMINFO=OFF  -DLLVM_ENABLE_ZLIB=OFF -DCMAKE_INSTALL_PREFIX=/llvm-build .. && make install && \
    cd / && \
    rm -rf /llvm-3.7.0.src llvm-3.7.0.src.tar.xz

VOLUME /llvm-build

# Local Variables:
# compile-command: "docker build -t benswift/extempore-llvm ."
# End:

