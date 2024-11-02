# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:2ea1577803314807beeb0a4b95540850195d99a62c7fd07910f844320e1c2c6f\
    "https://github.com/dragonwell-project/dragonwell17/releases/download/\
dragonwell-standard-17.0.11.0.12%2B9_jdk-17.0.11-ga/Alibaba_Dragonwell_Standard_17.0.11.0.12.9_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]