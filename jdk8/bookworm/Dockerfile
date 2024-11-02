# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:e29da5d35c12418337b83e19d024171d2f755989e62d0bc483c9ec86d0483258\
    "https://github.com/dragonwell-project/dragonwell8/releases/download/\
dragonwell-standard-8.20.21_jdk8u422-ga/Alibaba_Dragonwell_Standard_8.20.21_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "sh" ]