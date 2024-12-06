# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:31477bf2b6087ae18d81409ff4115482359f8b1eb2eef765a4329acdd50c21d6\
    "https://github.com/dragonwell-project/dragonwell11/releases/download/\
dragonwell-standard-11.0.25.21_jdk-11.0.25-ga/Alibaba_Dragonwell_Standard_11.0.25.21.9_x64_linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM debian:bookworm

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]