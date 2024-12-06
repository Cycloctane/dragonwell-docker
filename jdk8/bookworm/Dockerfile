# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:93f88d5f49ca5c3ea99ee865c9589138f9fb435901ebe1fc74434f0ceba1f1ab\
    "https://github.com/dragonwell-project/dragonwell8/releases/download/\
dragonwell-standard-8.23.22_jdk8u432-ga/Alibaba_Dragonwell_Standard_8.23.22_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "sh" ]