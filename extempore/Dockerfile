FROM benswift/extempore-llvm

# based on an original dockerfile by Sébastien Rannou
MAINTAINER Ben Swift <ben@benswift.me>

# which GitHub branch to build Extempore from
ENV EXTEMPORE_GH_BRANCH llvm-3.7

# get deps (listed in alphabetical order)
RUN apt-get update --yes && apt-get install --yes \
    libasound2                                    \
    # libnanomsg0                                   \
    portaudio19-dev &&                            \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# download extempore
RUN curl -L -o source.zip http://github.com/digego/extempore/zipball/$EXTEMPORE_GH_BRANCH/ && \
    unzip source.zip && \
    mv $(ls | grep extempore) /extempore && \
    rm source.zip

# set LLVM environment var
ENV EXT_LLVM_DIR /llvm-build

# build extempore
RUN mkdir /extempore/cmake-build && cd /extempore/cmake-build && cmake -DIN_TREE=ON .. && make && cp extempore .. && cd /extempore

# build the stdlib (comment out if you don't want it)
RUN AOT_LIBS="core/std.xtm core/math.xtm" ./compile-stdlib.sh --noaudio

# remove build-time deps from image
# RUN apt-get remove --purge --yes binutils curl g++ cmake patch python unzip xzdec    

# expose extempore primary & utility process ports, plus nanomsg port
EXPOSE 7099 7098 7199

ENTRYPOINT ["/extempore/extempore"]

# Local Variables:
# compile-command: "docker build -t benswift/extempore ."
# End:
