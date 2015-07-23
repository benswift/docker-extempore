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
docker run --rm -t -i --privileged extempore
```

## DockerHub

I'll try and keep it up-to-date on DockerHub as `benswift/extempore`,
so then you can just `docker pull benswift/extempore`.

## Caveats

This is still in the pre-alpha stage. Pull requests/improvements
welcome.

## Licence

MIT Licence, same as Extempore.
