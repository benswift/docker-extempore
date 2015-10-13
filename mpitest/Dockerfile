FROM ubuntu:vivid

MAINTAINER Ben Swift <ben@benswift.me>

RUN apt-get update --yes && apt-get install --yes binutils gcc ssh libopenmpi-dev openmpi-bin && apt-get clean && rm -rf /var/lib/apt/lists/*

ADD mpi_mm.c /

RUN mpicc mpi_mm.c -o mpi_mm

# ENTRYPOINT ["mpiexec -np 2 ./mpi_mm"]

# Local Variables:
# compile-command: "docker build -t benswift/mpitest ."
# End:
