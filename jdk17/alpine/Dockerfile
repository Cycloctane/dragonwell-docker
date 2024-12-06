# syntax=docker/dockerfile:1
FROM alpine:3.20

WORKDIR /tmp

ADD --checksum=sha256:c932f3dab72fd2c80f6d732a1ea829ee75469595560893b90ca883d457b9a97f\
    "https://github.com/dragonwell-project/dragonwell17/releases/download/\
dragonwell-standard-17.0.13.0.14%2B9_jdk-17.0.13-ga/Alibaba_Dragonwell_Standard_17.0.13.0.14.9_x64_alpine-linux.tar.gz"\
    ./openjdk.tar.gz

RUN mkdir openjdk;\
    tar --extract --file openjdk.tar.gz --directory openjdk --strip-components 1;\
    rm openjdk/lib/src.zip

FROM alpine:3.20

COPY --from=0 /tmp/openjdk /usr/local/openjdk
ENV LANG="C.UTF-8" JAVA_HOME="/usr/local/openjdk" PATH="/usr/local/openjdk/bin:$PATH"
CMD [ "jshell" ]