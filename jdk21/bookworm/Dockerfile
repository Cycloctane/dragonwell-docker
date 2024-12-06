# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:7b51d0f2ec8c2096741dda160c61b047a6fd47c9a554fdfdd961f9745523f0ee\
    "https://github.com/dragonwell-project/dragonwell21/releases/download/\
dragonwell-standard-21.0.5.0.5%2B9_jdk-21.0.5-ga/Alibaba_Dragonwell_Standard_21.0.5.0.5.9_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]