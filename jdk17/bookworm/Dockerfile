# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:281d1c204fc0bfa6d7669921a8261cc7efc7513818d3312e9306786814457966\
    "https://github.com/dragonwell-project/dragonwell17/releases/download/\
dragonwell-standard-17.0.13.0.14%2B9_jdk-17.0.13-ga/Alibaba_Dragonwell_Standard_17.0.13.0.14.9_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]