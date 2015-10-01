# Docker Extempore

Dockerfiles for [Extempore](http://github.com/digego/extempore)

Uses `ubuntu:vivid` from DockerHub as a base container.

`extempore-llvm` is a container containing a patched version of LLVM
which works with Extempore. It is built separately because it takes a
long time to build.

## Build

```
docker build -t extempore-llvm .
docker build -t extempore .
```

## Usage

```
docker run --rm -P benswift/extempore --noaudio
```
The `-P` flag binds all the exposed ports to the host. If you're
running in `docker-machine`, you'll first need to run
```
docker-machine ip machine-name
```
to get the IP address of your machine, then look at `docker ps` to see
where the ports have been mapped. Use these values as the host and
port respectively when you connect your editor to the Extempore
process running inside the container.

The `--noaudio` flag means that Extempore doesn't try to find an audio
device---which requires special privileges. You can pass the
`--privileged` flag to `docker run` if you want to use audio/graphics.

## DockerHub

I'll try and keep it up-to-date on DockerHub as `benswift/extempore`,
so then you can just `docker pull benswift/extempore`.

## Caveats

This is still in the pre-alpha stage. Pull requests/improvements
welcome.

## Licence

MIT Licence, same as Extempore.
