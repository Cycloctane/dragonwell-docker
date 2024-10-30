# Dragonwell Docker

Simple dockerfiles for creating [Alibaba Dragonwell JDK](https://dragonwell-jdk.io/) (Standard Edition) docker images.

| Version |  Arch  | Base Image                   |
|---------|--------|------------------------------|
| 8       | x86_64 | debian bookworm              |
| 11      | x86_64 | debian bookworm, alpine 3.20 |
| 17      | x86_64 | debian bookworm, alpine 3.20 |
| 21      | x86_64 | debian bookworm, alpine 3.20 |

## usage

Build dragonwell 21 alpine image:

```bash
docker build -t dragonwell:jdk21-alpine ./jdk21/alpine
```

Build custom image with alternative openjdk binaries (e.g. Adoptium OpenJDK) and base image (e.g. ubuntu) using the "base" Dockerfile:

```bash
docker build -t $tag\
    --build-arg DOWNLOAD_URL=$jdk_bin_tar_url\
    --build-arg BASE_IMAGE=ubuntu:22.04\
    ./base
```