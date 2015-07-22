# Docker Extempore

Dockerfiles for [Extempore](http://github.com/digego/extempore)

Requires `debian:testing` from DockerHub

`extempore-llvm` creates a container containing a patched version of
LLVM which works with Extempore. It is build separately because it
takes a long time to build.

## Build

```
docker build -t extempore-llvm .
docker build -t extempore .
```

## Usage

The `--privileged` flag is necessary to run with audio/graphics

```
docker run --rm -t -i -p 7098:7098 -p 7099:7099 --volumes-from extempore-llvm --privileged extempore
```

## Caveats

This is still in the pre-alpha stage. Pull requests/improvements
welcome.

## Licence

MIT Licence, same as Extempore.
